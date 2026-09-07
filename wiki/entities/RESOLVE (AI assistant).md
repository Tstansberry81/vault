---
type: entity
created: 2026-08-30
updated: 2026-09-06
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
  "[[RESOLVE Daily Activity 2026-09-01]]",
  "[[RESOLVE Daily Activity 2026-09-02]]",
  "[[RESOLVE Daily Activity 2026-09-03]]",
  "[[RESOLVE Daily Activity 2026-09-04]]",
  "[[RESOLVE Daily Activity 2026-09-05]]",
  "[[RESOLVE Daily Activity 2026-09-06]]"
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
- **Inputs:** Next 2-day calendar, `get_school_day()` (today's classes/coursework), Notion open tasks, unread email (graceful error-handling: skip errors instead of stopping)
- **Output:** Warm, short brief with highlights and urgent items. If lectures exist, leads with CLASS TODAY section (time/location from calendar). Flags due work, meetings, calendar anomalies.
- **Example:** [[RESOLVE Daily Activity 2026-09-06|Sep 6 brief]] — day confirmed clear, zero events, flagged PHIL reading due Tue 9/8

**2. Daily Inbox-to-Calendar Sweep** (runs during morning or early afternoon)
- **Inputs:** Recent email (50 messages, 2-day window), 30-day calendar look-ahead, task list
- **Output:** Identifies calendar-worthy events (invitations, RSVPs, appointments, flights, travel, deadlines, deliveries) and either injects them into calendar or flags for action
- **Calibration:** Gracefully skips emails with parsing errors; refuses to invent events from empty-bodied emails (e.g., Allianz email with no body text); surfaces **only real, confirmed happenings**
- **Example:** [[RESOLVE Daily Activity 2026-09-04|Sep 4 sweep]] — API overload forced partial run; [[RESOLVE Daily Activity 2026-09-06|Sep 6 sweep]] — zero events (correct; week was clear)

**3. Weekly Review** (Friday end-of-week or weekend)
- **Inputs:** `get_recent_activity` (7-day ledger: commands, outcomes, decisions, failures), `get_finance` (7-day spend), `get_calendar` (week ahead), task list
- **Output:** Honest synthesis — what got done, decisions made, what failed/stalled (named plainly), money in/out, week ahead
- **Tone:** Unsparing. Not cheerleading; flagging gaps and delivery risks plainly (e.g., "PHIL reading has been deferred two weekends in a row; it's now one weekday away from deadline with reading incomplete").
- **Example:** [[RESOLVE Daily Activity 2026-09-06|Sep 6 weekly review]]

### Error Handling

- **Graceful degradation:** If a connector (email, calendar, Notion, finance) returns an error, RESOLVE logs it clearly and continues with available data rather than failing the entire command
- **Allianz email judgment (Sep 4–6):** Tracked an empty-bodied email for 4 days; RESOLVE refused to invent a trip without explicit confirmation text. This decision stands; it reflects disciplined skepticism about incomplete data.
- **API overload (Sep 4):** Morning brief 529 error; inbox sweep completed successfully despite upstream failure. No cascade.

## Operational Status (Early September 2026)

- **Timeline:** Operational logs begin 2026-07-12; daily logs available for Sep 1–6
- **Pattern:** Morning brief + inbox sweep + weekly review form the core rhythm
- **System health:** Nominal post-API-failure (Sep 4 outage did not cascade; Sep 5–6 runs clean)
- **Known issue:** Gmail connector down since 2026-06-30 (permissions error; flagged for reconnect)
- **Current focus:** Traveler's Fall 2026 UVA semester; class-to-task/calendar/deadline coherence

## Future Extensions

Potential command additions (not yet implemented):
- **Finance dashboard** — track spending vs. budget over time
- **Task-to-calendar injection** — map Notion tasks with deadlines directly to calendar
- **Email priority classification** — distinguish signal (actionable) from noise (promotional, FYI)
- **Weekly metrics dashboard** — productivity/focus tracking over weeks

## Links

- **Daily activity logs:** [[RESOLVE Daily Activity 2026-09-06]] (latest), [[RESOLVE Daily Activity 2026-09-05]], [[RESOLVE Daily Activity 2026-09-04]], etc. (see sources above)
- **Philosophy:** [[Self-Discipline and Goals]]
- **Context:** [[UVA and the Quant Question]] — current coursework; [[Homework Hatch (startup)]] — related automation project