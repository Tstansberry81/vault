---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2025-08-12
author: Traveler Stansberry
source_type: chat
tags: [chat, gaming, pc-hardware, troubleshooting]
status: active
---

# Uninstalling ASUS Armoury Crate to Fix Monitor Detection

A short PC-hardware troubleshooting session in which [[Traveler Stansberry]] works through removing leftover **ASUS Armoury Crate** install remnants on his Windows gaming machine. The problem: his ASUS monitor showed up under "user data" but not in Armoury Crate's **Devices** tab, leaving him unable to edit its settings (RGB/Aura, profiles).

ChatGPT (GPT-5) walked him through the official ASUS uninstall tool, then manual cleanup of program folders, AppData, and registry keys. When Traveler asked it to "use your agent version" to do the work directly, the model clarified it can't run anything on his PC and instead produced a full `Remove-ArmouryCrate.ps1` PowerShell script — killing ASUS processes, deleting services (`ArmouryCrateService`, `LightingService`, `ROGLiveService`), unregistering scheduled tasks, purging folders and device-profile caches, and removing `HKLM/HKCU\SOFTWARE\ASUS` registry keys (with a backup step first). The final exchange debugged a "file not found" error, traced to OneDrive hijacking the Desktop path and the classic `.ps1.txt` extension gotcha.

## What it reveals
- Confirms his **gaming rig is ASUS ROG hardware** (Armoury Crate / Aura ecosystem, dedicated gaming monitor), filling in the hardware side of his [[Film and TV]]-adjacent [[Family and Personal Life]] gaming life.
- Shows his instinct to reach for an "agent" to just *do* the task — consistent with his interest in agentic AI tooling elsewhere (cf. his [[Homework Hatch (startup)]] MCP/agent work) — and his comfort pasting and running admin PowerShell scripts.
- Pure personal/utility troubleshooting; no coursework or intellectual content.
