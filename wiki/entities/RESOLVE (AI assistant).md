---
type: entity
created: 2026-07-19
updated: 2026-08-17
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
  "[[RESOLVE Daily Activity 2026-08-17]]"
]
status: active
---

# RESOLVE (AI Assistant)

An **AI-powered personal assistant system** serving [[Traveler Stansberry]], handling calendar/task/email management, scheduling, research, and brief generation. Integrations include Outlook (calendar + email), Notion (task management), Telegram (communication), Apple Health (via Watch), vault search, and web research. **Gmail has been offline since 2026-06-30** (permissions error; awaits reconnection).

## Core Capabilities

### Established and Daily
- **Morning briefings**: Daily summary of next 2 days' calendar, open Notion tasks, recent unread email, and health data (sleep/resting HR from Apple Watch where available). Warm-toned, concise, timezone-aware.
- **Calendar integration**: Real-time access to upcoming events; creation of new events from email or manual instruction with optional clarification.
- **Inbox-to-calendar sweep**: Scan 50 recent emails over the past 2 days for real-world events (invitations, RSVPs, appointments, meetings, deadlines, travel, reservations, tickets) and compare against 30-day calendar view. Create calendar blocks only for concrete, actionable date/time commitments; skip newsletters, notifications, and cold contact attempts.
- **Health snapshot**: One-line recovery metric from Apple Watch (sleep quality, resting heart rate) when fresh data available.
- **Weekly review synthesis** (Sundays): Summary of the week's calendar, task completion, and notable patterns.

### Operational Patterns (as of Aug 2026)

- **Daily activation**: Morning (briefing + health check) + noon/afternoon (inbox sweep if new mail).
- **Error handling**: Gracefully skip any connector that fails (Gmail down, Notion temporarily unavailable) rather than stopping the pipeline. Log the skip; all other connectors remain active.
- **Calendar discipline**: No entry created for marketing emails, newsletters, streaming alerts, or cold social-media requests — only concrete events with real-world attendees, times, and commitments.
- **Notion-centric task tracking**: All open/priority tasks live in Notion; briefing displays them without filtering.

### Calibration & Constraints

RESOLVE is **operational but not autonomous at the system level**. Commands from Traveler explicitly trigger operations (morning brief, sweep, weekly review); no unsolicited interventions or predictive actions. All calendar creations are either: (a) explicit instruction from Traveler, (b) parsed from an inbound email/invite with high confidence, or (c) offered as a suggestion for approval.

**Known gaps:**
- Gmail offline (reconnect blocked by permission state).
- Notion connector intermittently unavailable (no architectural root cause documented yet).
- No predictive task generation or automated deadline escalation yet (possible future).

### Recent Operational Notes (Aug 2026)

- System has been healthy and stable through mid-August.
- All morning briefings completing within the expected window.
- Inbox-to-calendar accuracy remains high; no false positives on event creation over the past 30 days.
- Move-in logistics (Aug 20) have been tracked but no major calendar conflicts emerged.

See individual daily activity logs (linked in `sources:`) for granular diagnostics and task snapshots.

