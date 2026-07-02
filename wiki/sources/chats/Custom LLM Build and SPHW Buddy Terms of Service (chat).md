---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2025-08-18
author: Traveler Stansberry
source_type: chat
tags: [chat, startup, coding, llm, legal]
status: active
---

# Custom LLM Build and SPHW Buddy Terms of Service (chat)

A long, two-part [[Homework Hatch (startup)]] working session (GPT-5, Aug 2025). It starts with Traveler wanting to "make a custom LLM with my insane pc" and ends with him red-teaming his own startup's Terms of Service. It is one of the most revealing chats about both his technical ambition and his self-doubt.

## Part 1 — Building a custom LLM on his gaming PC
Traveler asks how to train a custom LLM on his rig (the [[Gaming PC Specs and ASUS ROG Monitor Troubleshooting (chat)|RTX 5090 Astral, 32 GB GDDR7]]). The model lays out the standard menu: QLoRA fine-tune a 7-8B open base (Llama 3.1, Qwen3, Mistral), train a small GPT from scratch (nanoGPT) to "learn the guts," or — most relevant for his app — do RAG over his own documents. He immediately self-deprecates ("using cursor to code. im not that smart"), so the model pivots to the lowest-friction path: Ollama + LangChain + Chroma RAG, scaffolded in [[Cursor and the sisyphus10 Codebase Overview (chat)|Cursor]].

He then uploads an actual zip of a **from-scratch PyTorch Transformer project** he had already built. It contains a real mini-framework: `custom_llm.py`/`advanced_llm.py` (model defs), multiple training entry points (`train_llm.py`, `train_schoolbot.py`, `train_educational_chat.py`, `train_advanced_undergraduate.py`), `inference.py`, a saved `example_model.pt` checkpoint, plus `hwbuddy_chatbot_integration.py` and `schoolbot_core.py` — i.e. an education-focused chatbot scaffold wired toward HW Buddy. The model rates it a "teaching-grade mini-GPT" and gives a detailed correctness review: set `pad_token`, right-shift labels with `-100` masking, enforce causal + attention masks, add AMP/grad-clipping/warmup, save best+last checkpoints, add perplexity eval, and wrap an OpenAI-compatible FastAPI server. Verdict: keep the repo as scaffold but serve a stronger open base (Llama/Qwen via vLLM) for production quality.

The emotional beats matter as much as the technical ones. He asks bluntly "**am i dumb**" — the recurring self-assessment anxiety seen across his chats. The answer reframes it (he built a working jet engine in his garage while most people are at paper airplanes), connecting to his [[Emotional Life and Inner World]] and the gap between his ambition and his perceived ability.

## Part 2 — Drafting and hardening the SPHW Buddy ToS
He pastes a full, AI-generated **SPHW Buddy Terms & Conditions** (note: SPHW Buddy = an earlier name for [[Homework Hatch (startup)]]) and asks for a rating and rewrite. The draft reveals the product's intended feature set in detail:
- GPA/grade tracking, assignment management, AI chatbot tutor
- **Leaderboards and peer grade comparison** (a social/competitive layer)
- A **virtual currency ("Buddy Coins")** and a **"gambling simulation"** feature
- Third-party integrations: **Canvas**, **OpenAI**, **Google Gemini**, Google Classroom
- Maryland governing law (consistent with his [[Maryland LLC Setup, EIN, and Domain Transfer for Homework Hatch (chat)|Maryland LLC]])

The model scores v1 **72/100**, flagging the biggest risks: calling a feature "gambling" (regulator/app-store red flag), peer-visible grades (FERPA/COPPA + bullying exposure), and a Maryland-vs-international jurisdiction conflict. Traveler iterates: rebrand "gambling" → "**Gamified Simulations**," keep grade visibility (says he already built an opt-out button). He pastes an aggressively lawyered v2 (sweeping disclaimers, indemnification, $10 liability cap, 6-month claim window) that the model rates 9.5/10 on legal protection.

The most characteristic exchange is the legal argument he wins on his own. He pushes back: "how is it gambling if no currency is ever exchanged?" and reasons through the three-prong gambling test (consideration, chance, prize) himself — concluding "i think i would win that court case... 'Buddy Coins' cannot be redeemed for any actual currency at any time." This is his [[Political and Economic Views|individualist, first-principles]] streak applied to law, and it echoes his interest in real cases (e.g. [[Porter Stansberry SEC Case and Antidepressant Queries (chat)|Porter Stansberry's SEC case]]). He also tellingly drops the 18+ restriction once he realizes it's only "a CYA move," not a legal requirement.

## Tail end — quick homework/app errands
The chat trails into unrelated quick hits: a request to "create a logo for hw buddy," a grammar check, the meaning of *parallel structure* and *ambivalence* (vocab for an English essay), and the **NSLC (National Student Leadership Conference)** selection process — whether it's capped at 2 per school (it isn't; rolling admissions, capacity-limited). These connect to his [[College Search]] / [[Extracurriculars and Achievements]] track.

## What it reveals
This is the clearest single window into HW Buddy as a *product*: not just a tutor chatbot but a gamified, social, multi-LLM-backed grade platform with Canvas ingestion (see [[Canvas LMS Adoption Research for Homework Hatch (chat)|Canvas LMS Adoption Research for Homework Hatch]], [[Agentic AI, MCP, and LMS Credential Ingestion for Homework Hatch (chat)|Agentic AI, MCP, and LMS Credential Ingestion for Homework Hatch]]). It also shows Traveler genuinely doing the engineering — a hand-built PyTorch Transformer — while leaning on Cursor and constantly questioning his own competence.
