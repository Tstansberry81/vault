---
type: entity
created: 2026-07-19
updated: 2026-08-18
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
  "[[RESOLVE Daily Activity 2026-08-18]]"
]
status: active
---

# RESOLVE (AI Assistant)

An **AI-powered personal assistant system** serving [[Traveler Stansberry]], handling calendar/task/email management, scheduling, research, and brief generation. Integrations include Outlook (calendar + email), Notion (task management), Telegram (communication), Apple Health (via Watch), vault search, and web research. **Gmail has been offline since 2026-06-30** (permissions error; awaits reconnection).

## Core Capabilities

### Established and Daily
- **Morning briefings**: Daily summary of next 2 days' calendar, open Notion tasks, recent unread email, and health data (sleep/resting HR from Apple Watch where available). Warm-toned, concise, timezone-aware.
- **Calendar integration**: Real-time access to upcoming events; creation of new events from email or manual instruction with optional attendee notification.
- **Inbox-to-calendar sweeps**: Scan recent email for real-world happenings (invitations, RSVPs, appointments, meetings, deadlines, travel, deliveries) and create calendar entries for events requiring Traveler's action or attention.
- **Task synthesis**: Querying Notion for open tasks and surfacing urgent/overdue items in morning briefs.
- **Health briefing**: Integration with Apple Watch data (sleep duration, resting heart rate, recovery) when available.

### Advanced / Experimental
- **Connector diagnostics**: Testing and reporting on the health of integrated services (Outlook, Notion, Gmail, Telegram, Apple Health).
- **Graceful degradation**: Morning briefs and sweeps skip broken connectors (e.g., Gmail) rather than halt, ensuring partial data is still useful.

## Integration Status

| Connector | Status | Last Working |
|-----------|--------|--------------|
| **Outlook (calendar + email)** | ✅ Active | Current |
| **Notion (tasks)** | ✅ Active | Current |
| **Telegram** | ✅ Active | Current |
| **Apple Health (Watch)** | ✅ Active | Current |
| **Gmail** | ❌ Offline | 2026-06-30 (permissions error; awaits user reconnection) |

## Operational Patterns (Jul–Aug 2026)

**Frequency:** Daily at ~8 AM, with ad-hoc scheduling tasks on demand (e.g., dinner with [[Naomi]]).

**Modal activity (routine):**
- Morning brief: 5–10 min summary of day + open tasks
- Inbox-to-calendar: 1–2 messages/week requiring event creation; most email is marketing/notifications (no action)
- Calendar: average 1–2 events/day during high season; dropped to 0 in late July (post-graduation, pre-move-in)

**Recent pattern (late August 2026):** The calendar has emptied as [[College Search|move-in day]] (August 20) approaches. Days are now open blocks (packing, final prep). The critical path shifted to **pre-arrival administrative tasks** with firm deadlines ([[College Search#🚨 Outstanding Pre-Arrival Tasks|see College Search]]): advisor confirmation (Aug 28) and SIS/credit validation (Sep 4).

## Vault Integration

RESOLVE can search the wiki and reference back to [[Traveler Stansberry]] when composing briefs. The morning brief vaults itself (via `vault_append_log`) under the title "Morning brief" with today's date. This archive becomes a time-series record of Traveler's calendar and task state.

---

**Related:** [[College Search]] · [[Self-Discipline and Goals]] · [[Homework Hatch (startup)]]