---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2025-09-10
author: Traveler Stansberry
source_type: chat
tags: [chat, homework-hatch, coding, ai, canvas]
status: active
---

# Canvas API Access Audit and Custom ChatGPT Mode System

A wide-ranging Sept 2025 session that begins with a deceptively small question — "does UNC use Canvas?" — and unfolds into a real engineering and personalization problem for [[Homework Hatch (startup)]]. It is one of the clearest single-chat windows into both how Traveler builds his startup and how he configures his AI tools to work the way he wants.

## The Canvas policy-mapping problem

The actual driver: Homework Hatch ingests students' LMS data, but **Canvas API access is set per-institution**, not globally. ChatGPT lays out the three buckets every school falls into — self-service **Personal Access Tokens (PATs)**, **request-only** (IT ticket / ServiceNow), or **Developer-Key / OAuth-only** (admin-approved apps). Traveler wants a *systematic* way to detect which bucket each top university is in, so HH can pick the right onboarding flow per campus.

The answer is a Python scraper (`canvas_access_audit.py`) that, per school: builds `site:<domain> "Canvas" "access token"`-style DuckDuckGo queries, fetches the school's own KB pages, runs three regex detectors over the text, scores/ranks the evidence, and writes a CSV labeling each school **PAT / REQUEST / DEVKEY / UNKNOWN**. He then asks for a refactor ("reduce clutter") and a full beginner-level walkthrough, since he has *no prior Python knowledge* — the explanation maps every function back to HH's onboarding logic (PAT → "paste your token" UI; REQUEST → "open a ticket" link; DEVKEY → OAuth app-approval flow). This is the same campus-credential-ingestion problem explored in [[Agentic AI, MCP, and LMS Credential Ingestion for Homework Hatch (chat)|Agentic AI, MCP, and LMS Credential Ingestion for Homework Hatch]] and [[Canvas LMS Adoption Research for Homework Hatch (chat)|Canvas LMS Adoption Research for Homework Hatch]].

## The full HH codebase walkthrough

He uploads "HOMEWORK HATCH 9-3.zip" and has ChatGPT reverse-engineer the whole stack. The picture it paints is the most complete architecture snapshot of HH in the chats:

- **Backend**: a single ~300k-char `application.py` Flask app (auth, admin, Canvas, payments, college-calculator routes), **SQLAlchemy** models, **Celery** background jobs (`sync_all_users_canvas`).
- **AI**: `ai_chatbot.py` (Gemini via `google.generativeai`, per-class JSON memory), a `local_llm_service.py` fallback, and `enhanced_ai_service.py` orchestrating a KB + assignments + learning-style into personalized study plans.
- **Canvas**: a `CanvasAPI` wrapper *plus* a `canvas_scraper.js` DOM-scraping fallback for campuses that block tokens.
- **Gamification**: `buddy_coins.py` (coins for assignments/quizzes/tests, leaderboards, achievements).
- **Payments**: Stripe checkout/subscription wrapper, gating premium features.
- **Storage/deploy**: local JSON + S3 helpers, WSGI/Procfile/Elastic Beanstalk configs (see [[Deploying a Flask App - AWS Elastic Beanstalk, GitHub Actions, and IAM Keys (chat)|Deploying a Flask App - AWS Elastic Beanstalk, GitHub Actions, and IAM Keys]]).

ChatGPT's main refactor advice — split the monolithic `application.py` into Flask Blueprints, migrate JSON state into SQL, centralize the campus-policy table, and audit for committed secrets — is concrete technical-debt guidance Traveler is now carrying.

## The custom "mode" command system

Midway, the chat pivots to how Traveler has *configured ChatGPT itself*. He screenshots his Customize/Personalization panels (personality set to **"Cynic"**, traits factual-first + chatty/witty/straight-shooting, memory and chat-history ON) and merges them with an earlier "18-year-old, grotesque-but-safe humor" style into one persona. He then designs a **numeric command syntax** he wants saved to memory and displayed at the start of every chat (or on the keyword "options"):

- **0** = Normal (his merged cynic/witty default)
- **1** = Researcher (pure breakdown/summary, no analysis)
- **2** = Data Analyst (code, calculations, formulas)
- **3** = Advice Giver (best ranked recommendations)
- **4** = Coder (expert debugging in n8n/Python/JS/C++, especially for Homework Hatch)

He uses it immediately (`4: refine the code`, `4: explain the code`). This reveals a meta-habit: Traveler treats his AI assistant as a configurable tool to be engineered, mirroring how he builds HH's own [[The One]]/Anna assistant and his [[n8n Automation Crash Course and AI Gmail Workflow (chat)|n8n]] command routers. It also confirms the personalization context that surfaces across his chats — the AI "knows" his PC build, college apps, and finance/AI interests.

## Tangents

Two unrelated detours: a detailed summary of the **"AI 2027"** forecast (the AI Futures Project scenario of agentic AI, "OpenBrain," misaligned Agent-4, and US–China compute competition), and a rundown of the **AI scaling laws / "scaling paradox"** (Kaplan, Chinchilla, test-time/inference scaling, diminishing per-dollar returns). These show his live interest in AI-industry trajectory, consistent with his [[UVA and the Quant Question]] and [[Intellectual Interests]] profile.

## Why it matters

This single chat captures Traveler operating on three layers at once: solving a real infrastructure bottleneck for [[Homework Hatch (startup)]] (per-campus Canvas access), getting his entire codebase explained to him as a non-coder, and engineering his own AI tooling into a custom mode system. It is strong evidence of the founder-who-can't-yet-code-but-directs-the-build pattern that recurs across his startup chats.
