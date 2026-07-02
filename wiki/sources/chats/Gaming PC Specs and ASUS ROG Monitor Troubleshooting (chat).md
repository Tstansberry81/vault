---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2025-08-12
author: Traveler Stansberry
source_type: chat
tags: [chat, gaming, hardware, personal]
status: active
---

# Gaming PC Specs and ASUS ROG Monitor Troubleshooting

A long, mostly practical tech-support session in which [[Traveler Stansberry]] photographs his desktop and a parts list, asks ChatGPT to identify and "analyze" the build, then spends most of the chat troubleshooting a dead-display / locked-OSD / dead-mic situation. Low intellectual content, but it is the clearest single record of his actual gaming/work rig, which his coding and startup work ([[Homework Hatch (startup)]]) run on.

## The build (documented here for the first time)
An "ultra high-end" gaming system, itemized from his own parts photo:
- **GPU**: ASUS RTX 5090 ROG Astral O32G
- **CPU**: AMD Ryzen 7 9800X3D
- **Motherboard**: MSI PRO X870E-P WIFI (AM5, PCIe 5.0)
- **RAM**: Corsair 64GB (2×32GB) DDR5-6000
- **Storage**: Samsung 990 Pro 2TB NVMe Gen4
- **Case**: NZXT H9 Flow TG
- **Cooler**: Lian Li Hydroshift II LCD-360TL; PSU Lian Li Edge Gold 1200W
- **Monitor**: ASUS ROG Swift OLED PG27AQDP (27" 1440p WOLED, 480 Hz)
- **Peripherals**: SteelSeries Arctis Nova Pro headset (with GameDAC), Logitech Pro 2 Lightspeed mouse, Keychron V1 Max keyboard, Razer Firefly V2

He asks for estimated FPS (including Minecraft Java/shaders), then has ChatGPT spec a "Beyond God-Tier" Threadripper workstation (~$27–34k) as a thought experiment.

## What he was actually fighting
Most of the transcript is a frustrated debugging marathon: monitors not connecting after working "yesterday," a **key-locked OSD** he can't unlock, **Armoury Crate** refusing to sync the monitor (installer hangs, "path too long" and "(507) busy" errors, uninstaller failing), and the **Arctis Nova Pro mic getting zero input** — traced to the GameDAC being stuck on USB-2 / unable to switch to USB-1, leaving it possibly an RMA. Workarounds he's pointed to: DDC/CI tools (Monitorian, ClickMonitorDDC) and the NVIDIA control panel to set brightness without the locked buttons.

## Why it matters
- One revealing aside: he asks whether the build will be "good at storing vast amounts of user data" — a tell that he was thinking about hosting/backing data for [[Homework Hatch (startup)]] on his own machine, before later chats move that workload to AWS.
- Reinforces the gamer/builder side of his [[Family and Personal Life]] — this is a high-budget personal rig, consistent with his finance-track materialism and [[Extracurriculars and Achievements]] in [[Coding Club]].

Otherwise this is throwaway IT support with no coursework or analytical content.
