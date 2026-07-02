---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2025-08-13
author: Traveler Stansberry
source_type: chat
tags: [chat, hardware, pc-gaming, troubleshooting]
status: active
---

# ROG Swift PG27AQDP 480Hz Dual-Monitor Black Screen on RTX 5090

A live PC-troubleshooting session where [[Traveler Stansberry]] tries to recover his main monitor after accidentally setting it to an unsupported refresh rate in the NVIDIA Control Panel. The chat is one-directional tech support — ChatGPT walks him through fixes while he photographs his screens — but it incidentally documents his high-end gaming/desktop rig.

## The setup it reveals
- **Main monitor:** ASUS **ROG Swift PG27AQDP** — a 27" 1440p **480 Hz OLED** panel (he corrects the model twice; ChatGPT first wrongly assumes 144 Hz).
- **GPU:** **NVIDIA RTX 5090**.
- **Secondary monitor:** a basic 60 Hz display.
- Dual-monitor extended desktop, mixed connections (HDMI/DisplayPort).

This is a flagship, money-no-object build — consistent with the ASUS ROG hardware in [[ASUS ROG OLED Monitor - RGB Lighting and Key-Lock Firmware Loop (chat)]] and his general consumer profile (high-end gaming PC alongside finance/coding work).

## The problem
He set the refresh rate to **360 Hz** by accident; the main monitor went to "no signal" and Windows fell back to driving only the 60 Hz secondary (later showing the main stuck at a failsafe **39.95 Hz**). The core bind: every time he reconnects the secondary to open NVIDIA Control Panel, the bad saved mode immediately re-fires and drops the main, so he can't fix it with both plugged in.

## The fixes offered
- Boot with **only the main monitor** connected so Windows reverts to a safe refresh, then reset a clean 480 Hz (8-bit color) mode.
- Reset via **Windows Safe Mode** (Shift+Restart → Troubleshoot → Startup Settings → 4).
- Restart the GPU driver with **Win+Ctrl+Shift+B**.
- Bandwidth reasoning: 1440p @ 480 Hz maxes DisplayPort 1.4 + DSC, so keep main on **DisplayPort** and secondary on **HDMI** to separate link controllers; drop color depth to 8-bit to free bandwidth.
- Nuclear option: wipe NVIDIA's saved EDID/mode profiles with **DDU (Display Driver Uninstaller)** in Safe Mode, then reinstall the driver fresh.

ChatGPT visibly fumbles here — it gives a wrong/garbled `DriverStore\FileRepository` path, and Traveler catches a typo (`DriverStone`) in one of his own screenshots — a small reminder that he uses the model as a fast-but-fallible support desk rather than an authority.

## Why it's in the wiki
Low intellectual content, but a clean data point on his personal hardware (RTX 5090, PG27AQDP) and his habit of leaning on ChatGPT for hands-on hardware/IT problems. Connects to his broader [[Film and TV]]/gaming-adjacent personal-life footprint and his coding/tech fluency.
