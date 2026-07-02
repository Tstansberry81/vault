---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2025-09-10
author: Traveler Stansberry
source_type: chat
tags: [chat, coding, startup, learning]
status: active
---

# Learning to Code for Homework Hatch - Beyond Vibe Coding

A September 2025 conversation in which Traveler, having built [[Homework Hatch (startup)|Homework Hatch]] almost entirely through "vibe coding" in Cursor, asks how to actually *learn* to code so he can understand and edit his own app. The chat is a candid window into where his technical self-education stood: he had a working full-stack codebase he did not understand. It connects to his role running the [[Coding Club]] and his broader [[Intellectual Interests|intellectual]] ambition to own his startup end-to-end.

## What he asked
He opened by asking for beginner coding apps, probed gamified platforms (Codédex, Grasshopper, Mimo, Sololearn), then pivoted to the real question: for Homework Hatch, is he better off with gamified tools or "just diving deep"? The model was blunt — gamified apps are "training wheels on a tricycle" and he'd outgrow them in two weeks because HH needs Python (AI/backend), JavaScript/Node, HTML/CSS, and real API/database work that XP badges never teach.

## The architecture walkthrough (most valuable part)
Traveler re-uploaded `HOMEWORK HATCH 9-3.zip` and got a line-by-line, beginner-framed tour of his own app. This is the clearest single inventory of the HH stack at that date:

- **Backend**: Flask (`application.py`, a 300k+ char mega-file of routes), SQLAlchemy ORM (`models.py`, `database.py`), Celery background jobs (`tasks.py`, `celery_config.py`).
- **Frontend**: Jinja2 HTML templates, static assets.
- **AI**: Gemini via `google.generativeai` (`ai_chatbot.py` with per-user/per-class JSON memory), a local-LLM fallback wrapper, and `enhanced_ai_service.py` orchestrating personalized study plans.
- **Canvas**: an API path (`CanvasAPI` wrapper with bearer token) plus a DOM-scraper JS fallback served via Flask for campuses that block tokens.
- **Payments**: Stripe subscription wrapper gating premium features.
- **Storage**: local JSON / SQLite + AWS S3 helpers.
- **Gamification**: `buddy_coins.py` (10 coins per assignment, 20 quizzes, 30 tests, plus grade bonuses, leaderboards).
- **Deploy**: `wsgi.py`, Procfile (gunicorn), Elastic Beanstalk configs, `requirements.txt`.

The model flagged real weaknesses: the monolithic `application.py` should be split into Flask Blueprints with an app factory; JSON state should migrate into SQL; secrets hygiene needs `.env` discipline; and the Canvas merge filters need unit tests so real assignments aren't dropped. It supplied a full drop-in Blueprint scaffold (`app/__init__.py`, `routes/auth.py`, `routes/canvas.py`, etc.).

## The learning toolbox
He repeatedly insisted on *applications* he could install, not concepts. The recommended real-world stack: VS Code (over Cursor, to "stare at raw code and suffer properly"), Postman, DB Browser for SQLite, GitHub Desktop, Heroku CLI then AWS EB CLI, Stripe CLI, Jupyter/Anaconda. Learning apps: freeCodeCamp, Codecademy, Mimo, Khan Academy SQL, plus *Automate the Boring Stuff with Python*.

## The timeline reality check
As a full-time HS student (1–2 hrs weekdays, 3–5 weekends), the model estimated **9–12 months / ~300–400 hours** to own HH end-to-end, or a **3–4 month / ~120 hour** shortcut just to "read and lightly edit without breaking it." It framed the effort as equivalent to one serious extracurricular — fitting given his [[Extracurriculars and Achievements|packed slate]].

## What it reveals
This is the honest baseline of Traveler-as-builder circa fall of senior year: a founder who shipped a genuinely complex Flask/AI/Stripe/Canvas product via AI assistance but couldn't yet read it. It documents his self-awareness about the gap between "vibe coding" and real fluency, and his determination to close it — consistent with the [[UVA and the Quant Question|technical ambition]] he carries toward finance/CS.
