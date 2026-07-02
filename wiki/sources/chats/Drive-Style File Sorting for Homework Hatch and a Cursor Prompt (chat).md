---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2025-10-04
author: Traveler Stansberry
source_type: chat
tags: [chat, coding, homework-hatch, google-drive]
status: active
---

# Drive-Style File Sorting for Homework Hatch and a Cursor Prompt

A short, tightly-scoped engineering chat in which Traveler asks for a sorting algorithm that mirrors the Google Drive UI ("folders first, natural name sort, multiple sort modes") so his startup [[Homework Hatch (startup)]] can render an integrated Drive file/folder browser correctly. He was wiring Google Drive into the app and the files/folders were sorting wrong. This connects to his broader effort to mirror a Drive folder tree inside the product (see other chats on Drive folder mirroring and LMS ingestion) — the app pulls in students' cloud files, so a correct, predictable file browser is table stakes.

## What the assistant delivered
A "drop-in" comparator spec implemented in **both TypeScript (frontend) and Python (backend)** for end-to-end consistency:
- **Sort modes:** Name (A→Z / Z→A), Last modified, Last modified by me, Last opened by me, Size.
- **Natural, case-insensitive name ordering** so "File 2" sorts before "File 10" — using `localeCompare(a, b, undefined, { numeric: true, sensitivity: 'base' })` on the frontend (and `natsort` suggested for true backend parity).
- **Item-kind grouping:** folders before files (optional toggle), with **shortcuts treated as their target kind** (`application/vnd.google-apps.shortcut` resolving via `shortcutDetails.targetMimeType`).
- Deterministic tie-breakers (name asc, then `id`), trashed items pushed last, optional starred-first.
- A performance note he'd actually care about: don't N+1 crawl folders for "last modified inside" — run one `pageSize=1` query ordered by `modifiedTime desc` per listed folder and cache it as `folderLatestActivityTime`. Sort server-side before pagination, mirror the same comparator client-side so re-sorts don't reshuffle mid-page.

## The real ask
His follow-up is the tell: *"create a prompt to get Cursor to do this for me."* The assistant produced a clean, fully-specified **Cursor prompt** — role, data model, sorting rules, backend tasks (FastAPI/Flask `sort_drive_items`), frontend tasks (React `makeDriveComparator`), pytest + Vitest test cases, exact files to add/modify, acceptance criteria, and seed JSON test data with expected orderings.

## What it shows
This is a clean snapshot of Traveler's actual development workflow: he uses ChatGPT to design the algorithm and spec, then hands a polished prompt to **Cursor** to implement it — the spec-then-delegate "beyond vibe coding" pattern he's been deliberately cultivating (cf. his chats on learning to code for the startup and the Cursor codebase). He's working as an architect/PM over the code rather than hand-writing every line, but the spec is precise (he knows what folders-first, natural sort, and pagination stability mean), so this isn't blind vibe-coding. It also confirms the Homework Hatch stack: Python backend (Flask/FastAPI) + React/TypeScript frontend, with deep Google Drive integration.
