---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2025-09-16
author: Traveler Stansberry
source_type: chat
tags: [chat, coding, homework-hatch, devops, aws]
status: active
---

# Content Filtering and the Elastic Beanstalk Deploy Loop

A two-part devops session for [[Homework Hatch (startup)]], dated 2025-09-16 (GPT-5 thinking). Both halves are infrastructure work on the live Flask backend, and both reveal Traveler hitting the gap between [[Learning to Code for Homework Hatch - Beyond Vibe Coding (chat)|"vibe coding" and real engineering]] when an AI-tutoring product has to actually ship and stay up.

## Part 1 — content moderation on Python 3.13
Traveler asks for "the best course of action to install content filtering with python 3.13.7." This is a product-driven question: an edtech app aimed at students needs to filter abusive or unsafe text. The advice steers him away from heavy local PyTorch/Transformers stacks (whose 3.13 wheel support was still spotty) toward:
- **Managed moderation APIs** as the primary path — OpenAI's `omni-moderation-latest` (free for API traffic, multimodal) plus Google's Perspective API as a second toxicity signal.
- A **scikit-learn** (LogReg / linear SVM on TF-IDF) local backstop that installs cleanly on 3.13, plus a regex/deny-list rule layer in front.
- A `ModerationClient` adapter abstracting `check_text` / `check_image`, with config-driven thresholds (allow / warn / block / escalate) and audit logging.
- If he ever wants frontier local models, run them as a **separate Python 3.12 microservice** over HTTP rather than forcing one environment to do everything.

This connects to his recurring concern about [[Gemini vs OpenAI API ToS and Cheating Liability for Homework Hatch (chat)|API terms and cheating/liability]] — moderation is part of keeping the product defensible.

## Part 2 — the Elastic Beanstalk "Groundhog Day" deploy loop
Traveler attaches screenshots of an EB environment stuck in a "update config → app deploy fails → retry" loop, with the main app never loading. Diagnosis from his uploaded zip:
- His `.ebextensions` set **both Rolling and Immutable** deployment policies across different config files, *and* changed instance type / ASG sizes in the same deploy — the exact combo EB refuses ("cannot update resource configuration and instance configuration simultaneously with immutable deployments").
- He bundled his **entire 200 MB virtualenv** (~30k files) into the source — EB rebuilds from `requirements.txt` and ignores it, so it only bloated uploads.
- He **hardcoded secrets** (API keys, SMTP) into `.ebextensions/03_environment.config` — flagged as a foot-gun to move into EB environment properties or SSM.

The fix path: pick one deployment policy, strip the venv/`__pycache__`, add a `/health` endpoint, and either move to a Docker container (`python:3.13-slim` + Gunicorn) to lock the runtime, or — when he insists on **non-Docker multi-instance** — a clean load-balanced Python-on-AL2 setup (Min 2 / Max 4 on t3.small/medium, Rolling+Health, minimal `.ebextensions`, `Procfile` running `gunicorn wsgi:application`).

He explicitly wants a "bulletproof" `deployment.py`, and the chat hands him a full boto3 script that builds a clean zip (excluding venv/junk), uploads to S3, creates an EB application version, updates the environment, streams events, waits for health=Green, and **auto-rolls-back** on failure — with a guard that *refuses* to set Immutable alongside capacity changes, the very thing that bricked his env.

## What it shows
This is Traveler operating as a solo founder-engineer: he's running real AWS infrastructure for [[Homework Hatch (startup)]], confronting deployment policy semantics, secret hygiene, and runtime-version dependency hell — the unglamorous reality behind the product. It sits alongside his other AWS work like [[Deploying a Flask App - AWS Elastic Beanstalk, GitHub Actions, and IAM Keys (chat)|the EB / GitHub Actions / IAM chat]] and [[AWS Identity Center Setup for Homework Hatch and Wikipedia Training Dataset (chat)|AWS Identity Center setup]], and reflects the determined, ship-it individualism in his [[Intellectual Profile]] — though he's still leaning on the model to untangle infrastructure he set up faster than he understood it.
