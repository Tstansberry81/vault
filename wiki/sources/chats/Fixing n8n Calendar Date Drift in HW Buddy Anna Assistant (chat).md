---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2025-08-31
author: Traveler Stansberry
source_type: chat
tags: [chat, startup, automation, n8n]
status: active
---

# Fixing n8n Calendar Date Drift in HW Buddy Anna Assistant

A debugging session in which Traveler hands ChatGPT (GPT-5) the exported JSON of an [[Homework Hatch (startup)|HW Buddy]] [n8n](https://n8n.io) workflow and asks it to diagnose why created Google Calendar events keep being dated to **2023** instead of the current year. This is the same Telegram voice-and-text assistant stack documented in his other automation chats — the agent personas **"Anna"** (calendar) and **"Wade"** (email) routed by a "Router Bot" — building directly on the work in [[n8n Telegram Voice Assistant for HW Buddy - Calendar Automation (chat)]] and [[n8n Command Router for Homework Hatch - Telegram, Calendar, Instagram (chat)]].

## The bug, diagnosed
ChatGPT identified three faults:
- **Key mismatch.** Anna's system message promises to call the Google Calendar tool with keys `eventName`, `startISO`, `endISO`, `location`, `description`, but the calendar node was pulling capitalized `$fromAI('Start')`, `$fromAI('End')`, `$fromAI('Summary')`. The undefined dates made the LLM "helpfully" hallucinate a default year (2023).
- **No absolute "today."** Anna's prompt gave a timezone offset (`$moment().format('Z')`) but never an absolute date, so "this Friday at 3" anchored to a stale prior year.
- **Brittle success/fail router.** The `If2` node used an `empty` operator on a malformed `=={{ … }}` left value compared against a literal calendar URL — never logically gating success vs. failure, producing lying status messages.

## The fixes
- Remap the calendar node expressions to the exact lowercase keys Anna emits (`$fromAI('startISO', …)`, etc.).
- Inject an explicit `TODAY: {{ $moment().format('YYYY-MM-DD') }}` block plus "assume current year if omitted" into Anna's system message.
- Optional Code node to normalize the year unless the user explicitly typed one, using a `/\b20\d{2}\b/` regex on the original message.
- Anchor "now" to the Telegram message timestamp via `$moment.unix(...message.date)`.
- Fix `If2` to gate on `notEmpty($('Detect Anna Result').first().json.htmlLink)`.

Across follow-ups, Traveler insists firmly — "dont change anything drastically and dont recreate anything... just edit the parameters" — and ultimately asks ChatGPT to edit the entire `.json` and return a downloadable fixed file, which it does.

## What it shows
A snapshot of Traveler operating as a no-code/low-code builder for his startup's internal tooling: he treats ChatGPT as a pair-debugger handed a raw workflow export, and shows real product discipline — minimal-diff editing, refusing rebuilds, demanding both voice and text paths keep working. It reinforces the picture of [[Homework Hatch (startup)]] as a genuinely engineered system and of [[Traveler Stansberry]]'s hands-on, iterative approach to [[Coding Club|automation tooling]]. The "LLM invents a wrong year when given no anchor" lesson is a small but real piece of prompt-engineering knowledge.
