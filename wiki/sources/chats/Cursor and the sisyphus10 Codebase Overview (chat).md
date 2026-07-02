---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2025-07-17
author: Traveler Stansberry
source_type: chat
tags: [chat, coding, startup, homework-hatch]
status: active
---

# Cursor and the sisyphus10 Codebase Overview (chat)

A short July 2025 exchange that doubles as a rare architectural X-ray of [[Homework Hatch (startup)]]. Traveler opens by asking how well ChatGPT is "implemented with Cursor" — meaning [[Cursor (AI code editor)]], the AI-native VS Code fork by Anysphere that he had evidently adopted as his IDE. After clearing up that ChatGPT is *not* directly integrated into Cursor (it runs the same underlying GPT/Claude models, so it can advise on prompts, diffs, and refactors alongside it), he asks whether he can upload a large amount of code so the model can "understand my program." He then uploads a ZIP of the actual project.

## What the codebase reveals

The project directory is named **`sisyphus10`** — the working repo name for his Homework Hatch / SPHW Buddy app (the Sisyphus reference fits his [[Political and Economic Views|determinist]] streak). The model extracts and summarizes it as a **Flask** web app that is a *student performance tracking and gamification platform* built around **Canvas LMS** integration. Concrete components:

- `application.py` — main Flask app; routes for dashboard, login, grading, class views, messaging, Canvas sync.
- `auth.py` — Flask-Login auth with registration, email verification, and **admin approval** workflow.
- `buddy_coins.py` — the "Buddy Coins" reward/points engine: coins awarded by assignment type and grade, admin bonuses, bet winnings, with leaderboards and CSV export.
- `canvas_integration.py` — Canvas API client pulling courses, assignments, and grades.
- `content_filter.py` — chat moderation for illicit content in user messages.
- `s3_data.py` — reads/writes JSON to **AWS S3** (data persisted as flat JSON files: `buddy_coins.json`, `chat_messages.json`, `grades_data.json` — no real database).
- `auto_git_watchdog.py` — watches for file changes and auto-commits to Git (deployment automation).
- Deploy stack: AWS **Elastic Beanstalk** (`.ebextensions`, `.elasticbeanstalk`), `Procfile`, `requirements.txt`.

Notably, the model flags that **OpenAI / AI feedback is commented out** at this stage — the "AI study help" piece was scaffolded but not yet live.

## Why it matters

This is the most direct picture in the wiki of how Homework Hatch was actually *built*: a solo-developed Flask + S3-JSON + Elastic Beanstalk stack, Canvas-grade syncing, and a gamification layer (Buddy Coins, leaderboards, and even a **betting/gambling-on-grades** mechanic) — chosen for engagement. It shows Traveler's real workflow as a self-taught builder leaning on [[Cursor (AI code editor)]] and ChatGPT as pair programmers, consistent with his [[Coding Club]] teaching and [[Extracurriculars and Achievements|extracurricular]] profile. The reliance on flat JSON files over a database and the commented-out AI hint at an early, pre-scaling prototype.
