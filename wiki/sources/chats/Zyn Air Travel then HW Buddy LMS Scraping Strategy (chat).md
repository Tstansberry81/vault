---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2025-09-09
author: Traveler Stansberry
source_type: chat
tags: [chat, startup, homework-hatch, lms-integration, personal]
status: active
---

# Zyn Air Travel then HW Buddy LMS Scraping Strategy

A two-part ChatGPT exchange (dated 2025-09-09, GPT-5) that swings from a personal travel logistics question into a genuinely substantive product-engineering discussion for [[Homework Hatch (startup)|Homework Hatch]] (HW Buddy).

## Part 1 — personal logistics (low value)
Traveler opens by asking how to get **Zyn nicotine pouches** through airport security: whether TSA flags them, where to pack them, whether an opened tin is fine. The answers: TSA doesn't care, keep them in the original tin in a carry-on, don't check them or hide them, and watch customs in strict countries (Australia, Singapore, UAE). A small personal-life datapoint — consistent with his [[Family and Personal Life|off-the-record teenage habits]] — but no lasting knowledge.

## Part 2 — the real content: LMS ingestion for HW Buddy
After a couple of one-off lookups (Harvard's ~$4.9M/yr application-fee revenue; whether High Point University uses Canvas), Traveler clarifies he's researching **for Homework Hatch, not himself** — building the assignment-ingestion pipeline. HPU runs **Blackboard, not Canvas**, which reframes the integration: a different (and messier) connector than the Canvas API.

The key moment: Traveler says he'd "really like to get a scraper working" because **API access to other LMSs is messy and requires approval from higher-ups** (the same institutional-gatekeeping problem flagged in [[Agentic AI, MCP, and LMS Credential Ingestion for Homework Hatch (chat)]] and [[Canvas LMS Adoption Research for Homework Hatch (chat)]]). The model pushes back toward a **compliant, consent-based architecture** rather than central scraping:

1. **iCal calendar feeds (zero-scrape)** — every major LMS (Canvas, Blackboard, Brightspace, Moodle) exposes a per-student iCal due-date feed. Ingest the URL, normalize, done. No API keys, no approvals.
2. **Email parsing (zero-scrape)** — read-only Gmail/Outlook OAuth, parse LMS notification emails for course/title/due-date, dedupe by message-ID.
3. **User-side browser automation (compliant scraping)** — Playwright/Puppeteer logging in *as the user* in their own session, storing an encrypted per-user profile, pausing for MFA on first run, throttling, never hitting hidden endpoints.
4. **LTI 1.3** — clean and approved, but needs school buy-in and a long lead time.

The recommended HW Buddy build is a **multi-ingest "LMS Connector"**: iCal as the stable primary for due dates, email as near-real-time secondary, and an on-demand Playwright "Deep Sync" for rich fields (descriptions, rubrics, attachments) only when the user clicks. A Python Playwright skeleton for a Blackboard "upcoming" scraper is included, with a unified JSON output schema so the app is LMS-agnostic, plus ops rules (run user-scoped, never bypass MFA/CAPTCHA, throttle 1–2 pages/min, backoff on 429/5xx, respect ToS).

## What it reveals
This is Traveler the founder hitting the central technical and legal wall of HW Buddy: **how to get assignment data out of locked-down school systems without institutional permission**. His instinct (just scrape it) gets redirected toward a defensible "consent on the student's own account" model — the same compliance tension that runs through his [[Gemini vs OpenAI API ToS and Cheating Liability for Homework Hatch (chat)]] and [[Custom LLM Build and SPHW Buddy Terms of Service (chat)]] research. The Canvas-vs-Blackboard distinction also reinforces why he keeps wanting a "schools cheat sheet" mapping which LMS each target school uses — a real go-to-market data-collection task for the startup.
