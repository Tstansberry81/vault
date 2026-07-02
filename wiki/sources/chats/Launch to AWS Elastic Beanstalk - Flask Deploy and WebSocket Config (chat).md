---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2025-10-21
author: Traveler Stansberry
source_type: chat
tags: [chat, coding, startup, aws, deployment]
status: active
---

# Launch to AWS Elastic Beanstalk - Flask Deploy and WebSocket Config

A deployment-engineering session (GPT-5, 21 Oct 2025) in which Traveler uploaded the actual source zip of [[Homework Hatch (startup)]] (`HOMEWORK HATCH 10-20.zip`) and asked for a step-by-step plan to push the app live on **AWS Elastic Beanstalk** ahead of an expected ~100 users in the first month. It is one of the clearest windows into the real technical architecture of the product as it stood in late 2025, just before launch.

## What the repo actually is (per the read zip)
- A **Python/Flask** app: entry point `wsgi.py` (`from application import application`), served by **Gunicorn** via a `Procfile`.
- Real-time features through **Flask-SocketIO** (`socketio = SocketIO(application, cors_allowed_origins="*")`), with a custom `/quizws` path — i.e. a live-quiz feature alongside `/socket.io/`.
- EB deployment config already scaffolded: `.ebextensions/01_app.config` (port 8000, WSGIPath, static mapping) and `.ebextensions/02_nginx.config` (a bare reverse proxy missing WebSocket upgrade headers).
- `config.py` reads a long list of env vars revealing the integration surface: `OPENAI_API_KEY`, `CANVAS_API_URL`/`CANVAS_API_TOKEN`, `GOOGLE_CLIENT_ID/SECRET`, `MICROSOFT_CLIENT_ID/SECRET`, SMTP creds, `STRIPE_SECRET_KEY`/`STRIPE_PUBLISHABLE_KEY`/`STRIPE_PRICE_ID`, and `DOMAIN_NAME` (homework-hatch.com).
- Bundled **SQLite** files (`student_behavior.db`, `educational_knowledge.db`) and heavyweight ML deps (`torch`, `transformers`) in `requirements.txt`.

This confirms the product's shape: a **Canvas-integrated** (the Canvas/Google/Microsoft OAuth keys), Stripe-monetized, OpenAI-backed homework assistant with a live-quiz socket feature — consistent with the LMS-scraping and Canvas-API work documented elsewhere.

## What he was solving
The model produced a repo-specific EB playbook: strip `venv/`/`__pycache__`, zip a clean bundle, `eb init`/`eb create hh-prod --single --instance_types t3.small` with env vars, deploy, then Route 53 + ACM for HTTPS. Traveler pushed back twice — "this doesnt ever mention AWS" and "make sure its specific to only the file i gave u" — forcing increasingly concrete, console-level AWS steps. The final thread ("websocket") drilled into enabling true WebSockets: add `eventlet`/`gevent`, switch the Procfile to `--worker-class eventlet -w 1`, and replace `02_nginx.config` with one passing `Upgrade`/`Connection "upgrade"` headers for `/socket.io/` and `/quizws`.

Notable warnings he was given: EB's EC2 filesystem is **ephemeral**, so bundled SQLite writes are lost on instance replacement (advice: move to RDS/Postgres for durability), and `torch`/`transformers` make first builds slow.

## What it shows
This is hands-on solo infra work — Traveler acting as the sole engineer on a shipping product, not a vibe-coder. It pairs with his other build logs (Elastic Beanstalk deploy loops, IAM/Identity Center setup, GitHub Actions, the Flask architecture analysis) and his stated push to learn real coding "beyond vibe coding." The model addresses him as "Dom," a quirk of his ChatGPT setup. Connects to his [[Coding Club]] teaching, the [[Investment Club]]-adjacent entrepreneurial drive, and his individualist, build-it-yourself bent in [[Political and Economic Views]].
