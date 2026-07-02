---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2025-09-24
author: Traveler Stansberry
source_type: chat
tags: [chat, coding, homework-hatch, google-drive, api]
status: active
---

# Google Drive Folder Tree Mirroring for Homework Hatch

A debugging session (ChatGPT, GPT-5, 2025-09-24) in which Traveler iterates on the Google Drive ingestion layer for [[Homework Hatch (startup)]]. The goal: when a user connects their Drive, the app should display their files **exactly as Drive's own web UI shows them** — top-level "source folders" first, then drill-down — rather than a flattened dump of everything the account can see. This is part of the same [[Homework Hatch (startup)]] data-ingestion problem space as the LMS/Canvas scraping chats, but here the target is personal Google Drive.

The chat opens with one of Traveler's recurring custom ChatGPT "mode" personas (0=Normal, 1=Researcher, 2=Data Analyst, 3=Advice Giver, 4=Coder) — he selects **Mode 4 (Coder)**, the same jailbreak-flavored persona system documented in his [[Canvas API Access Audit and Custom ChatGPT Mode System (chat)]]. The assistant answers in a deliberately abrasive "code-monkey" register throughout.

## The technical arc
1. **First attempt (wrong):** a script that pulled *everything* via `files.list` with `includeItemsFromAllDrives=True` and tried to infer each file's "source folder" by climbing the parent chain. Result (shown in his screenshot): junk — `.git`, `.venv`, duplicate timestamp folders, items from "Shared with me" and other people's drives. The model's diagnosis: "You pulled the whole circus instead of the stage."
2. **The fix:** mirror the UI by querying only direct children. Top level = `q = "'root' in parents and trashed = false"` with `corpora="user"`, `spaces="drive"`, `orderBy="folder,name"`; each folder's contents = `'<folder_id>' in parents`. Shortcuts to folders are followed to their **target** id, not the shortcut stub. "Shared with me" items never appear because they have no parent under `root`.
3. **Code review of his own module (`google_drive_source_folders.py`):** the model flags three real bugs in code Traveler pasted — (a) folder shortcuts stored the shortcut's id instead of the target folder id, so later `'<id>' in parents` queries would return nothing; (b) fabricated metadata (`owners: me@example.com`, hardcoded `size`/`modifiedTime`), which "users will think your app is broken"; (c) a dead compatibility stub `get_google_drive_source_folders()` that always returned `[]`.
4. **Rewire of the sync manager:** Traveler then pastes `GoogleDriveSyncManager` and the model catches that he'd **duplicated the entire Drive-traversal logic inside the sync manager**, re-introducing the bugs they'd just killed. The cleaned version delegates all Drive structure logic to the single helper, adds proper OAuth token refresh (build `Credentials` with refresh token, retry on 401/403), linear backoff over 3 attempts, and per-user daemon sync threads on a 5-minute interval.

## What it reveals
This is hands-on backend engineering, not vibe-coding: Traveler is wrestling with real Google Drive API semantics (root aliases, shared drives, shortcut resolution, pagination, OAuth refresh tokens) and per-user multi-tenant sync for [[Homework Hatch (startup)]]. It shows the recurring pattern in his coding work — he pastes AI-generated code, runs it, hits a concrete failure, and iterates against the actual output — consistent with his stated push to move [[Learning to Code for Homework Hatch - Beyond Vibe Coding (chat)|beyond vibe coding]]. The "duplicate traversal in the sync manager" mistake also shows a genuine weakness the AI caught: copy-paste drift across modules that silently regressed an already-fixed bug. The deliberate use of the Mode-4 persona ties into how he frames [[Homework Hatch (startup)]] more broadly: a homework-help tool whose entire value is ingesting a student's real coursework files (Drive, Canvas/LMS) so the AI can act on them.
