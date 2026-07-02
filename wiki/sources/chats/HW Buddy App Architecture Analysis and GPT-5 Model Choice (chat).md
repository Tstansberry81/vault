---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2025-08-30
author: Traveler Stansberry
source_type: chat
tags: [chat, startup, homework-hatch, coding, llm]
status: active
---

# HW Buddy App Architecture Analysis and GPT-5 Model Choice

Traveler uploads a `HWBUDDY 8-27.zip` of his [[Homework Hatch (startup)]] codebase and asks ChatGPT to "analyze this... tell me all about it." The model reverse-engineers the project structure from filenames, then the chat pivots to practical questions about updating his OpenAI API key and choosing a GPT-5 variant for a Discord bot. The conversation is a useful snapshot of how far the app's scaffolding had grown by late August 2025.

## What the codebase contains

The model maps HW Buddy as far more than a chatbot — a "full student productivity ecosystem" built in Python/Flask:

- **Entry points** — `application.py` (student/teacher UI) and `admin_app.py` (admin panel), confirming a split between the user-facing app and an oversight back end.
- **AI layer** — `ai_chatbot.py`, `ai_service.py`, and `educational_llm_service` wrap the model calls that produce summaries, flashcards, and study guides.
- **Canvas integration** — `background_canvas_sync.py` (a background worker), a `canvas-automation/` folder (`analyze_canvas_data.py`, `clean_canvas_data.py`, `install_canvas_extension.py`), and live `background_canvas_sync.log` files. This is the LMS-ingestion plumbing that pulls assignments, grades, and due dates automatically.
- **Gamification** — `buddy_coins.py` (a "Buddy Coins" reward economy) and an `arcade/` folder (`arcade_games.py`, `arcade_routes.py`) embedding mini-games tied to the coin system for engagement/stickiness.
- **Admin "control tower"** — HTML templates for user management, chat monitoring, system logs, and API-usage/cost tracking, plus `admin_disciplinary_system.py` and `content_filter.py` for moderation and anti-cheating safeguards.
- **Infra/dev tools** — `auth.py` (OAuth/JWT), `auto_venv.py`, `wsgi.py` (Gunicorn/WSGI hosting), and caching, consistent with his AWS Elastic Beanstalk deployment work.

The model's pitch summary: HW Buddy as "Duolingo + Canvas + ChatGPT + Kahoot + Discord" in one. This corroborates the breadth seen in his other startup chats — the Canvas/LMS credential ingestion, content filtering for cheating liability, and Maryland LLC/business setup.

## Model-selection questions

After a tangent, Traveler asks how to update his API key to run a newer ChatGPT version, both for HW Buddy and an unrelated Discord bot. Key takeaways the model gives:

- The **API key is just authentication** — the model version is set by the `model=` parameter in the request (e.g. swap `"gpt-4o-mini"` to `"gpt-5"`), and keys belong in a `.env` env var, never hard-coded.
- GPT-5 launched **Aug 7, 2025** and is available across all tiers; via API the variants are `gpt-5`, `gpt-5-mini`, `gpt-5-nano`, and `gpt-5-chat-latest`.
- Recommendation for the Discord bot: default to cheap/fast `gpt-5-mini` for casual use, gate a `!smart` command to full `gpt-5` for tutoring/coding/essay help — a tiered approach to control API spend.

> [!note] Accuracy
> The model's API/pricing claims here are GPT-5's own marketing-era summary and should not be treated as authoritative — these are exactly the kind of LLM-provider details worth verifying against current docs.

## What it reveals

This is Traveler operating as the technical founder of [[Homework Hatch (startup)]]: he treats the LLM as a code-archaeology and ops assistant rather than building from scratch. It shows real engineering maturity — background workers, an admin panel, content moderation, cost tracking — and confirms the [[Coding Club]]-adjacent skill set he applies to the venture. The casual jump to a personal Discord bot shows the same toolkit spilling into hobby projects. Connects to his broader [[Intellectual Interests]] and the practical, build-first cast of his [[Extracurriculars and Achievements]].
