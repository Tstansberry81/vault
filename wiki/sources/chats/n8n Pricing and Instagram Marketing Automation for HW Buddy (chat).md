---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2025-08-31
author: Traveler Stansberry
source_type: chat
tags: [chat, startup, automation, n8n]
status: active
---

# n8n Pricing and Instagram Marketing Automation for HW Buddy

A planning conversation (GPT-5, Aug 2025) in which Traveler evaluates the workflow-automation tool **n8n** as infrastructure for [[Homework Hatch (startup)]] (here called "HW Buddy"). He shares a screenshot of n8n's pricing tiers and asks ChatGPT to assess them "in regards to the hw buddy devs (team of 5 people)" — a rare concrete signal that the startup had a multi-person dev team, not just himself.

## What he was doing
- **Pricing analysis.** ChatGPT compares the **Starter ($24/mo, 2,500 executions, 1 shared project, 1-day history)** and **Pro ($60/mo, 10,000 executions, 3 projects, 7-day logs, admin roles, global variables)** tiers. Verdict: Starter is too cramped for 5 devs; **Pro is the "minimum viable choice."** Enterprise only matters if the tool goes student-facing.
- **Understanding execution billing.** Traveler probes exactly what counts as a "workflow execution" — learning it's per-*run* (one trigger → finish), not per-node or per-step, but that chaining workflow A → workflow B counts as two. He correctly flags the cost trap: a Canvas-polling cron every 5 min = ~8,640 executions/month, blowing past Starter alone.
- **Instagram marketing automation.** He asks whether n8n can automate Instagram marketing. ChatGPT lays out what Meta's **Instagram Graph API** allows (scheduled posts, carousels, Reels via `/media` → `/media_publish`, AI-generated captions, comment replies, analytics) versus what's banned (Stories, personal accounts, auto-follow/mass-DM/scraping). A full n8n node blueprint is given: Cron → content-calendar sheet → LLM caption refinement → media create/publish → insights logging → Telegram alerts.

## What it reveals
- **Scope clarification.** Crucially, Traveler corrects the assistant's assumption: the bot is **"not meant for students, it's meant for in-house scheduling and marketing"** — a Telegram-triggered agent (voice/text → LLM → Google Calendar/Gmail/Instagram) for his own 5-person team, not a customer-facing product. This reframes the [[Homework Hatch (startup)]] tooling: he was building internal ops/marketing automation, distinct from the student homework product.
- **Builder fluency.** He reasons about cost ceilings, dev/staging/prod project separation, credential storage vs. hardcoding keys, and API rate limits — consistent with his hands-on, technical approach seen across his startup chats and [[Coding Club]] teaching. Connects to his broader interest in agentic AI orchestration (Telegram bots, LLM tool-calling, Canvas integration).

The takeaway: for light in-house use (~3,100 executions/month across 5 devs plus a few scheduled posts), **n8n Pro** is the sweet spot.
