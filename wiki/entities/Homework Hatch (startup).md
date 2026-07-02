---
type: entity
created: 2026-06-15
updated: 2026-06-17
tags: [project/startup, ai, entrepreneurship]
sources: ["[[idea]]", "[[business plan]]", "[[prices]]", "[[plan for next week (hwbuddy)]]", "[[Homework Hatch Stuff]]", "[[Homework Hatch Codebase Walkthrough and Backslash-Zip EB Deploy Failure (chat)]]", "[[Filing the Maryland LLC for Homework Hatch - Articles, EIN, and Stripe (chat)]]", "[[Canvas API Key Revoked - Extension Scraper and LMS Access Strategy (chat)]]", "[[n8n Command Router for Homework Hatch - Telegram, Calendar, Instagram (chat)]]", "[[Homework Hatch Competitor Strategy and the Admin-Free Privacy Pivot (chat)]]", "[[Learning to Code for Homework Hatch - Beyond Vibe Coding (chat)]]"]
status: active
---

# Homework Hatch (startup)

[[Traveler Stansberry]]'s real edtech/AI venture (2025), variously called **Homework Hatch**, **SPHW Buddy**, and **HW Buddy** — the concrete, real-world version of the AI ambition he keeps circling in his fiction.

## The product
An AI study platform that ingests a student's **LMS data** (Canvas, Schoology) and turns it into:
- AI study plans, summaries, practice quizzes (Kahoot/Gimkit-style), a class-focused chatbot
- A **college-acceptance-% calculator**, recommendations, test prep
- A gamified "**Buddy Coins**" arcade economy (coins earned by completing assignments)
- Class/grade/club chats

## Business thinking ([[prices]], [[idea]])
Three tiers — Normal $10 / Premium $20 / Pro $25 — with AI cost modeled at ~$2–3/user and hosting ~$2/user. The [[idea]] note includes a full ChatGPT-assisted pricing & break-even analysis (e.g. the "premium trap" problem). Tech stack surfaced in his notes: **AWS** (Elastic Beanstalk), **GitHub Actions**, **Playwright** (automated LMS login w/ 2FA handling), **Stripe**, iOS App Store release.

> [!warning] Security
> An associated note held **live AWS credentials in plaintext** and was deleted during ingest; those keys should be rotated. (Logged in [[log]].)

## Building it for real — the ChatGPT build log (2025–26)
His ChatGPT export (51+ chats) turns Homework Hatch from a plan into a documented build. He shipped it largely by **"vibe coding" in [[Cursor (AI code editor)|Cursor]]**, then deliberately set out to *actually* learn to code so he could understand and edit his own app ([[Learning to Code for Homework Hatch - Beyond Vibe Coding (chat)]]).
- **Stack & deploy:** a **Flask** backend on **AWS**, evolving from **Elastic Beanstalk** → **App Runner + ECR** (he hit a 12 GB Docker-image wall), with **GitHub Actions** CI/CD, IAM keys, content filtering, and WebSocket config ([[Deploying a Flask App - AWS Elastic Beanstalk, GitHub Actions, and IAM Keys (chat)]], [[Fixing the Docker-to-ECR Push Failure for Homework Hatch - App Runner and the 12GB Image (chat)]], [[Launch to AWS Elastic Beanstalk - Flask Deploy and WebSocket Config (chat)]]). He repeatedly uploaded full codebase zips for architecture reviews ([[HW Buddy App Architecture Analysis and GPT-5 Model Choice (chat)]]).
- **Co-founder [[Josh (Homework Hatch co-founder)|Josh]]:** he walked through granting Josh AWS Identity Center access screen-by-screen ([[AWS Identity Center Setup for Homework Hatch and Wikipedia Training Dataset (chat)]]).
- **LMS ingestion — the pivot:** the plan relied on the **Canvas API**, but his school **revoked the API key**, forcing a pivot to a browser-extension scraper and cloud-storage OAuth (Google Drive / Microsoft OneDrive), where he ran into the OAuth consent-screen wall ([[Canvas API Key Revoked - Extension Scraper and LMS Access Strategy (chat)]], [[OneDrive Azure Integration and the OAuth Consent Wall for Homework Hatch (chat)]], [[Google Drive Folder Tree Mirroring for Homework Hatch (chat)]]).
- **n8n automation ("Anna"):** an "AI secretary" built in **[[n8n (automation platform)|n8n]]** — a Telegram voice note → Google Calendar assistant (chronic date-drift bug), a command router across Telegram/Calendar/Instagram, plus Instagram marketing automation ([[n8n Command Router for Homework Hatch - Telegram, Calendar, Instagram (chat)]], [[n8n Debugging - Google Calendar Voice Assistant for Homework Hatch (chat)]]). Also a prototype Discord bot on the OpenAI API.
- **Incorporated:** filed as a **Maryland LLC** (Sept 2025) — Articles of Organization, EIN, domain transfer, Stripe ([[Filing the Maryland LLC for Homework Hatch - Articles, EIN, and Stripe (chat)]]).
- **Business & launch:** valuation + AWS unit-cost modeling, GPT-5 model selection, a study-materials spec (flashcards, live quiz, practice banks) written as Cursor prompts, and a pre-launch **competitor strategy with an "admin-free privacy pivot"** ~2 weeks before launch ([[Homework Hatch Competitor Strategy and the Admin-Free Privacy Pivot (chat)]], [[Study Materials Spec for Homework Hatch - Flashcards, Live Quiz, Practice Banks (chat)]]).
- **Compliance/ethics:** he red-teamed his own startup's Terms of Service and interrogated the cheating-liability of using third-party LLM APIs commercially ([[Custom LLM Build and SPHW Buddy Terms of Service (chat)]], [[Gemini vs OpenAI API ToS and Cheating Liability for Homework Hatch (chat)]]) — the same anti-cheating tension that drives [[The One]].

## He also taught it
His [[Coding Club]] curriculum (Python → APIs → "pull Canvas data" → Flask on AWS → AI study-tool generators) is the Homework Hatch skill-stack, taught to others. His résumé title: **"Co-Founder, Central Coder"**; skills listed — Python, Flask, SQL, n8n, APIs.

## Why it matters
This is the autobiographical root of [[The One]] — his short story about an MIT student destroyed by AI-startup ambition — and of his lifelong [[Do Androids Dream of Electric Sheep?|fascination with AI]]. Where the fiction is cautionary, the notes are earnest and operational: he's actually building it.

## See also
[[The One]] · [[Do Androids Dream of Electric Sheep?]] · [[College Search]] (finance/CS direction) · [[Consumerism and Alienation]]
