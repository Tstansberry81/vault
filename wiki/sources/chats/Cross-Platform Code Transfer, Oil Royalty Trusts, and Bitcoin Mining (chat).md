---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2025-10-07
author: Traveler Stansberry
source_type: chat
tags: [chat, coding, finance, japanese, college-apps]
status: active
---

# Cross-Platform Code Transfer, Oil Royalty Trusts, and Bitcoin Mining

A wide-ranging single-session ChatGPT chat (GPT-5, 7 Oct 2025) that hops across five unrelated topics. It is a useful cross-section of [[Traveler Stansberry]]'s simultaneous threads: shipping his startup's code, vetting a college-app credential, an [[IB Japanese (SL)]] vocabulary check, and energy/crypto investing curiosity for [[Investment Club]].

## Porting the Homework Hatch app from Windows to macOS
The framing question is logistical and reveals his dev setup: his [[Homework Hatch (startup)]] application is a **Python app built on Windows** (using shell-set environment variables and a `venv`), and he needs to keep working on it during a week in **London** on a Mac. The assistant lays out a "use it this week" path: recreate the venv with `pyenv`/matching Python version, fix CRLF line endings via `.gitattributes` (`* text=auto eol=lf`), and — the key portability fix — **stop hard-coding env vars in the shell and load a `.env` via `python-dotenv`** so the same code reads config on both OSes. The "make it bulletproof" path pushes Docker/Dev Containers, a `Makefile`/`justfile` for single-entry commands, a CI matrix across ubuntu/macos/windows, and `pathlib` over hardcoded backslashes. This confirms the app is Flask-flavored Python and that he was actively cross-platform developing while traveling.

## Is NSHSS a scam? (college-app credential vetting)
He asks whether the **National Society of High School Scholars** is a scam. The verdict: not criminally fraudulent (BBB A+, real structure) but a "vanity honor society" with mass invitations, low selectivity, name-confusion with NHS, and weak ROI on the ~$90 lifetime fee. Practical due diligence consistent with his [[College Search]] / [[Extracurriculars and Achievements]] mindset — he treats pay-to-join honors with the same skepticism he brings to investing.

## Japanese: "Soga Shoshi" disambiguation
A quick [[IB Japanese (SL)]] vocabulary thread. He first writes "Soga Soshi" (蘇我宗師 = "Master/Grandmaster Soga," a religious/martial title with no business meaning), then corrects to **蘇我商事 (Soga Shōshi)** — where 商事 (shōshi) = "commercial affairs / trading company," the standard suffix in firms like 三菱商事 (Mitsubishi Corporation) and 伊藤忠商事 (Itochu). So "Soga Shōshi" = "Soga Trading Company." A small but telling overlap of his Japanese study and his finance interest in corporate naming.

## Energy investing: high-ROIC oil and the royalty-trust model
The longest finance thread, aimed at [[Investment Club]] / [[UVA and the Quant Question]] interests. He asks for oil companies with **high ROIC** (Chevron ~13.6%, Imperial Oil ~13.1%, Devon, ConocoPhillips), then LNG players (Cheniere/ticker LNG, Freeport, TotalEnergies, Shell, QatarEnergy, plus shippers Golar/GasLog/Teekay). The sharpest moment: he asks what it's called when a company **only owns the land rights and collects royalties** — answer: a **royalty / mineral-rights interest** (vs. working interest that bears drilling costs; ORRI for brokers). He then gets a top-10 of **mineral royalty trusts / companies**: Viper Energy (VNOM), Black Stone Minerals (BSM), Kimbell (KRP), Dorchester (DMLP), Texas Pacific Land (TPL), Sabine (SBR), Permian Basin (PBT), Cross Timbers (CRT), San Juan Basin (SJT), Hugoton (HGT). The royalty-trust model — capital-light, off-the-top royalty income, no drilling capex — is exactly the kind of high-return, asset-light business his value-investing instincts gravitate toward.

## Bitcoin mining explainer
He closes by asking how Bitcoin mining works. The answer walks through the blockchain ledger, SHA-256 proof-of-work (finding a nonce that hashes below target), block rewards (3.125 BTC post-2024 halving) plus fees, the 51%-attack security argument, ASIC rigs (Antminer S21, WhatsMiner M60, ~3,000W each), mining pools, and energy controversy. General-curiosity finance/tech, not coursework.

## What it shows
A snapshot of his parallel lives in one window: a working founder solving real deployment friction ([[Homework Hatch (startup)]]) while abroad, a college applicant doing credential due diligence, a Japanese student, and a finance-minded investor probing capital-efficient business models. The connective thread is ROI-driven skepticism — he evaluates honor societies, oil majors, and royalty trusts with the same "what's the actual return" lens.
