---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2025-10-19
author: Traveler Stansberry
source_type: chat
tags: [chat, startup, homework-hatch, product-spec, edtech]
status: active
---

# Study Materials Spec for Homework Hatch - Flashcards, Live Quiz, Practice Banks

A product-design session for [[Homework Hatch (startup)]] in which Traveler scopes a **Study Materials** feature set, asking ChatGPT to write a behavior-only specification he can feed straight into Cursor to generate code. The explicit framing — "give me descriptions of each so i can feed it to cursor so it will know how to code it" — shows his settled spec-then-vibe-code workflow: write a clean conceptual blueprint in natural language, then hand it to the AI agent to implement. His follow-up ("do it all in words with no reference to ui changes, dependencies, or anything else. just the raw ideas") deliberately strips out framework/UI noise to get a clean domain model, a sign of growing engineering discipline beyond pure vibe-coding (see [[Learning to Code for Homework Hatch - Beyond Vibe Coding (chat)]]).

## The three pillars
Traveler explicitly clones the UX of three category-leading apps:
- **Flashcards** modeled on **Quizlet** — Flip/Learn/Write/Test modes with **SM-2 spaced-repetition** scheduling (0–5 grade scale, ease/interval/repetition tracking, due queues, mastery thresholds), tolerant answer matching (case/punctuation normalization, synonym lists, Levenshtein fuzzy thresholds, multiple correct orders flagged for language learning).
- **Live Multiplayer Quiz** modeled on **Kahoot** — host-driven session lifecycle with join codes, per-question countdown/lock/reveal, server-authoritative scoring with linear time-decay bonuses, streak bonuses, difficulty multipliers, anti-replay nonces, reconnect tokens, and tie-breaker rules.
- **Practice Quizzes** modeled on **Canvas** quizzes — async assessments with item pools, attempt policies (limits, timers, navigation, randomization, accommodations), autosave/resilience with the server as time authority, partial-credit grading, rubric-based manual grading for essays, regrade-on-key-change with audit trails, and review-visibility policies.

## Shared architecture
The spec lays out a unified content model — sets, cards, question banks, quizzes, attempts, sessions, reports — with tagging, learning objectives, ordinal difficulty, privacy levels (private/shared/public), and version immutability (active attempts bind to a fixed question version). It also covers a ten-type question schema (MC, multi-select, T/F, short answer, numeric-with-tolerance, matching, ordering, hotspot, essay, file upload), item analytics (p-value difficulty, point-biserial discrimination), and a recommendation engine that routes weak objectives back into flashcard study.

## What it reveals
This is one of the clearest snapshots of Traveler operating as a product manager rather than a student: he is reverse-engineering the three apps his target users (high schoolers) already live in, and folding them into [[Homework Hatch (startup)]]'s LMS-integrated platform. The emphasis on integrity signals (focus-loss tracking, blur counts, rapid-response flags) ties into the cheating-liability tension that recurs across his startup chats — he wants study tools that feel legitimate to schools, not a cheating engine. The level of detail (SM-2 math, server-authoritative scoring, regrade audit trails) shows he is thinking about real assessment infrastructure, not a toy MVP. Connects to his broader build stack work in [[HW Buddy App Architecture Analysis and GPT-5 Model Choice (chat)]] and [[Cursor and the sisyphus10 Codebase Overview (chat)]].
