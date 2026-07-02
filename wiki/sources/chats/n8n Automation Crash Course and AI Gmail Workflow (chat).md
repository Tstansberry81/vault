---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2025-09-05
author: Traveler Stansberry
source_type: chat
tags: [chat, coding, automation, n8n, homework-hatch]
status: active
---

# n8n Automation Crash Course and AI Gmail Workflow

A September 2025 ChatGPT (GPT-5) session in which [[Traveler Stansberry]] asks for a beginner-level crash course on **n8n**, the visual workflow-automation tool, plus a primer on how Node.js works. This is the conceptual groundwork for the automation layer of [[Homework Hatch (startup)]] — n8n later becomes the backbone of his "Anna" assistant pipelines (see the sibling chat *Fixing n8n Calendar Date Drift in HW Buddy Anna Assistant*), so this conversation captures him at the learning-the-primitives stage.

## What he was doing
- Asked for a concise, link-heavy explainer of n8n and of **Node.js** (V8 runtime, single-threaded event loop + non-blocking I/O via libuv, CommonJS vs ES modules, npm/nvm). The model gave him the "8 things to know" mental model: workflows/nodes, items as an array of `{json: {...}}`, expressions (`{{$json.name}}`, `$now()`), built-ins, the optional Code node (JS + Python via Pyodide), credentials, error handling via an Error Trigger workflow, and the quickstart.
- Then asked, explicitly "like I know nothing," for a no-code plan to build an **AI Gmail automation** that reads, summarizes, and sends email. The recipe: Gmail Trigger (OAuth) -> Gmail "Get All" -> Set node to trim fields -> optional OpenAI node to summarize/draft -> Gmail Send Email -> optional Error Trigger and Schedule Trigger. This is the same trigger-transform-AI-send shape his HW Buddy assistant later runs on.
- Finished the automation thread by requesting curated getting-started resources (official quickstart, Level 1 text course, learning path, blog/Medium walkthroughs, YouTube).

## What it shows
Consistent with his [[Intellectual Interests]] and self-taught builder streak from [[Coding Club]], he learns infrastructure by demanding the minimal mental model plus authoritative links rather than hand-holding. The "no prior coding experience" framing here is notable given that elsewhere he is deploying Flask apps and training models — he treats n8n as a glue/no-code layer to ship product features fast for his startup rather than a coding exercise.

## Tangent
The session ends on unrelated trivia: typical hours/tenure of an undercover narcotics officer in Texas, then how "abnormal" Rust Cohle's four-year deep-cover stint in *True Detective* Season 1 was by real-world standards. A throwaway curiosity detour with no bearing on his coursework or projects, in line with his habit of pivoting a working chat into pop-culture/[[Film and TV]] questions.
