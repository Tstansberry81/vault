---
type: entity
created: 2026-07-19
updated: 2026-08-23
tags: [technology, personal, automation, ai]
sources: [
  "[[RESOLVE Daily Ingest 2026-07-14]]",
  "[[RESOLVE Daily Ingest 2026-07-17]]",
  "[[RESOLVE Daily Ingest 2026-07-18]]",
  "[[RESOLVE Daily Ingest 2026-07-19]]",
  "[[RESOLVE Daily Activity 2026-07-20]]",
  "[[RESOLVE Daily Activity 2026-07-21]]",
  "[[RESOLVE Daily Ingest 2026-07-22]]",
  "[[RESOLVE Daily Activity 2026-07-23]]",
  "[[RESOLVE Daily Activity 2026-07-24]]",
  "[[RESOLVE Daily Activity 2026-07-25]]",
  "[[RESOLVE Daily Activity 2026-07-31]]",
  "[[RESOLVE Daily Activity 2026-08-01]]",
  "[[RESOLVE Daily Activity 2026-08-02]]",
  "[[RESOLVE Daily Activity 2026-08-03]]",
  "[[RESOLVE Daily Activity 2026-08-11]]",
  "[[RESOLVE Daily Activity 2026-08-12]]",
  "[[RESOLVE Daily Activity 2026-08-13]]",
  "[[RESOLVE Daily Activity 2026-08-14]]",
  "[[RESOLVE Daily Activity 2026-08-15]]",
  "[[RESOLVE Daily Activity 2026-08-16]]",
  "[[RESOLVE Daily Activity 2026-08-17]]",
  "[[RESOLVE Daily Activity 2026-08-18]]",
  "[[RESOLVE Daily Activity 2026-08-19]]",
  "[[RESOLVE Daily Activity 2026-08-20]]",
  "[[RESOLVE Daily Activity 2026-08-21]]",
  "[[RESOLVE Daily Activity 2026-08-22]]",
  "[[RESOLVE Daily Activity 2026-08-23]]"
]
status: active
---

# RESOLVE (AI Assistant)

An **AI-powered personal assistant system** serving [[Traveler Stansberry]], handling calendar/task/email management, scheduling, and brief generation. Integrations include Outlook (calendar + email), Notion (task management), Telegram (communication), Apple Health (via Watch), and vault search. **Gmail has been offline since 2026-06-30** (permissions error; awaits reconnection).

## Core Capabilities

### Established and Daily

1. **Morning briefing** — checks calendar (configurable window), Notion tasks, unread email; writes warm, actionable brief with highlights and urgent items. Skips connector errors gracefully.
2. **Inbox-to-calendar sweep** — extracts time-sensitive emails (invitations, RSVPs, appointments, deadlines, flights, deliveries) and cross-references with GCal; flags new events or conflicts.
3. **Calendar coordination** — can schedule social events (e.g., dinner with [[Naomi]]) by checking both parties' free time.
4. **Task/assignment harvesting** — pulls new assignments from email and files them into Notion databases (assignments, exams, lectures) with dates, readings, and context preserved.
5. **Brief generation** — synthesizes system state (activity, finance, calendar) into readable narratives with honest callouts of what's working and what stalled.

### Advanced Operations

- **Coursework infrastructure build:** Full course scheduling (ECON 2010, PHIL 1730 on 2026-08-23) — exams to GCal, lecture schedules, reading lists, all with proper tagging.
- **Notion database management:** Can create/populate databases, add rows with readings/dates, tag by unit. **Cannot modify view sorts** (API limitation) without a running local worker.
- **Weekly + monthly reviews:** Aggregates activity, finance (SimpleFIN), calendar, and stalled tasks into structured reviews.
- **Vault operations:** Can read from and append to the wiki; logs daily activity; propagates scheduling info.

## System Health & Status (as of 2026-08-23)

| Connector | Status | Notes |
|-----------|--------|-------|
| **Outlook (Calendar + Email)** | ✅ Healthy | Primary conduit for calendar/email. Working reliably. |
| **Notion** | ⚠️ Partial | API write access works (create databases, add rows). View sort changes blocked (API limitation); require local worker. |
| **Telegram** | ✅ Healthy | Communication channel; working. |
| **Apple Health** | ✅ Limited | Watch data pulls when available; used for recovery metrics in briefs. |
| **Gmail** | ❌ Offline | Offline since 2026-06-30 due to permissions error. Awaits reconnection. |
| **Local worker** | ⚠️ Offline | Was online during early week; offline by 2026-08-23. Needed for in-browser Notion edits (view sorts). Restart: `launchctl kickstart -k gui/$(id -u)/com.resolve.localworker`. |

## Known Gaps & Calibrations

> [!warning] Operational constraints
> - **Gmail:** Offline for ~2 months (since 2026-06-30). Non-blocking but reduces email coverage; Outlook is the primary path.
> - **Notion API limits:** Cannot change view sorts programmatically; requires browser + local worker. As of 2026-08-23, local worker is offline and awaiting restart signal from Traveler.
> - **Second-half course schedules:** ECON 2010 has full first half (8 lectures Aug–Sep), but second half (9/28 onward) only partially transcribed in recent logs; should be cross-checked against syllabus/Notion DB.
> - **Four stalled tasks:** Mentioned in [[weekly-review-2026-08-23.md]] but not detailed in activity logs; worth reviewing in context of next week's priorities.

## Operational Pattern (Jul–Aug 2026)

RESOLVE has evolved from **raw ingest of daily schedules** (mid-July) to **intelligent course infrastructure** (late August). The system now:

- Handles routine briefing + triage with high reliability.
- Builds complex scheduling infrastructure (exams, lectures, readings) without human data-entry.
- Gracefully skips connector errors instead of halting.
- Generates structured weekly/monthly reviews with honest assessment of progress and stalled work.
- Maintains backlinks between systems (GCal ↔ Notion ↔ vault).

**Peak activity:** Late August 2026, as Traveler moved from orientation → residence → semester start. School scheduling (ECON, PHIL) took priority.

## Related Pages
- [[Traveler Stansberry]] — the user
- [[UVA and the Quant Question]] — the broader context (Traveler's UVA commitment)
- [[ECON 2010 (Principles of Microeconomics, UVA Fall 2026)]] — recent course scheduled
- [[Moral and Political Philosophy (UVA Fall 2026)]] — concurrent course
- [[weekly-review-2026-08-23.md]] — latest review; full week context
