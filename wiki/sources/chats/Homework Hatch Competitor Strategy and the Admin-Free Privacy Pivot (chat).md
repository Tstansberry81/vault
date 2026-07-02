---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2025-09-19
author: Traveler Stansberry
source_type: chat
tags: [chat, startup, homework-hatch, strategy, product]
status: active
---

# Homework Hatch Competitor Strategy and the Admin-Free Privacy Pivot

A long, decision-dense ChatGPT (GPT-5) strategy session for [[Homework Hatch (startup)]], dated **two weeks before launch** ("we launch in 2 weeks... marketing is going to start rolling out over the weekend and I'm going to vibe code the rest"). It starts as a competitive analysis and ends as the chat where Traveler crystallizes the product's core identity: a **student-only, faculty-free, privacy-as-premium ed-social-media app**. This is one of the most important positioning documents in the whole startup corpus — it is where HW Buddy stops being "AI homework help" and becomes "the Discord of studying your school can't see."

## The competitive map
Traveler asked for a thorough teardown of competitors. The model laid out the landscape: **Quizlet** (Magic Notes, spaced repetition, habit-forming), **Chegg/CheggMate**, **Course Hero/Learneo** (Symbolab, QuillBot, Scribbr bundle), **Photomath/Wolfram/Symbolab** (STEM step-by-step), **Perplexity**, **Notion AI**, **StudyX/Discord study bots**; the Canvas-integrated tier (**Gradescope, Perusall, Packback**, all riding LTI 1.3); and admissions tools (**Scoir, Naviance**) relevant to HH's "college odds" feature. He specifically asked about **MyWhiteboard.ai** (200k+ students, video/lecture digestion) as a near-competitor. The recommended moat: be the *course-aware copilot* with "Proof Mode" (no answer until you attempt) and citations everywhere — out-context Quizlet, out-trust Chegg.

## The pivot: kill the institutional play
The orchestrating decision happens mid-chat. Traveler reveals he has been using **student personal API keys** to reach Canvas. The model pushed hard toward **LTI 1.3 + LTI Advantage** (NRPS rosters, AGS grade passback, Deep Linking) — walking through the full OIDC launch flow, JWKS hosting, Flask `/lti/login` and `/lti/launch` routes, and the Canvas Developer Key admin install. But Traveler rejected the entire premise: he wants the app **admin- and faculty-free on purpose**. His thesis, stated plainly:

> "Students trust that they can use our application however they want to without school faculty or administrators hovering over them and their data."

This is a deliberate strategic trade — giving up system-wide campus contracts (big money) for bottom-up viral student adoption (the Quizlet/Photomath/Notion playbook). It is a textbook expression of his [[Political and Economic Views]] and [[Individual vs. Society]] instincts applied to a product: anti-surveillance, pro-individual-control, distrustful of institutional gatekeepers.

## What replaces LTI: a student-owned scraper
Because there is no admin install, HH ingests Canvas through what the *student* can give it. The model handed Traveler a complete **Chrome MV3 extension** scaffold: `manifest.json` with `instructure.com` host permissions, a `content.js` that hooks the History API to detect Canvas SPA route changes, `extractors.js` DOM parsers for Modules/Assignments/Pages (resilient selectors, `window.ENV` for course IDs), and a `background.js` service worker that stores the HH JWT and an optional Canvas **PAT** in `chrome.storage.local` (never the server) and POSTs scraped text to Flask `/ingest/scrape`, `/ingest/assignments_api`, and `/ingest/file` routes feeding a chunk-embed-RAG pipeline. The privacy story is structural: only scrape the page the student is already viewing, files only leave the browser on explicit click, big red "Delete all my data" button.

## Privacy-as-premium and ed-social-media
Traveler clarified he was never going to monetize data — he wants to **charge a premium for privacy** and market HH "kind of like an ed-social media." The model leaned into "the Discord of studying": end-to-end encryption and local-first storage as the paid tier, study rooms, shared flashcard decks, anon posting, streaks/badges visible only to friends and never to teachers, course-specific hubs ("Intro to Psych at [School]"). Crucially, Traveler noted HH **already has club, grade, and class chats** — so the plan is to make those chats the collaboration backbone: drop a homework assignment in chat, friends co-work it (possibly via Word Online / Google Docs deep-links), HH auto-generates a shared deck + quiz. The flywheel: one student uploads the Psych slides, the whole class wants in.

## Feature and infra decisions
- **Google Drive + OneDrive deep-links:** full walkthrough of the Google Picker (GIS OAuth, `drive.file` scope), MSAL.js + Graph File Picker, programmatic time-limited share links (`createLink` with `expirationDateTime`), and org-only fallback when school tenants block anonymous links.
- **Khan-style explainer videos:** Traveler wants AI-generated whiteboard lessons saved in the user's library. The model steered him *away* from cinematic text-to-video toward a deterministic, cited pipeline — RAG storyboard JSON → TTS → whiteboard/slide-overlay/[[Manim]]-graph renderers → FFmpeg compose. Refuse to narrate anything not traceable to the source slide.
- **AI stack pick (the "default" ship list):** Claude 3.5 Sonnet for tutoring/scripts (GPT-4o backup), `text-embedding-3-large`, Cohere rerank-3, PGVector→Qdrant, SymPy + Wolfram for math, faster-whisper, ElevenLabs TTS, Celery + Redis, S3. (For the 2-week crunch he was told to drop to one LLM, `text-embedding-3-small`, and a static-slide MVP video.)
- **Hosting / long-term:** ship the launch on the existing [[Homework Hatch (startup)]] Elastic Beanstalk setup, then migrate to containers — AWS App Runner + ECS Fargate + RDS/pgvector + S3/CloudFront for enterprise optics, or Render + Neon + Cloudflare R2 for developer sanity. Multi-tenant by `(user_id, tenant_id)`, feature flags, queues split into indexing/video/asr.

## What it reveals
This chat shows Traveler operating as a real founder making a hard, brand-defining trade-off and overriding the AI's default enterprise advice with conviction. He is comfortable rejecting "best practice" (LTI 1.3) when it conflicts with his thesis, and he frames the product's edge in ideological terms — privacy, student ownership, no surveillance — that mirror his personal convictions. It also pins HW Buddy's real architecture at this stage: Flask + browser-extension scraping + per-user RAG, with chats as the existing social spine. It connects to his broader work in [[Coding Club]] (he teaches the skills he's vibe-coding here), his [[Investment Club]]-adjacent founder ambitions, and the [[UVA and the Quant Question]] / finance trajectory of [[Traveler Stansberry]].

> [!note] Related HH chats
> See the LTI/scraping debates in [[Zyn Air Travel then HW Buddy LMS Scraping Strategy (chat)]], [[Agentic AI, MCP, and LMS Credential Ingestion for Homework Hatch (chat)]], and [[Canvas LMS Adoption Research for Homework Hatch (chat)]]; the cheating-liability tension in [[Gemini vs OpenAI API ToS and Cheating Liability for Homework Hatch (chat)]]; and the EB hosting work in [[Deploying a Flask App - AWS Elastic Beanstalk, GitHub Actions, and IAM Keys (chat)]].
