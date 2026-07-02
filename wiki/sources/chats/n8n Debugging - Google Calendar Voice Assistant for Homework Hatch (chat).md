---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2025-08-31
author: Traveler Stansberry
source_type: chat
tags: [chat, startup, coding, automation/n8n]
status: active
---

# n8n Debugging - Google Calendar Voice Assistant for Homework Hatch

A long, screenshot-driven troubleshooting session in which Traveler debugs the [[Homework Hatch (startup)]] Telegram assistant — an [[n8n (automation platform)|n8n]] workflow that turns a Telegram voice note into a Google Calendar event. This is a direct continuation of the same product line documented in [[n8n Telegram Voice Assistant for HW Buddy - Calendar Automation (chat)]] and [[n8n Command Router for Homework Hatch - Telegram, Calendar, Instagram (chat)]]; the workflow here is named "ai assistant" and runs against the `sphwbuddy@gmail.com` calendar. It shows Traveler operating as a no-code/AI-agent builder, iterating tightly against live error screenshots rather than writing code from scratch.

## The workflow architecture
The pasted JSON exposes the full pipeline: a **Telegram Trigger** ("Listen for incoming events") feeds a **Voice or Text** Set node and an IF that branches voice messages to a Telegram file fetch plus OpenAI **Speech to Text** (Whisper transcribe). A **Router Bot** [[LangChain]] agent (gpt-4o-mini, JSON mode) classifies each message as `ROUTE_EMAIL` or `ROUTE_ANNA`. The email branch runs an agent named **Wade** (EmailBot) + a "Parse Wade Output" Code node + Gmail send; the calendar branch runs **Anna**, an agent wired to the Google Calendar Tool node via `ai_tool`, with Window Buffer Memory keyed on the Telegram user id. A "Detect Anna Result" Code node parses Anna's output, and **If2** routes to a success vs failure Telegram message. This is a genuinely non-trivial multi-agent automation built by a high schooler.

## Bugs found and fixed (the substance)
The session is a clinic in n8n agent-tool plumbing failure modes:
- **Key mismatch:** the Calendar tool read `$fromAI("Start"/"end")` while Anna's prompt produced `startISO`/`endISO` → undefined times. Fixed by aligning keys.
- **`$fromAI()` constraints:** AI Tool fields reject normal expressions (`$moment()`, `||`, escaped quotes); `[invalid syntax]` and `[undefined]` errors came from mixing fallbacks/escapes in, and from executing the tool node standalone (`$fromAI` only resolves when the agent calls the tool).
- **Stray-newline equality bug:** If2 compared against `"SUCCESS\n"`, so successes fell to the ❌ branch. The robust fix abandoned status-string matching entirely and keyed success off the presence of a Google Calendar `htmlLink` (regex / is-empty operator).
- **Code node crashing** ("Unknown error") on empty input → rewritten with `$input.all()`, try/catch, and null-coalescing so it never throws.
- **Date hallucination:** Anna parsed "October 25th" as **2023** because the LLM had no "now" anchor. Fix: inject today's date and timezone via a **Set node** (`$moment().format('YYYY-MM-DD')` / `Z`) into Anna's prompt, plus a "bias dates to the future / roll forward past dates" system-message rule.

## What it reveals
Traveler is building real, deployed agentic tooling for [[Homework Hatch (startup)]] and debugging it empirically — running steps, screenshotting errors, pasting them back, and iterating. He shows working knowledge (or fast acquisition) of OAuth scopes, RFC3339 datetimes, LLM JSON-mode unreliability, and the gap between an LLM-tool placeholder and actual runtime values. His questions ("how do i add a set node", "im in edit fields what now") confirm he is self-teaching the n8n UI in real time. This connects to his broader [[Coding Club]] / builder identity and the agentic-AI direction documented in [[Agentic AI, MCP, and LMS Credential Ingestion for Homework Hatch (chat)]].

![[5ca07d1e-a349-4e66-bde9-908d954ab1de.png]]
