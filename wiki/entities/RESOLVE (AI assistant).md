---
type: entity
created: 2026-08-30
updated: 2026-09-01
tags: [systems, automation, ai, resolve, personal-ops]
status: active
sources: [
  "[[RESOLVE Daily Activity 2026-07-20]]",
  "[[RESOLVE Daily Activity 2026-07-24]]",
  "[[RESOLVE Daily Activity 2026-08-01]]",
  "[[RESOLVE Daily Activity 2026-08-20]]",
  "[[RESOLVE Daily Activity 2026-08-28]]",
  "[[RESOLVE Daily Activity 2026-08-29]]",
  "[[RESOLVE Daily Activity 2026-08-30]]",
  "[[RESOLVE Daily Activity 2026-09-01]]"
]
---

# RESOLVE: Personal Operating System

**RESOLVE** is [[Traveler Stansberry]]'s autonomous personal AI assistant and operating system (2026 onward). It operates as a **structured task automation layer** managing calendar, email, task tracking, and decision support via a series of well-defined daily and weekly commands.

## Overview

RESOLVE is **not a chatbot**; it's a **procedural agent** executing a repeating command suite designed to:
1. Extract real-world signals from disconnected sources (calendar, email, Notion, finance APIs)
2. **Cross-check for coherence** (email mentions an event → does it match the calendar?)
3. Synthesize brief summaries and recommendations
4. Log all activity for persistent records and future reference

> [!note] Operational philosophy
> RESOLVE embodies [[Self-Discipline and Goals]] — automating the "boring but critical" parts of calendar/email/task management so Traveler can focus on actual work. It's a **productivity buffer** between raw chaos and the intellectual work.

## Command Suite

### Daily Commands

**1. Morning Brief** (runs at start of day)
- **Inputs:** Next 2-day calendar, `get_school_day()` (today's classes/coursework), Notion open tasks, unread email
- **Error handling:** Skip connectors that fail; don't abort
- **Output:** Warm, concise summary with highlights and urgencies
- **Typical content:** Classes with times, due coursework, calendar events, important emails
- **Example (2026-09-01):** Three classes (EGMT 1540, MATH 1310, PHIL 1730), **urgent Aristotle reading** (Nicomachean Ethics I–III.4) due for PHIL 1730 at 15:30

**2. Daily Inbox-to-Calendar Sweep** (mid-morning or as needed)
- **Inputs:** Last 48 hours of email (`get_inbox_recent` limit 50), next 30 days of calendar (`get_calendar`)
- **Task:** Filter emails for real-world events (invites, RSVPs, deadlines, travel, appointments) vs. noise (newsletters, marketing, contests)
- **Output:** List of calendar-worthy events to add; summary of noise/signal ratio
- **Example (2026-09-01):** 9 readable messages; 0 calendar-worthy events; all noise (newsletters, promos, Twitch notifications)

### Weekly/Periodic Commands
- **Weekly digest** — consolidated view of the week's commitments
- **Finance check** (as needed) — portfolio status, trading activity
- **System health** — connector status, error logs, performance

## System Integration

- **Connectors:** Gmail, Outlook email, Outlook calendar, Notion, Telegram, finance APIs
- **Data flow:** Extractive (reads from sources) and synthetic (produces digests, not stored actions)
- **Failure mode:** Graceful — skip erroring connectors, don't abort the whole run
- **Log persistence:** All activity logged to [[wiki/log]] for historical reference

## Operational Pattern (Aug–Sep 2026)

- **Frequency:** Daily morning brief + inbox-to-calendar sweep (and periodic runs)
- **Task load:** Typical pattern: 2–4 commands per run, ~5–10 min per session
- **System health:** Reliable; occasional connector hiccups (Gmail had a permissions issue in July)
- **Usage trajectory:** Started 2026-07-12; now in routine steady state (daily use at UVA, F26)

> [!note] Week 1 @ UVA (Aug 26–Sep 1, 2026)
> RESOLVE transitioned from summer mode to **semester mode** with the start of classes. Inbox is light (mostly promotional); calendar is steadily filling with coursework deadlines. The system is managing class load, reading assignments, and potential finance/quant work alongside normal ops.

---

## Related

[[Traveler Stansberry]] · [[Self-Discipline and Goals]] · [[UVA and the Quant Question]]