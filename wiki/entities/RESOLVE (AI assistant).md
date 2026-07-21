---
type: entity
created: 2026-07-19
updated: 2026-07-20
tags: [technology, personal, automation, ai]
sources: [["[[RESOLVE Daily Ingest 2026-07-14]]", "[[RESOLVE Daily Ingest 2026-07-17]]", "[[RESOLVE Daily Ingest 2026-07-18]]", "[[RESOLVE Daily Ingest 2026-07-19]]", "[[RESOLVE Daily Activity 2026-07-20]]"]]
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

### Emerging (as of 2026-07-20)
- **Vault research & writing**: Web search + multi-paragraph vault page generation
  - Successfully completed: UVA Rotunda history, Student Health & Wellness Center, College pathway (Arts & Sciences → McIntire), guitar capo/barre chord synthesis
  - Writes structured `wiki/` pages with metadata; integrates with vault backlink graph
- **Reminders**: Create calendar-based reminder events (e.g., "drink water", "get sweatshirt from Dom")
- **Diagnostic testing**: Read-only health checks on connectors, inbox state, vault search

## Observed Limitations & Gaps

### Active Blockers
- **🚨 Executor + Haiku model incompatibility** (2026-07-20): Web search tool calls failed due to model not supporting programmatic tool calling. Requires `allowed_callers=["direct"]` or compatible model. Traveler identified and is actively debugging.
- **Gmail connector down** (since 2026-06-30): Requires permissions reconnect; email coverage incomplete across some sessions
- **Data formatting flakiness**: Early inbox API calls returned empty FROM/SUBJECT fields (resolved by later runs, but indicates backend volatility)

### Capabilities Not Yet Observed
- Sophisticated email prioritization (can identify noise, but limited semantic ranking)
- Task deadline parsing from email bodies (would require NLP)
- Calendar conflict detection / meeting prep
- Expense tracking or financial reconciliation
- Detailed health analytics (currently just sleep/HR pull)

## Implementation Notes

- **Language model:** Primary agent uses a capable model (Claude, likely 3.5+); executors initially attempted Haiku 4.5 (too limited for tool calling; Traveler fixing)
- **Architecture:** Planner-executor pattern — agent queues tasks, background executors run research/writing jobs, results stream into vault or user feed
- **Iteration pace:** Fast debugging cycle — Traveler tests, identifies failure mode, fixes infrastructure, retries within same session
- **Vault integration:** Saves multi-paragraph research summaries directly to `wiki/sources/` or `wiki/entities/`; maintains frontmatter + `[[wikilinks]]` metadata

## Development Activity

2026-07-20 session logged **39 discrete commands/tasks**, mostly diagnostic and troubleshooting:
- 11 consecutive inbox read-only tests (identifying data formatting issues)
- Daily sweep of 50 emails
- Systems health check (Apple Watch, recent activity, vault search)
- 3 failed research executor attempts (blocker identified)
- 4 successful research tasks (after fix)
- Reminders and quick tasks (drink water, get sweatshirt)

This suggests **active development and testing cycle**, not just passive operation.

## Context & Future Direction

- Built in parallel with [[Homework Hatch (startup)|Homework Hatch]] (edtech/AI tutoring platform)
- GitHub repo: `Tstansberry81/resolve` (evidence: workflow failure notifications in inbox)
- Aligned with Traveler's [[Self-Discipline and Goals|"lock in" / automation aspirations]]
- **Intent:** Full web dashboard control panel (mentioned in [[agent-memory|agent memory]])
- **Use case urgency:** UVA orientation + college transition looming (fall 2026) — building infrastructure ahead of time

## Related Pages

- [[Traveler Stansberry]] — the user and builder
- [[Homework Hatch (startup)]] — parallel automation/edtech project
- [[UVA and the Quant Question]] — context (incoming student building personal OS)
- [[Autonomous Agent — Pipeline Spec]] — design documentation
- [[Autonomous Agent — Project Infrastructure]] — technical architecture

## Recent Ingests

- [[RESOLVE Daily Activity 2026-07-20]] — testing, research capabilities, executor blocker
- [[RESOLVE Daily Ingest 2026-07-19]] — morning brief, email sweep, reminder creation
- [[RESOLVE Daily Ingest 2026-07-18]] — full operation summary
- Catalog: [[_RESOLVE Daily Ingests]]
