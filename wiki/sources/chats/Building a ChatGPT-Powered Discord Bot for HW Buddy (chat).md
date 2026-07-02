---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2025-08-24
author: Traveler Stansberry
source_type: chat
tags: [chat, coding, startup, discord, openai-api]
status: active
---

# Building a ChatGPT-Powered Discord Bot for HW Buddy

A hands-on coding/debugging session (24 Aug 2025) in which [[Traveler Stansberry]] stood up a working **Discord bot wired to the OpenAI API** as a prototype surface for his [[Homework Hatch (startup)]] product — the bot literally logs in as **"HW Buddy Assistant"** in his **"HW Buddy Development"** server. This is one of several chats showing him scaffolding the startup's AI-tutor functionality on cheap, available infrastructure before committing to anything heavier (cf. [[Custom LLM Build and SPHW Buddy Terms of Service (chat)|Custom LLM Build and SPHW Buddy Terms of Service]], [[Training a Custom AI on AWS with Bloomberg Data (chat)|Training a Custom AI on AWS with Bloomberg Data]]).

## What he was doing
He asked first whether ChatGPT could be downloaded to desktop and integrated with Discord, then accepted the offer of a ready-to-run **`discord.py` + OpenAI** Python script. The arc of the chat is a beginner-to-working debugging walkthrough:
- Learned that **ChatGPT Plus and OpenAI API access are billed separately** — the Plus subscription does not grant API access; he had to go to `platform.openai.com`, add billing, and generate a secret key (metered per-token).
- Set `OPENAI_API_KEY` and `DISCORD_TOKEN` as environment variables rather than hardcoding secrets.
- Hit the standard Discord gotchas: which "key" to use (the **Bot Token**, not Application ID or Public Key), an "Invalid scopes provided for user installation" OAuth error (fixed by checking only the `bot` scope), and the **Message Content Intent** that must be enabled for the bot to read messages.
- Debugged a "bot is in server but not responding" state down to intents/permissions, with a `!ping` → `pong` minimal test isolating Discord-side vs. OpenAI-side failures.
- Asked how to **change the model**; learned the API doesn't self-report its version and that "I'm GPT-3.5" replies came from a hardcoded system message, not the actual model. Settled on `gpt-4o-mini` for speed/cost with a `gpt-4.1` option for heavier reasoning, plus a tutor system prompt: *"You are HW Buddy Assistant, a helpful AI tutor."*

He confirmed "**got it to work thanks**" at the end. Notably he mentioned he didn't have `pip` on his desktop because it's tied "to a side project," signaling he keeps his startup work in a separate Python environment.

## What it reveals
- **Practical, ship-first engineering.** He's comfortable copy-pasting, running, and debugging real code through env-var secrets, OAuth scopes, and gateway intents — consistent with the self-taught, project-driven coder seen across his [[Coding Club]] teaching and [[Homework Hatch (startup)]] build logs.
- **Product direction.** The assistant's closing pitch — hook the bot into **Canvas or SPHW Buddy project data** for class-specific help, add `/studyguide` slash commands, give it conversation memory — maps directly onto Homework Hatch's actual feature set (see [[Canvas LMS Adoption Research for Homework Hatch (chat)|Canvas LMS Adoption Research for Homework Hatch]], [[Agentic AI, MCP, and LMS Credential Ingestion for Homework Hatch (chat)|Agentic AI, MCP, and LMS Credential Ingestion for Homework Hatch]]).
- **Cost-consciousness** about per-token API billing, echoing his broader build-vs-buy deliberations for the startup.

> [!note] Provider note
> This bot is built on OpenAI's API (`gpt-4o-mini` / `gpt-4.1`), not Anthropic's — relevant when comparing against his other API-platform research for the startup.
