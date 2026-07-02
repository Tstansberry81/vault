---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2025-11-03
author: Traveler Stansberry
source_type: chat
tags: [chat, startup, homework-hatch, canvas, web-scraping]
status: active
---

# Canvas API Key Revoked - Extension Scraper and LMS Access Strategy

A [[Homework Hatch (startup)]] engineering/strategy chat triggered by a hard blocker: the school disabled the Canvas API key the product had been relying on to pull assignment data. Traveler asks for "the best current way to scrape assignment data" now that the official key is gone — a recurring theme in his startup work, where LMS access is the load-bearing dependency.

## The ranked options
ChatGPT lays out five routes, ranked by robustness vs. risk:
1. **Proper LTI 1.3 / Canvas developer keys / Canvas Data / Caliper** — supported, auditable, scalable, FERPA-friendly. Requires school admin buy-in (scopes can't be self-granted). The "correct" long-term answer.
2. **Browser-extension client-side collector** — each student opts in and the extension reads their own Canvas pages, so there's no server-side impersonation. The recommended fallback when admins won't cooperate.
3. **Headless scraping (Playwright/Puppeteer)** with user sessions — brittle, ToS/legal risk, emergency-only.
4. **Email-notification forwarding** parsed into assignments — cheap and reliable but inconsistent.
5. **Manual uploads + Drive/OneDrive sync** — low-tech, fully compliant (connects to his earlier Drive-sync and OneDrive work).

The key technical insight pushed throughout: intercept `fetch`/`XHR` JSON responses rather than scraping the DOM, since Canvas is a single-page app and DOM scraping is fragile.

## What he chose to build
Traveler picks the extension route and asks for it "as user friendly as possible." ChatGPT produces an MV3 (Manifest V3) Chrome/Edge/Firefox extension starter kit: `manifest.json` scoped to Canvas hosts, a `content.js` that overrides `window.fetch` and `XMLHttpRequest.prototype.send` to capture assignment JSON, a `schema.js` sanitizer (metadata only — id, course_id, name, due date, points, url, published, submission types; explicitly strips submissions/comments), a `background.js` batching queue with exponential backoff and JWT upload, plus popup/options UI for single-toggle consent and token capture. He's told to swap in `YOUR_API_BASE`/`YOUR_PROJECT_ID` and wire `signIn()` to the real Homework Hatch auth.

## The unresolved question
He then asks which colleges currently let students self-generate Canvas personal access tokens (searching Reddit for current-year evidence). ChatGPT honestly reports it **could not confirm** any named institution — only vague r/Professors and r/canvas posts — and recommends he survey early adopters per-school to learn whether token generation is enabled, falling back to the extension where it isn't. This pins down the central uncertainty in his go-to-market: token availability varies by Canvas install, so the extension is the safe universal intake.

## What it shows
A clear-eyed snapshot of Traveler operating as a solo founder hitting a real infrastructure wall and reasoning through legal (FERPA, ToS), technical (XHR interception, MV3), and distribution (per-school token policy) tradeoffs at once. It connects directly to his broader LMS-ingestion thread — see his Canvas adoption research, LMS credential-ingestion, and scraping-strategy chats — and reflects the privacy-first posture he later leaned into. He defaults to consent-based, metadata-only collection rather than credential scraping, consistent with the admin-free privacy pivot elsewhere in the project.
