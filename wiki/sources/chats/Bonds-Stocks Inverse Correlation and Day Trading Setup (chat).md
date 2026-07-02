---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2025-07-14
author: Traveler Stansberry
source_type: chat
tags: [chat, finance, investing, trading, bloomberg]
status: active
---

# Bonds-Stocks Inverse Correlation and Day Trading Setup

A summer 2025 grab-bag chat in which [[Traveler Stansberry]] worked through a string of practical [[Investment Club|investing]] and trading mechanics questions, with a couple of unrelated personal tangents thrown in. The session reads as hands-on self-education: he is learning market relationships, setting up a [[TradingView]] paper-trading account, and figuring out how an underage student can actually start trading and pulling data.

## Finance fundamentals
He opened with two conceptual questions — **why bonds and stocks are inversely correlated**, and **why interest rates and bond prices are inversely correlated**. The answers tie back to material he already studies in [[IB Economics (SL)]]: interest rates as the key link (rising rates lower bond prices and the present value of future earnings), the "flight to safety" / risk-off dynamic, and the exceptions (stagflation, recession rate cuts) where the inverse relationship breaks down. He also confirmed that **profit margin** (net income / revenue) is routinely computed quarterly off 10-Q filings versus annually off 10-Ks — equity-research mechanics consistent with his work in chats like [[Insurance Equity Research - Arch Capital and Palomar (chat)]].

## Trading mechanics
A practical block on getting set up to trade:
- **Resetting a TradingView paper-trading account** (Trading Panel → gear icon → Reset account).
- **How to day trade** — a full primer covering strategies (scalping, momentum, breakouts, VWAP), risk management (1–2% per trade, stop-losses), the U.S. **Pattern Day Trader rule** ($25k minimum for 4+ day trades in 5 days), and the blunt caveat that 80%+ of day traders lose money.
- **Adding a stop loss on TradingView** via the order ticket or by dragging the line on the chart.

## Underage account access
A revealing logistics question: **how to open an Interactive Brokers account as a 17-year-old**. The answer pointed to a **UGMA/UTMA custodial account** with a parent as custodian (cash-only, no margin), assets transferring to him at the age of majority. As a [[St. Paul's School]] senior born around 2008, this is Traveler trying to move from paper trading to real capital — a concrete step beyond the [[Investment Club]] he runs.

## Data tooling
Two [[Bloomberg Terminal|Bloomberg]]-flavored questions show his ongoing familiarity with terminal and Excel workflows (see [[Bloomberg Excel Functions - YoY Revenue, EPS, and Beta (chat)]]): the `BDH` Excel function for historical prices (`=BDH("AAPL US Equity","PX_LAST",...)`, with the note that Jan 1 is a market holiday returning `#N/A`), and the terminal commands `HP <GO>` / `GPO <GO>` for historical price lookups. He also asked how to **select a cell from inside Excel's function dialog**.

The chat closed with a [[Homework Hatch (startup)]]-relevant question: **how to get an API key from Veracross** (St. Paul's student-information system) — creating an OAuth integration partner, obtaining client ID/secret, defining scopes like `students:list`, and running the `client_credentials` flow. This suggests interest in programmatically pulling school data, connecting to his edtech build.

## Personal tangent
One off-topic detour: a survey of **Corvette special editions and modifications** (Z06, ZR1, Grand Sport, Callaway, anniversary/pace-car editions) — a glimpse of personal-interest curiosity amid the finance work.
