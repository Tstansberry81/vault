---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2025-08-30
author: Traveler Stansberry
source_type: chat
tags: [chat, startup, automation, n8n, homework-hatch]
status: active
---

# n8n Command Router for Homework Hatch — Telegram, Calendar, Instagram

A build/devops session in which Traveler asks ChatGPT (GPT-5) to construct a "complex workflow station" in **[[n8n (automation platform)|n8n]]** for his [[Homework Hatch (startup)]] (referred to here as "HW Buddy"). The goal: an automation hub that listens to natural-language commands over **Telegram**, uses an AI agent to parse intent, then dispatches to coded functions — automated Google Calendar event creation/lookup and automated Instagram posting, with room to add more. This is Traveler running the operational and marketing side of his startup as a one-person ops team, leaning on AI to wire up plumbing he hasn't built before.

## What was produced
The assistant pasted a full importable n8n workflow JSON — "HW Buddy — Command Router (Telegram → AI → Calendar / Instagram)" — with this architecture:
- **Telegram Trigger** → **Extract Command** (function node pulling `chat_id`, `from`, `text`).
- **AI: Parse Intent** — an HTTP call to OpenAI (`gpt-4o-mini`, `temperature 0`, JSON-object response) with a system prompt that forces the model to emit strict JSON matching a schema: `intent` (one of `CREATE_EVENT`, `GET_EVENTS`, `POST_INSTAGRAM`, `HELP`) plus `args` (title, ISO start/end, timezone defaulting to `America/New_York`, attendees, image_url, caption, windowDays). This is a clean example of using an LLM as a constrained intent classifier / router rather than a chat surface.
- **Route by Intent** Switch node fans out to: Google Calendar create, Google Calendar getAll (upcoming events, formatted for Telegram), or a two-step Instagram Graph API post (`/media` create container → `/media_publish`).
- Merge nodes re-attach the Telegram `chat_id` so confirmations route back to the user; plus a global **Error Trigger** that DMs the failure.

Setup instructions covered BotFather token creation, an `OPENAI_API_KEY` env var, Google Calendar OAuth2 credentials, and Instagram Business/Creator linkage via `IG_USER_ID` + long-lived `IG_ACCESS_TOKEN`. The assistant offered optional extensions: voice commands (Telegram voice → OpenAI Whisper transcription → same parser) and new switch cases (`SEND_DISCORD`, `CREATE_TODO`, `BUILD_STUDY_GUIDE`, Notion/Gmail/Canvas pulls).

## How it shows Traveler working
Most of the back-and-forth is Traveler struggling to find the **Import from File / Import from Clipboard** option in the n8n UI — he sends three screenshots of his "HW Buddy Swarm" project workspace, and the assistant walks him through where the menu hides. He then asks ChatGPT to emit the workflow as a downloadable `.json` file. This is characteristic [[Homework Hatch (startup)]] hands-on building: he treats ChatGPT as a pair-programmer/ops engineer to stand up infrastructure (calendar + social automation) outside his core coding comfort zone. It connects to his broader pattern of using agentic AI and integrations for the startup (see [[Agentic AI, MCP, and LMS Credential Ingestion for Homework Hatch (chat)]], [[Canvas LMS Adoption Research for Homework Hatch (chat)]]).

## Style note
Mid-conversation Traveler tells the assistant "take away your 18 year old speech i dont like it" and then "save that to memory, but keep the sarcasm" — a small window into how he curates his AI tooling's tone: no try-hard youth slang, dry sarcasm acceptable. Reflects his self-image as an [[Individual vs. Society|individualist]] who wants instruments, not personality.

A closing exchange clarifies a limit: he asks whether ChatGPT can "watch" an Instagram video URL; the model says no but offers to scrape public caption/metadata and build a repost workflow.
