---
type: entity
created: 2026-06-18
updated: 2026-06-18
tags: [finance, quant, project, ai, code, product]
sources: ["[[vision.zip]]"]
status: active
---

# Vision (Porter Intelligence)

The **consumer-facing product front-end** for [[Traveler Stansberry]]'s quant work (`raw/vision.zip`, June 2026) — a lightweight **static site** that turns the [[The Edge (trading model)|Edge model]]'s output into a "size it to your capital" 10-stock portfolio dashboard. It holds **no model code**; it just renders a generated data snapshot. The branding is **"Porter Intelligence,"** styled to match the house look of his father's [[Porter Stansberry (father)|Porter & Co.]] — the clearest sign yet that Traveler is aiming his model at his father's financial-publishing world as an actual product.

## The pipeline
```
the Edge repo (in-house model) ──► export_sauron.py ──► vision_data.js ──► index.html
```
`export_sauron.py` (in the Edge repo) runs the model at the launch config and writes `vision_data.js` (`window.VISION_DATA = {…}`), which `index.html` loads cache-busted with an N/A fallback. The product config: **2-year + 20-year backtests, 1-month rebalance, 75% YoY-revenue-growth mix, 10-stock equal-weight, ~10 bps cost.** The internal product name in the data feed is still **"Sauron"** (see [[Sauron Investing]]); the public skin is "Vision · Porter Intelligence."

## What it shows
- A **capital → 10 positions** sizing flow (enter your capital, get share counts for the equal-weight book).
- The **current 10-stock book** (launch snapshot `as_of` 2026-04-17: AAOI, CAR, UI, MOD, VRT, NIO, MARA, SM, VG, CRWV) with sector and acceleration score.
- A **2-year growth-of-$1 curve** and a **20-year track-record curve**, each vs the S&P 500, plus headline stats. The 2Y headline reads CAGR ~49.8% / Sharpe 1.65 / max DD −12.9% — see the [[The Edge (trading model)#The honest read on performance|honest-performance caveat]] (the 10–20Y windows are far more modest).
- A standing **disclaimer**: *"Backtest, net of ~10 bps costs. Not a forecast or investment advice."*

## Design
A polished dark-green Porter-style theme (Fraunces / Inter / JetBrains Mono, faint grid texture, green glow) — a deliberate corporate-product look, not a research notebook. Pure static (`render.yaml` is a Render static-site blueprint; also Netlify/Vercel/Pages-friendly).

## Why it matters
Vision is the **packaging layer** that turns the [[The Edge (trading model)|Edge]] from a personal research tool into something presentable to an audience — and it does so under the **Porter Intelligence** name. It ties the [[Quantitative Finance|quant thread]] directly to [[Porter Stansberry (father)|his father's]] industry: a son building a quant product in (and branded for) the family business. For the [[UVA and the Quant Question|quant question]] it's evidence of **product sense and ambition**, not of math rigor — the model behind it is still AI-coded.

## See also
[[The Edge (trading model)]] · [[Sauron Investing]] · [[Personal Quant Model]] · [[Porter Stansberry (father)]] · [[Quantitative Finance]] · [[Homework Hatch (startup)]] · [[Traveler Stansberry]]
