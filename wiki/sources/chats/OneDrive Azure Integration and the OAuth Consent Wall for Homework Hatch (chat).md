---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2025-10-06
author: Traveler Stansberry
source_type: chat
tags: [chat, startup, homework-hatch, oauth, cloud-integration]
status: active
---

# OneDrive Azure Integration and the OAuth Consent Wall for Homework Hatch

A development/setup chat (2025-10-06, GPT-5) in which Traveler wires up a **Microsoft OneDrive connector** for [[Homework Hatch (startup)]], then discovers a structural threat to the whole cloud-sync model: school and college IT tenants routinely block third-party OAuth app consent. The conversation moves from "how do I click through Azure" to "is this a fatal flaw for the product," and it's one of the clearer windows into Hatch as a real data-ingestion platform rather than a toy.

## What he was doing
The connector mirrors the [[Google Drive Folder Tree Mirroring for Homework Hatch (chat)|Google Drive]] and Canvas integrations already in Hatch — OneDrive is "just another data-source connector." The assistant walks him through registering an app in **Microsoft Entra ID** (Azure AD): new app registration, choosing *"Accounts in any organizational directory and personal Microsoft accounts"* (multi-tenant), collecting the client/tenant IDs, adding **Microsoft Graph** delegated permissions (`User.Read`, `Files.ReadWrite`, `offline_access`), creating a client secret, and configuring redirect URIs (`localhost:3000` for dev, `homeworkhatch.com` for prod). He confirms the app already pulls from Canvas, generates study guides/flashcards, and computes college odds — consistent with the architecture seen across his other [[Homework Hatch (startup)]] chats and the [[Building a ChatGPT-Powered Discord Bot for HW Buddy (chat)|HW Buddy]] work.

A debugging aside: a screenshot of a `No such file or directory` error on `application.py` was just a wrong-working-directory issue running the venv Python from `C:\Users\14105\` instead of the project folder (`HOMEWORK HATCH 2`). Confirms he runs a Flask app locally on Windows.

## The structural problem
When he tried to connect his school `@stpaulsmd.org` account ([[St. Paul's School]]), tenant policy blocked third-party consent — admins disable "users can consent to apps accessing company data." He immediately grasped the stakes: *"this might be a fatal flaw for onedrive integration."* The assistant confirmed it's **very common** in K-12 and higher ed, including universities tightening third-party app access. Same wall exists on the Google side: unverified apps requesting sensitive Drive scopes are capped at **100 users lifetime** until they pass Google's **OAuth app verification** (privacy policy, demo video, scope justification, domain ownership; full-`drive` restricted scopes can trigger a $15k–$75k third-party security audit).

Workarounds discussed: personal Microsoft/Gmail accounts for early users, the Microsoft 365 Developer sandbox tenant, requesting tenant-wide admin consent (with a copy-paste IT-admin email he was given), publisher verification, minimizing scopes (`Files.Read` / `drive.file` over full access), and a manual share-link/upload fallback. He asked for data on what percent of college students use personal cloud accounts as primary storage; no solid survey exists, estimate landed around 10–30%.

## What it shows
This is Traveler operating as a **founder hitting platform-governance reality** — the bottleneck on Hatch isn't code, it's the OAuth verification and admin-consent gauntlet imposed by Microsoft, Google, and school IT departments. It reflects his characteristic pattern of building real infrastructure (Azure registrations, Graph scopes, multi-tenant flows) while running ahead of himself into questions of institutional adoption. Connects to his startup-governance concerns in [[Gemini vs OpenAI API ToS and Cheating Liability for Homework Hatch (chat)]], the [[Canvas LMS Adoption Research for Homework Hatch (chat)|adoption]] and [[Homework Hatch Competitor Strategy and the Admin-Free Privacy Pivot (chat)|privacy-pivot]] strategy work, and his [[Extracurriculars and Achievements|entrepreneurial profile]]. The closing idea — building a "Connect OneDrive → Export → Import to Google Drive" flow that migrates only *Hatch-relevant* files — shows him reframing a constraint into a scoped product feature.
