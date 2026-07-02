---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2025-09-09
author: Traveler Stansberry
source_type: chat
tags: [chat, college-apps, startup, admissions]
status: active
---

# iOS App Release Steps and Duke vs UVA ED Chances

A September 2025 ChatGPT (GPT-5) session that opens with a [[Homework Hatch (startup)]] mobile-launch question and then pivots into an extended early-decision strategy analysis — the clearest single snapshot of how Traveler was weighing his top college choices going into senior fall.

## App Store / Play Store launch for Homework Hatch
Traveler asks how hard it is to ship an iPhone (and Android) version of [[Homework Hatch (startup)]] after its web launch. The answer: the code is easy, Apple's rules are the "boss fight." Key takeaways he absorbed:
- **iOS:** $99/yr Apple Developer Program (ideally on the **HW Buddy LLC** company account), Mac + Xcode, provisioning profiles, App Review (no "webview-only" junk), mandatory **Sign in with Apple** if offering Google/Canvas sign-in, **In-App Purchase** for subscriptions (Apple's cut), App Privacy labels, ATT prompt, and a real in-app **account-deletion** flow.
- **Android:** $25 one-time Play Console fee, faster reviews, staged rollout.
- **Stack advice:** **Flutter** single codebase + Firebase/Supabase, with AI jobs queued to his existing AWS backend; TestFlight beta to ~50 students.
- **Compliance flag:** because it touches school data, FERPA/COPPA edges matter — consistent with the legal/ToS worries in [[Custom LLM Build and SPHW Buddy Terms of Service (chat)]] and [[Gemini vs OpenAI API ToS and Cheating Liability for Homework Hatch (chat)]]. Note the recurring **Canvas OAuth** assumption ties back to [[Canvas LMS Adoption Research for Homework Hatch (chat)]].

A brief consumer detour follows (TI-84 Plus CE storage, then Bluetooth MP3 players under $75 for high-school use — SanDisk Clip Sport Plus, AGPTEK, TIMMKOO).

## College admissions: the real substance
He feeds his profile in repeatedly: **4.03 UW / 4.58 W GPA, Cum Laude Society, Homework Hatch creator, 150+ service hours, IB Diploma candidate, 1500 SAT, 33 ACT** — a useful corroboration of [[Academic Record]] and [[Extracurriculars and Achievements]]. He frames the decision as a binding **ED to UVA vs. Duke**, and probes which school he is the *better applicant* for.

The model pushes a consistent thesis: his startup spike makes him a markedly stronger fit at **Duke** (innovation/entrepreneurship culture) than at [[UVA and the Quant Question|UVA]], where out-of-state slots are capped at ~1/3 of the class. Traveler challenges the model's UVA out-of-state numbers and — using a calculator photo — derives a **~3% OOS admit rate (1,767 ÷ 58,995)** himself, catching the model's loose framing. The session expands into a five-school boosted-odds table (all treated as out-of-state):

| School | OOS admit rate | His "boosted" odds |
|---|---|---|
| Duke (ED) | ~16–17% | ~25–30% |
| UVA (OOS) | ~3% | ~6–8% |
| UNC | ~8–12% | ~15–20% |
| Wake Forest | ~20% | ~30–40% |
| UT Austin | ~10–12% | ~20–25% |

He also pulls **IB credit policies** for Duke, Wake Forest, and UNC (Duke: HL only, 6/7 required; Math HL 7 = two credits) — relevant given his [[IB Math (SL)]] track and broader [[IB History (HL)]] / [[IB Economics (SL)]] load.

> [!note] Outcome context
> Traveler ultimately commits to **UVA for finance** (per [[Traveler Stansberry]] and [[College Search]]). This chat captures the moment he was actively talked *toward Duke ED* and still skeptical — he says he "initially thought I was a better applicant for UVA." The Duke-vs-UVA deliberation also recurs in [[Duke, Miami, and Common App Essay Drafting (chat)]] and ranking research in [[Top US College and Finance Undergrad Rankings (chat)]].

## What it shows
A revealing blend of his two senior-year obsessions: turning [[Homework Hatch (startup)]] into a real shippable product, and gaming the admissions math. Characteristically, he doesn't accept the AI's numbers at face value — he recomputes the UVA OOS rate on his calculator and corrects the model, the same quantitative skepticism that runs through his finance and [[UVA and the Quant Question|quant]] interests.
