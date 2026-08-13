---
type: entity
created: 2026-07-19
updated: 2026-08-12
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
  "[[RESOLVE Daily Activity 2026-08-12]]"
]
status: active
---

# RESOLVE (AI Assistant)

An **AI-powered personal assistant system** serving [[Traveler Stansberry]], handling calendar/task/email management, scheduling, research, and brief generation. Integrations include Outlook (calendar + email), Notion (task management), Telegram (communication), Apple Health (via Watch), vault search, and web research. Gmail is currently failing with permissions error (since 2026-06-30).

## Core Capabilities

### Established
- **Morning briefings**: Daily summary of next 2 days' calendar, open Notion tasks, recent email, and health data (sleep/resting HR). Timezone-aware and warm-toned. Example from 2026-08-11: flagged haircut appointment (8:00 AM deadline) and two high-priority UVA tasks with runway (advisor call due Aug 28, SIS credit confirmation due Sep 1).
- **Calendar integration**: Real-time access to upcoming events; event creation with optional clarification. Post-travel (return from Dublin, 2026-08-11), calendar remains exceptionally clear — only routine commitments scheduled. As of 2026-08-12, next 48 hours are completely blank (no events Aug 12–13).
- **Email triage**: Scans unread email (limit 50 messages, last 2 days) to identify actionable calendar items (invitations, RSVPs, appointments, reservations, deliveries). Daily inbox-to-calendar sweep compares email against 30-day calendar lookout. Since mid-July, sweep consistently surfaces only promotional noise (Twitch alerts, newsletters, marketing); no real events missed in last 4 weeks.
- **Notion task visibility**: Reads open tasks with high/medium/low priority flags; reports on tasks with explicit deadlines (e.g., UVA advising deadlines Aug 28 and Sep 1–4).
- **Health data integration**: Apple Watch check (sleep, resting heart rate) included in morning brief when available.
- **Web research**: Can search external sources (e.g., weather, upcoming events) as needed.

### System Health (as of 2026-08-12)
- **All connectors operational**: No errors during Aug 11–12 operations.
- **Email accumulation**: ~28,359 unread messages (typical due to promotional subscriptions). Last 2 days produced zero actionable signals.
- **Graceful error handling**: Now configured to skip connector errors rather than halt the entire brief (Aug 12 update).

### Known Issues
- **Gmail integration broken** since 2026-06-30 (OAuth/permissions issue); Outlook is the primary email system.

## Operational Patterns

**Morning rhythm:** Brief arrives early (pre-8 AM typical), summarizes next 48h, flags urgent deadlines.

**Daily inbox sweep:** Routine post-brief, focuses on real-world events vs. noise. Over the past 4 weeks, sweep accuracy is high — consistently identifies actual calendar needs while filtering promotional clutter.

**Pre-event reminders:** When calendar contains critical events (haircut, travel, meetings), system flags them in the brief 48h+ ahead.

**Move-in countdown:** As of 2026-08-12, system is tracking UVA move-in (Aug 20, 8 days away) and has flagged "pack mountain house gear" as an undated task that needs attention before move-out.

## Design Philosophy

- **Brevity + warmth**: Briefs are short, conversational, and human-readable; designed to be read in 2–3 minutes.
- **Signal over noise**: System explicitly filters promotional email and low-value notifications; only surfaces items requiring Traveler's decision or action.
- **Proactive**: Flags upcoming deadlines and time-sensitive tasks before they become urgent.
- **Reliable**: Operates on a routine cadence (daily morning + sweep); when a component fails, falls back gracefully rather than breaking.

## Related Pages
- [[Traveler Stansberry]] — primary user
- [[Homework Hatch (startup)]] — another AI automation project
- [[Personal Quant Model]] — system that may integrate with RESOLVE in future
- [[Self-Discipline and Goals]] — 75 Hard and goal-setting context
- [[College Search]] — UVA move-in and transition tracking
