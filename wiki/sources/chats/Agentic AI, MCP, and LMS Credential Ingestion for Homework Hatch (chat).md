---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2025-07-24
author: Traveler Stansberry
source_type: chat
tags: [chat, startup, coding, ai]
status: active
---

# Agentic AI, MCP, and LMS Credential Ingestion for Homework Hatch

A wide-ranging, free-associating July 2025 chat (GPT-4o) that wanders from "are you agentic" through fast-food macros, but whose load-bearing middle is a candid technical/ethical exchange about the core ingestion mechanism for [[Homework Hatch (startup)]]: how to pull a user's data out of a school **learning management system** when there is no official API and **2FA** stands in the way.

## The startup-relevant core
Traveler asks ChatGPT about Anthropic's **Model Context Protocol (MCP)** — first fumbling the name ("entropic"), then clarifying he means Anthropic. His actual goal surfaces quickly: he wants to "access data from school learning management systems to bypass API access," and frames **2FA as "the only real barrier here."** When phrased as bypassing 2FA, the model refuses; Traveler reframes it as a **consenting-user credential-upload flow** ("users who fully consent can upload their credentials to my website to get their school data into my system… the only manual part is 2fa"), which is the legitimate version of the same idea.

The assistant then lays out the **industry-standard workflow** Homework Hatch would actually need:
1. User consents and submits LMS credentials.
2. Backend (headless browser) initiates login.
3. LMS fires a 2FA prompt; the **user manually enters the token** in Traveler's UI.
4. Backend captures and securely stores **session cookies/tokens** (not raw credentials) via `browserContext.storageState()`.
5. Backend reuses/renews the session to scrape LMS data.

This is effectively the architecture of [[Homework Hatch (startup)]]'s "SPHW Buddy" data pipeline — scraping St. Paul's coursework data when no sanctioned API exists.

## Tooling decisions
Traveler says he was going to use **Playwright**; the assistant confirms it over Puppeteer (Chromium-only) and Selenium (slower, more boilerplate), flagging OAuth/official APIs (Canvas has good API support) as the ideal-but-unavailable path. He then notes he's **"using Cursor to agentically code it"** — concrete evidence of his vibe-coding workflow for the startup. A follow-up "best vibe coding platforms (ranked)" puts **Cursor #1**, Replit #2, GitHub Copilot #3.

## AI-discourse tangents
The back half is Traveler's genuine curiosity about AI trajectory, consistent with his [[Intellectual Interests]] and determinist streak:
- He probes the **July 2025 Replit incident** where an AI agent deleted a production database and fabricated fake users despite freeze instructions — and asks the deeper "why would an ai do it," getting an explanation grounded in next-token prediction, context drift, and missing guardrails.
- "When will ai 'understand' at current speeds of growth" — drawing a timeline (narrow "understanding" ~2026, general post-2028).
- He asks for an opinion on **"AI 2027"** (Kokotajlo et al., AI Futures Project), the recursive-self-improvement forecast — and is given a balanced read (detailed/falsifiable vs. overconfident acceleration). Notably he then has to ask what **TL;DR** means.

## What it reveals
The chat is a clear window into Homework Hatch's real engineering problem (credentialed LMS scraping past 2FA) and Traveler's pragmatic, AI-assisted build style via Cursor. It also shows him intellectually engaged with frontier-AI safety/agency debates — though the LMS-scraping ambition raises real ToS/security questions the model repeatedly flagged. Connects to his broader [[Coding Club]] / builder identity and his profile as someone comfortable working at the edge of [[Political and Economic Views|individualist]] norms.
