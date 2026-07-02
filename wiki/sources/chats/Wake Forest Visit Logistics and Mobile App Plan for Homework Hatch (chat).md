---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2025-09-09
author: Traveler Stansberry
source_type: chat
tags: [chat, college-search, startup, personal]
status: active
---

# Wake Forest Visit Logistics and Mobile App Plan for Homework Hatch

A grab-bag September 2025 chat that begins as travel/logistics planning for a [[College Search|college visit]] to Wake Forest University and drifts through personal-curiosity questions before landing on a substantive [[Homework Hatch (startup)|Homework Hatch]] product question about shipping native mobile apps. Useful mostly as a window into Traveler's college-search itinerary and the mobile roadmap for his startup.

## College visit logistics
Traveler was visiting Wake Forest (Winston-Salem, NC) at 3:00 PM with his mom and asked for light-bite restaurants (Theodore's in Reynolda Village, Xia's Asian Tapas, The Remedy, Caviste/Bobby Boy), the Carolina Inn hotel (which the model flagged is actually in Chapel Hill, two hours east), direct flights from BWI (none nonstop to Winston-Salem's Smith Reynolds INT; fly into Greensboro GSO instead), and Wake Forest's mascot (the Demon Deacon). This confirms his fall-2025 college tour included Wake Forest alongside his eventual choice of UVA — see [[College Search]] and [[UVA and the Quant Question]]. The BWI departure point reflects his Maryland home base (see [[Family and Personal Life]]).

## Personal-curiosity detour
Mid-chat he pivots to a string of questions: what a **124 IQ score** means (top ~5-7%, "above average/superior"), whether processing speed changes with age and correlates with ADHD, how ADHD correlates with IQ generally, and whether you can buy alcohol at NC gas stations (beer/wine yes, liquor only at state ABC stores). The IQ/ADHD/processing-speed thread is a personally revealing tangent — consistent with his self-aware, introspective streak documented in [[Emotional Life and Inner World]] and his analytical [[Intellectual Profile]].

> [!note] Possible self-reference
> The "124 IQ score" and ADHD/processing-speed questions read as self-directed (likely his own score or a self-assessment), not abstract curiosity. Treat as a soft personal data point, not confirmed.

## Homework Hatch mobile roadmap
The most substantive segment: Traveler asks how hard it is to get an app on iPhone, planning an iOS-compatible (and Google Play) version of [[Homework Hatch (startup)|Homework Hatch / HW Buddy]] after launch. Key takeaways he received:
- **iOS**: Apple Developer Program ($99/yr), Xcode on a Mac, SwiftUI (native) vs. React Native/Expo or Flutter (cross-platform). Mandatory compliance items: in-app account deletion, privacy nutrition label + App Tracking Transparency, Sign in with Apple if offering third-party SSO, demo reviewer login, no crashes/placeholder content. Estimated 3-8 weeks for a focused dev given an existing backend.
- **Android**: Play Console ($25 once), AAB bundle, Data safety form — generally easier/faster review.
- A suggested **HW Buddy feature checklist**: Canvas OAuth onboarding, today's-assignments home, due-soon push notifications, a study-tools tab (summarize/flashcards), a course-aware chat helper, and settings with account deletion.

This ties directly to the app's Canvas-LMS integration work (see [[Canvas LMS Adoption Research for Homework Hatch (chat)]]) and the broader architecture and build threads (see [[HW Buddy App Architecture Analysis and GPT-5 Model Choice (chat)]] and [[Building a ChatGPT-Powered Discord Bot for HW Buddy (chat)]]). The model also closed by offering to draft a SwiftUI/React Native screen map to hand "straight to Cursor" — his coding tool of choice (see [[Cursor and the sisyphus10 Codebase Overview (chat)]]). Relevant to his role in [[Coding Club]] and [[Extracurriculars and Achievements]].
