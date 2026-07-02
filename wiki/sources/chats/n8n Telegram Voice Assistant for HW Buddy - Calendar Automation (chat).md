---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2025-08-30
author: Traveler Stansberry
source_type: chat
tags: [chat, startup, coding, automation, n8n]
status: active
---

# n8n Telegram Voice Assistant for HW Buddy - Calendar Automation (chat)

A long, hands-on build-and-debug session in which Traveler tries to stand up a **Telegram voice assistant** for his startup [[Homework Hatch (startup)]] (here under its "HW Buddy" branding) using **n8n**, a no-code/low-code workflow automation platform. The chat opens with a one-line summary of HW Buddy — an AI student companion that integrates with [[Canvas LMS]]-style platforms to summarize course materials, generate flashcards/study guides/Kahoots, run a class-specific chatbot, and gamify engagement with "Buddy Coins" and leaderboards — then pivots almost entirely into practical automation engineering.

## What he was building
The goal: a Telegram bot that takes a **voice note** ("schedule calc test tomorrow at 3pm"), transcribes it via OpenAI **Whisper**, runs the text through **GPT** to extract structured event JSON `{title, date, time, description}`, and creates a **Google Calendar** event — then replies in chat to confirm. This is a concrete vertical slice of the broader HW Buddy vision (assignment/grade tracking, study automation), prototyped as a Telegram + n8n pipeline rather than inside the main app.

## The debugging arc
The conversation is mostly Traveler fighting infrastructure, with ChatGPT walking him through each layer:
- **n8n setup** — Node.js v18+, npm, `npm install -g n8n`, running with `n8n start --dotenv .env`; he confirms he's actually on **n8n Cloud** (`hw-buddy.app.n8n.cloud`) on a trial, not local/Docker.
- **Webhook wiring** — repeatedly setting Telegram's webhook to the n8n Production URL via `setWebhook` (he prefers the no-code browser-URL method over `curl`), and reading `getWebhookInfo` to verify.
- **JSON import hell** — hand-built `workflow.json` files kept failing with "Cannot read properties of undefined" and "Could not find property option" because n8n Cloud enforces a locked node schema; ChatGPT's fix was to abandon raw JSON imports and use the **prebuilt "Voice assistant agent" template** (Telegram Trigger → IF audio → Get file → Whisper transcribe → LangChain Agent with Google Calendar tool + memory → Reply).
- **The actual bug** — the template's `Telegram Message Trigger` had `userIds: "YOUR_USER_ID"` left as a placeholder, silently filtering out all messages; the reply node also referenced a nonexistent `output` key. Fixes: set his real Telegram user ID (`6594181389`), point the calendar to `primary` instead of the template's `robert@n8n.io` demo account, and harden the reply expression.
- Ends with voice notes still not kicking off the workflow and him asking ChatGPT to find GitHub repos with a ready-made version of the workflow he wants.

## What it reveals
This is Traveler in **scrappy founder/builder mode** — long on persistence ("fuck the repo for now, the bot is still not working"; "edit the code one last time"), short on patience for ceremony, willing to paste full workflow exports and grind through OAuth/webhook/schema errors to get a feature shipped. It shows him stitching together OpenAI, Telegram, and Google APIs through n8n rather than writing a backend from scratch, consistent with his other [[Homework Hatch (startup)]] work (see [[Agentic AI, MCP, and LMS Credential Ingestion for Homework Hatch (chat)]], [[Canvas LMS Adoption Research for Homework Hatch (chat)]], [[Custom LLM Build and SPHW Buddy Terms of Service (chat)]]). It also reflects his self-taught coding practice tied to running the [[Coding Club]] — comfortable orchestrating AI tools and APIs even while leaning on the model for the implementation details. The reliance on third-party APIs here sits against HW Buddy's stated long-term goal of building in-house models to reduce API dependence.
