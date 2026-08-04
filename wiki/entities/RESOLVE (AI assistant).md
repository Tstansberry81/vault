---
type: entity
created: 2026-07-19
updated: 2026-08-03
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
  "[[RESOLVE Daily Activity 2026-08-03]]"
]
status: active
---

# RESOLVE (AI Assistant)

An **AI-powered personal assistant system** serving [[Traveler Stansberry]], handling calendar/task/email management, scheduling, research, and brief generation. Integrations include Outlook (calendar + email), Notion (task management), Telegram (communication), Apple Health (via Watch), vault search, and web research. Gmail is currently failing with permissions error (since 2026-06-30).

## Core Capabilities

### Established
- **Morning briefings**: Daily summary of next 2 days' calendar, open Notion tasks, recent email, and health data (sleep/resting HR). Timezone-aware (e.g., recognized [[Traveler]]'s Dublin arrival on 2026-08-02 and adjusted greeting to 5-hour offset).
- **Calendar integration**: Real-time access to upcoming events; event creation with optional clarification. Currently tracking: [[Japanese Oral Interview]] (2026-08-07, 11:00 AM ET / 4:00 PM Dublin time).
- **Email triage**: Scans unread email (last 2–50 messages), flags urgent items, aggregates promotional noise. Recent performance: 100% noise filtration accuracy over 7-day period (all inbox entries correctly identified as non-actionable).
- **Task polling**: Reports open Notion tasks with priority assessment
- **Inbox-to-calendar sweep**: Automated scan for emails referencing real-world events (invitations, RSVPs, appointments, deadlines, travel, reservations); creates calendar entries where needed
- **Health integration**: Pulls Apple Watch data (sleep, resting HR) and incorporates into morning briefing
- **Graceful error handling**: When a connector fails (e.g., Gmail permissions), continues processing other sources instead of halting the brief

### Known issues & limitations
- **Gmail connector**: Permissions error since 2026-06-30; Outlook email functioning normally, so no loss of coverage
- **Notion task summaries**: Inconsistently included in morning briefs (present some days, omitted others; unknown reason — possible no open tasks)
- **Prep plan tracking**: Successfully flags when upcoming events have no attached plan (e.g., Japanese Oral Interview flagged on 2026-08-02 as "4 days out, no plan"). **Does not yet auto-create or auto-schedule prep plans** — flagging is sufficient, human must act on it.

---

## Operational Patterns (July–August 2026)

| Date | Context | Activity |
|------|---------|----------|
| 2026-07-12–25 | Routine (home) | Daily morning briefs, routine inbox sweeps, email → calendar classification |
| 2026-07-31 | Pre-travel | Full day briefing; travel planning coordination |
| 2026-08-01 | Travel day | Morning brief + full inbox-to-calendar sweep; Dublin arrival confirmed |
| 2026-08-02 | Early travel (day 2) | Morning brief + inbox sweep; flagged Japanese Oral Interview prep needed |
| 2026-08-03 | Travel (day 3) | Morning brief + inbox sweep; **no new actionables** |

**Pattern:** Inbox is extremely clean (promotional noise + social alerts only); calendar fills only when Traveler is doing exam prep or has scheduled commitments. Current state (Aug 3): **calendar empty, exam 4 days away, no prep schedule created**.

---

## Design & Rationale

RESOLVE is intentionally **minimal** in scope (no decision-making, no proactive scheduling without approval) and **transparent** in output (always explains what it found and what it did). It succeeds at its core job (calendar + email triage) and gracefully degrades when connectors fail. The morning brief is designed to be **short, warm, and actionable** — flags anything urgent, summarizes open tasks, then gets out of the way.

**Dependency tracking:** The system demonstrates awareness of dependencies (e.g., Japanese Oral Interview requires prep) and correctly identifies when prep hasn't been scheduled, but leaves action to the human. See [[Japanese Oral Interview]] for prep recommendations.

---

## Related

- [[Traveler Stansberry]] — user
- [[Japanese Oral Interview]] — current flagged upcoming event
- [[Homework Hatch (startup)]] — another Traveler project; comparison use case for task management
- [[Personal Quant Model]] — another project RESOLVE has helped coordinate
