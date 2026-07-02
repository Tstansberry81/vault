---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2025-08-18
author: Traveler Stansberry
source_type: chat
tags: [chat, gaming, pc-troubleshooting]
status: active
---

# RDR2 Debt-Quest Crash Fix on RTX 5090 Build (chat)

A marathon, image-heavy troubleshooting session (gpt-5, 18 Aug 2025) in which [[Traveler Stansberry]] tries to stop *Red Dead Redemption 2* from crashing-to-desktop at specific story beats — most stubbornly the **Strauss debt-collection mission** ("Money Lending and Other Sins", the Mrs. Londonderry / "Mrs. Willet" cutscene) and the **Hosea big-bear hunting quest** in Chapter 2. The crash reliably hit the moment a cutscene/cinematic began. He worked the problem for hours (he asks the AI mid-chat "when did this chat begin… ive been trying to bug fix it since then lmao").

## What he tried (the "nuclear fix path")
- Switching the graphics API **Vulkan → DirectX 12** (the standard fix; he eventually forced it through the in-game menu after `system.xml` edits wouldn't stick).
- Editing `system.xml` in `Documents/Rockstar Games/Red Dead Redemption 2/Settings`, deleting `.sga` cache files, adding launch args `-ignorepipelinecache` and `-cpuLoadRebalancing`.
- Disabling Steam + Rockstar **overlays**, fullscreen optimizations, running as admin, toggling autosave.
- Asking ChatGPT to **write PowerShell scripts** to automate the config edits, move files, and even launch RDR2 for him — repeatedly pasting screenshots when the scripts misfired.

## The actual root cause / resolution
None of the config fixes worked; the save itself was the problem (a corrupted/blocked mission flag — he'd started the "final" Strauss quest out of order). The fix path became: install **ScriptHook + the Rampage Trainer mod** to manipulate the save, then ultimately **download a known-good save file** that let him progress past the stuck Hosea mission. He notes he'll have to replay many quests and is unsure it was worth it, but thanks the assistant sincerely at the end.

## Why it matters
This documents his **high-end gaming rig** in full and his hands-on, persistent debugging style — he treats ChatGPT as a pair-programmer/tech-support, asking it to generate scripts and reading error dumps (e.g. `SteelSeriesCaptureSvc.exe` faults). The same machine recurs across his hardware chats; see [[ROG Swift PG27AQDP 480Hz Dual-Monitor Black Screen on RTX 5090 (chat)]], [[Gaming PC Specs and ASUS ROG Monitor Troubleshooting (chat)]], and [[Uninstalling ASUS Armoury Crate to Fix Monitor Detection (chat)]].

> The build: **ASUS RTX 5090 ROG Astral O32G**, **Ryzen 7 9800X3D**, MSI Pro X870E-P, Lian Li 1200W PSU + Hydroshift II 360 AIO, 64GB DDR5-6000, 2TB Samsung 990 Pro, NZXT H9 Flow, Win 11. Peripherals: ASUS PG27AQDP WOLED, SteelSeries Arctis Nova Pro, Logitech Pro 2 Lightspeed, Keychron V1 Max.

A pure leisure/personal-tech chat — no coursework or [[Homework Hatch (startup)]] content — but a clean window into how he attacks a frustrating technical problem until it breaks.
