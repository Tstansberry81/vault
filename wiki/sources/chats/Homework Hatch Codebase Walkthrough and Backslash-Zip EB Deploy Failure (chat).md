---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2025-10-22
author: Traveler Stansberry
source_type: chat
tags: [chat, startup, coding, deployment]
status: active
---

# Homework Hatch Codebase Walkthrough and Backslash-Zip EB Deploy Failure

Traveler uploaded a zipped export of the entire [[Homework Hatch (startup)]] project and asked ChatGPT (GPT-5) to read the whole directory and explain what the app attempts to achieve. This is one of the most complete single-shot inventories of the codebase in the chat corpus — a useful snapshot of the product's actual scope as of October 2025.

## What the codebase actually is
A monolithic **Flask** web app aiming to be an all-in-one student platform. The assistant verified these major capabilities in code/templates:
- **Canvas LMS integration** — imports courses/assignments, maps Canvas structures to local models, processes attachments, runs background sync on intervals (the `docs/AUTO_SYNC_README.md` describes a "every 10 minutes" loop).
- **File mirroring** — `google_drive_sync_manager.py` and `onedrive_sync_manager.py` plus `*_sorter.py` modules fetch, dedupe, and sort class materials.
- **AI study-materials generation** — `comprehensive_ai_service.py` / `study_materials_manager.py` produce study guides, flashcards, summaries, and practice questions from PDFs/Docs/PPTs, with content filtering.
- **Live multiplayer quiz / "arcade"** — `live_quiz_websocket.py` runs a real-time engine on **Flask-SocketIO** with host-controlled rooms, scoring, and leaderboards.
- **Class and global chat**, a **college admissions calculator** (GPA, in-state, athletics, first-gen, ED-rate factors), **Stripe** payments/tiers, an **admin console** ("Teacher Jarvis", user audits, payment bypasses, disciplinary types, chat wiping), and a **"Buddy Coins"** progress economy.

Stack: Flask + Flask-Login + Flask-SQLAlchemy + Flask-SocketIO, served by gunicorn via `wsgi.py` (`application`), SQLAlchemy models with several local SQLite DBs, S3 storage, and a `.ebextensions/` layout built for Elastic Beanstalk. The single `application.py` is described as ~440k chars of "all-roads-lead-to-Rome" — the monolith that recurs across the [[Learning to Code for Homework Hatch - Beyond Vibe Coding (chat)]] and deployment chats.

## Operational red flags the assistant caught
- Traveler had **committed his entire `venv/`** (~19,345 files), bloating the bundle.
- **Real API keys and client secrets were sitting in `.env`** — the assistant told him to move them to EB environment variables and rotate the exposed ones.
- In-process threaded schedulers will double-run under multiple gunicorn workers/instances; recommended a separate EB worker env, EventBridge, or an S3/Redis leader lock.

## The "turn your memory on dumbass" exchange
A revealing bit of Traveler's blunt, impatient register: he repeatedly ordered ChatGPT to permanently "save to memory" its understanding of Homework Hatch, and the model kept explaining it can't self-enable memory. He even screenshotted his settings toggles. Characteristic of how he treats the tool as a persistent collaborator on the startup.

## The deploy crash (the technical payload)
After asking for the "best way to deploy," Traveler pasted EB logs showing the deploy died before touching Python:
```
appears to use backslashes as path separators
unzip ... failed with exit status 1
```
Root cause: the ZIP was created on **Windows**, so paths used backslashes; Linux `unzip` on Elastic Beanstalk treated them as filename characters and aborted staging. Fixes offered: deploy via `eb deploy` (CLI builds a proper POSIX zip), re-zip in WSL/Git Bash, or `git archive --format=zip`. Also flagged the slash in the version label `Homework Hatch/beta1` (should be `Homework-Hatch_beta1`) and the Socket.IO Procfile needing `eventlet` (`gunicorn --worker-class eventlet -w 1`).

This connects directly to the long-running EB saga in [[Deploying a Flask App - AWS Elastic Beanstalk, GitHub Actions, and IAM Keys (chat)]], [[Launch to AWS Elastic Beanstalk - Flask Deploy and WebSocket Config (chat)]], and [[Content Filtering and the Elastic Beanstalk Deploy Loop (chat)]]. It shows Traveler operating well above "vibe coding" on infrastructure he doesn't fully control, troubleshooting real production failures for his [[Extracurriculars and Achievements|edtech venture]] — part of his [[Intellectual Interests|builder profile]] and [[UVA and the Quant Question|pre-finance/CS]] trajectory.

![[770ac289-38f3-4a5f-af4c-aaadda68bae4.png]]
