---
type: entity
created: 2026-07-19
updated: 2026-07-21
tags: [technology, personal, automation, ai]
sources: ["[[RESOLVE Daily Ingest 2026-07-14]]", "[[RESOLVE Daily Ingest 2026-07-17]]", "[[RESOLVE Daily Ingest 2026-07-18]]", "[[RESOLVE Daily Ingest 2026-07-19]]", "[[RESOLVE Daily Activity 2026-07-20]]", "[[RESOLVE Daily Activity 2026-07-21]]"]
status: active
---

# RESOLVE (AI Assistant)

An **AI-powered personal assistant system** serving [[Traveler Stansberry]], handling calendar/task/email management, scheduling, research, and brief generation. Integrations include Outlook (calendar + email), Notion (task management), Telegram (communication), Apple Health (via Watch), vault search, and web research. Gmail is currently failing with permissions error (since 2026-06-30).

## Core Capabilities

### Established
- **Morning briefings**: Daily summary of next 2 days' calendar, open Notion tasks, recent email, and health data (sleep/resting HR)
- **Calendar integration**: Real-time access to upcoming events; event creation with optional clarification
- **Email triage**: Scans unread email (last 2–50 messages), flags urgent items, aggregates promotional noise
- **Task polling**: Reports open Notion tasks with priority assessment
- **Inbox-to-calendar sweep**: Cross-checks emails for hidden deadlines, RSVPs, invitations; compares with calendar to surface conflicts
- **Graceful failure**: Skips connector errors rather than stopping the pipeline (e.g., Gmail down since 2026-06-30)
- **Quick commands**: Execute simple tasks (send email, open browser) with minimal context

### Emerging (as of 2026-07-20)
- **Vault research & writing**: Web search + multi-paragraph vault page generation
  - Successfully completed: UVA Rotunda history, Student Health & Wellness Center, College pathway (Arts & Sciences → McIntire), guitar capo/barre chord synthesis
  - Writes structured `wiki/` pages with metadata; integrates with vault backlink graph
- **Reminders**: Create calendar-based reminder events (e.g., "Call mom")

## Operational Pattern (as of 2026-07-21)

**Daily routine:**
1. **Morning brief** — calendar, tasks, email, health snapshot; logged to vault with timestamp
2. **Inbox-to-calendar sweep** — check last 2 days of email for real-world events (invites, RSVPs, deadlines, travel); cross-check calendar; surface any mismatches
3. **Quick task execution** — process ad-hoc commands (send email, open site, etc.)

**Status assessment (2026-07-21):**
- System healthy; all connectors functional except Gmail (graceful skip)
- Inbox well-managed: incoming mail is primarily noise (newsletters, promos, streaming notifications)
- Calendar clean and current for next 30 days (UVA grad party, Dublin flights, personal appointments already entered)
- Low ambient event load — consistent with summer transition period (post-high-school, pre-college)

## Known Limitations

> [!warning] Gmail connector down
> Outlook remains primary email source; Gmail requires reconnect (permissions issue, unresolved since 2026-06-30)

## Related
- [[Traveler Stansberry]] (user)
- [[Homework Hatch (startup)]] (systems/automation adjacent)
- [[Self-Discipline and Goals]] (context: personal optimization)