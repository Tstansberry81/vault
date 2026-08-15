---
type: entity
created: 2026-07-19
updated: 2026-08-14
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
  "[[RESOLVE Daily Activity 2026-08-14]]"
]
status: active
---

# RESOLVE (AI Assistant)

An **AI-powered personal assistant system** serving [[Traveler Stansberry]], handling calendar/task/email management, scheduling, research, and brief generation. Integrations include Outlook (calendar + email), Notion (task management), Telegram (communication), Apple Health (via Watch), vault search, and web research. Gmail is currently failing with permissions error (since 2026-06-30).

## Core Capabilities

### Established
- **Morning briefings**: Daily summary of next 2 days' calendar, open Notion tasks, recent email, and health data (sleep/resting HR). Timezone-aware and warm-toned. 
- **Calendar integration**: Real-time access to upcoming events; event creation with optional clarification. Gracefully falls back when connectors error (skips them rather than halting the session).
- **Inbox-to-calendar sweep**: Identifies real-world events from unread email (appointments, invitations, RSVPs, travel, deadlines) and creates calendar events for those that require action; filters marketing noise and ignores notifications. Scans last 2 days of email, cross-checks against next 30 days of calendar. Only creates events for happenings Traveler must know about or act on.
- **Task visibility**: Pulls open Notion tasks into morning brief; supports filtering by deadline or project.
- **Health integration**: Apple Watch data (sleep duration, resting heart rate) when fresh, integrated into brief.
- **Warm, human tone**: Briefs are not bulletpoints; they're conversational, with personality.
- **Graceful error handling**: When a connector (Gmail, Notion) errors, skips it rather than failing the whole command. Logs the issue.
- **Calendar error correction**: When RESOLVE makes a scheduling mistake (e.g., misinterpreting "tomorrow" as today), it catches and corrects it mid-session and alerts the user to fix stale calendar entries.

### Operational Patterns
- **Daily run**: Morning brief (usually ~7 AM), then inbox-to-calendar sweep (often 8–10 AM), then a general task/brief request if needed.
- **No unsolicited actions**: Does not create tasks, move emails, delete messages, or modify Notion without explicit request. Acts only on clear commands.
- **Security-conscious**: Monitors inbound emails for injection attempts (e.g., an email trying to trick RESOLVE into scheduling something). Reports suspicious patterns.
- **Real vs. noise**: Distinguishes real events (invitations, reservations, deadlines) from marketing (promos, newsletters, "is live" pings). Does not clutter calendar with promotional offers.

## Known Issues

- **Gmail connector down since 2026-06-30**: Permissions error ("requires additional permissions — reconnect"). Has not been restored; inbox-to-calendar sweep currently covers Outlook only.
- **Notion connector intermittent**: Occasionally unavailable in a session; morning brief skips it and continues rather than halting.

## History of Activity

See daily activity logs starting [[RESOLVE Daily Activity 2026-07-14]] through [[RESOLVE Daily Activity 2026-08-14]]. Operational volume typically 1–3 commands per day (morning brief + inbox sweep + occasional research/task requests). System has been healthy and reliable since inception (2026-07-14).

## Recent Patterns (last week of Aug)

- **Aug 11–13**: Light activity; routine morning briefs and inbox sweeps; calendar quiet.
- **Aug 14**: Morning brief and inbox-to-calendar sweep. Inbound email was 100% marketing/notifications (0 real events). Corrected a med check scheduling error (had placed it on Aug 14 instead of Aug 15).

## Next Generation Opportunities

(Deferred; to be addressed as Traveler's use matures.)

- Deeper research integration (background reading on meeting topics, context from past emails).
- Automated meeting prep (agenda, attendee notes, prior interactions).
- Proactive pattern detection (e.g., "you have back-to-back meetings; clear a block?" or "this deadline is tighter than usual").
- Integration with [[Homework Hatch (startup)]] or [[Personal Quant Model]] for domain-specific briefings.

---

**Links:** [[Traveler Stansberry]] · [[Cursor (AI code editor)]] · [[n8n (automation platform)]]