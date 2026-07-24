---
type: entity
created: 2026-07-19
updated: 2026-07-23
tags: [technology, personal, automation, ai]
sources: ["[[RESOLVE Daily Ingest 2026-07-14]]", "[[RESOLVE Daily Ingest 2026-07-17]]", "[[RESOLVE Daily Ingest 2026-07-18]]", "[[RESOLVE Daily Ingest 2026-07-19]]", "[[RESOLVE Daily Activity 2026-07-20]]", "[[RESOLVE Daily Activity 2026-07-21]]", "[[RESOLVE Daily Ingest 2026-07-22]]", "[[RESOLVE Daily Activity 2026-07-23]]"]
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
- **Financial tracking**: Monitors checking account, savings, and monthly budget spend vs. limit (e.g., $1,261 of $1,500 as of 2026-07-22)
- **Graceful failure**: Skips connector errors rather than stopping the pipeline (e.g., Gmail down since 2026-06-30)
- **Quick commands**: Execute simple tasks (send email, open browser) with minimal context
- **Vault logging**: Records activity and findings to [[wiki/log.md]] for audit and retrospection

### Emerging (as of 2026-07-20)
- **Vault research & writing**: Web search + multi-paragraph vault page generation (tested 2026-07-20, confirmed working 2026-07-21)

## Operational Patterns

### Daily Workflow
RESOLVE runs a predictable **morning + sweep** cycle:
1. **Morning brief** (typically ~8am): Calendar peek, task scan, email summary, health update
2. **Inbox-to-calendar sweep** (after morning brief): 50-message scan, event-relevance filter, calendar cross-check

As of 2026-07-23, both routines execute cleanly with **graceful error handling** — failed connectors (e.g., Gmail) don't block the full run.

### System Status (as of 2026-07-23)
- **Healthy:** Outlook (email + calendar), Notion, Telegram, Vault, Apple Health
- **Degraded:** Gmail (permissions error, unresolved since 2026-06-30)
- **Event load:** Typical (low volume of inbox noise; known future events pre-calendared)

## Technical Foundation
- Built on [[Cursor (AI code editor)]] (Aider-based AI pair programming)
- Integrations managed via [[n8n (automation platform)]]
- Persistent state in Notion + Outlook + Apple Health APIs
- Logging to vault ensures every agent action is auditable

## Next Frontiers
- Gmail reconnection / permissions repair (blocking since 2026-06-30)
- Automated analysis of email patterns (read-only; aggregate trends)
- Research pipeline maturation (web search + vault page gen now confirmed working)

## Related Pages
- [[Traveler Stansberry]] — principal
- [[Homework Hatch (startup)]] — sibling project (edtech, distinct from RESOLVE)
- [[Personal Quant Model]] — financial tracking system (feeds into RESOLVE budget awareness)
