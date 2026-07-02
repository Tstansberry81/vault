---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2025-08-31
author: Traveler Stansberry
source_type: chat
tags: [chat, startup, n8n, ai-agents, automation]
status: active
---

# n8n Router-Mail-Calendar Agent Debugging for HW Buddy

A long, in-the-weeds debugging session (GPT-5, 31 Aug 2025) in which Traveler builds and repeatedly un-breaks a multi-agent n8n workflow for [[Homework Hatch (startup)|HW Buddy]]. The flow is an "AI secretary": a Telegram bot that accepts **voice or text**, transcribes voice via speech-to-text, then passes the message to a **router agent** that dispatches to one of two specialist sub-agents. He drives the whole thing by screenshotting his n8n canvas and asking the model to diagnose red error states. This is a direct continuation of his [[n8n Telegram Voice Assistant for HW Buddy - Calendar Automation (chat)|earlier Telegram voice-assistant]] and [[n8n Command Router for Homework Hatch - Telegram, Calendar, Instagram (chat)|command-router]] experiments.

## The architecture
- **Router Bot** (renamed from "Josh") — a dispatcher agent with a strict system prompt that outputs JSON `{ "route": "ROUTE_EMAIL" | "ROUTE_ANNA", "original_message": "..." }`, fed by a Structured Output Parser.
- **Wade** — the "mail guy": an EmailBot agent wired to Gmail send/get, instructed to *act, not draft* (send immediately, never produce templates), confirming with a checkmark message.
- **Anna** — the "calendar girl": a Tools Agent wired to Google Calendar create/list, producing events from natural language.
- Shared plumbing: Telegram trigger ("Listen for incoming events"), OpenAI Chat Model nodes, Window Buffer Memory keyed by Telegram user id, and an If node routing on `route`.

## The bugs he hit (a tour of n8n footguns)
- **Ghost node references**: his If condition pointed at `$('Router Bot')` while the node was actually named "Josh" — n8n's `$('...')` lookups are name-sensitive and silently return `undefined`. Learned that node names and expression references must match exactly.
- **AI Agent needs a separate Chat Model node** wired into its input — setting `model: gpt-4o-mini` inside the agent config alone throws "no chat model."
- **Voice/Text branch checking the wrong field** (`$json.message.text` after a Set node stripped it).
- **A dead `If2` node** adding latency while routing both branches to the same place — repeatedly told to delete it.
- **Boolean-vs-string type errors**: an If expression returning the string `"false "` instead of a real boolean, which he found maddening ("can we make it not boolean? it keeps fucking up"). Resolved by switching to a string-route comparison (`ROUTE_EMAIL`).
- **The webhook silence problem**: bot not responding despite active workflow — diagnosed as Telegram allowing only one webhook per bot token, requiring a public HTTPS URL, and needing a deactivate/activate cycle (or BotFather `/deletewebhook`) to re-register. Used a "canary" echo node to prove the trigger fires.
- **Calendar create failures**: events failing on bad datetimes (Google needs RFC3339 with timezone offset, not "tomorrow 2pm"), an "Unable to create duplicate events at the same time" error, and the agent calling the tool twice — fixed by instructing Anna to emit RFC3339 and call the tool at most once, plus "Continue On Fail" + debug Telegram nodes to surface the exact Google error.
- **Flaky Structured Output Parser**: "every time we try the parser it doesn't work" — abandoned the parser in favor of a tiny `Detect Anna Result` Function node that heuristically reads success (a Google Calendar link or "successfully created" phrase) out of Anna's prose.

## What it reveals
This is Traveler the **builder** rather than the student: hands-on, iterative, debugging by trial-and-screenshot, willing to swap whole approaches (parser → function, boolean → string route) when something keeps failing. It shows real fluency with agentic-LLM plumbing — routers, tool agents, structured output, session memory — and the practical instinct to harden against edge cases (allowlist the Telegram user id, error fallbacks, "act don't draft"). The voice-driven Telegram secretary is recognizably a prototype layer of [[Homework Hatch (startup)|HW Buddy]]'s automation ambitions, connecting to his broader [[Intellectual Interests|interest]] in [[UVA and the Quant Question|building real software]] alongside his finance track. The session is less polished theory and more the messy reality of getting agents to *do the action* reliably.
