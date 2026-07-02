---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2025-07-08
author: Traveler Stansberry
source_type: chat
tags: [chat, finance, bloomberg, equity-research]
status: active
---

# Bloomberg Excel Functions - YoY Revenue, EPS, and Beta

A rapid-fire reference session in which [[Traveler Stansberry]] asked ChatGPT for the exact **Bloomberg Excel add-in formulas** (`BDP` for single data points, `BDH` for historical series) to pull common equity metrics. The all-caps, terse queries and the live-terminal context (he was clearly working at a Bloomberg-equipped workstation, likely a summer finance internship/program in July 2025) make this a working tool-reference, not a learning exercise. It complements his hands-on equity-research chats like [[Insurance Equity Research - Arch Capital and Palomar (chat)|Insurance Equity Research - Arch Capital and Palomar]] and [[Stock Valuation Metrics, Bonds, Options, and Bloomberg ROIC (chat)|Stock Valuation Metrics, Bonds, Options, and Bloomberg ROIC]].

## Fields he collected
- **Revenue growth YoY:** `=BDP("AAPL US Equity","SALES_GROWTH")`; manual route via `BDH(...,"SALES_REV_TURN",...,"PERIOD=YEAR")`.
- **EPS:** `EPS_T12M` (trailing 12m), `BEST_EPS` (Bloomberg consensus, current fiscal year — forward-looking), `BEST_EPS_NXT_YR`, `BEST_EPS_CUR_QTR`. He specifically probed what `BEST_EPS` means (analyst consensus, not historical).
- **Diluted EPS:** `EPS_DIL_T12M`, `EPS_DIL`.
- **Most-recent-quarter actual EPS:** `EPS_REPORT`.
- **Leverage:** `TOT_DEBT_TO_EBITDA`, `TOT_DEBT_TO_ASSETS` (and the component fields `TOT_DEBT`, `EBITDA`, `BS_TOT_ASSET` to build ratios by hand).
- **Adjusted beta:** he wanted *overridable adjusted beta* (`BETA_ADJ_OVERRIDABLE`) as a monthly time series 2020–2025; ChatGPT flagged that this is a point-in-time calculated field that can't be pulled historically via `BDH`, and gave the proper workaround — pull monthly `PX_LAST` for stock and `SPX Index`, compute returns, and run `=SLOPE()` for rolling beta.

## Troubleshooting thread
He hit real friction ("NOT WORKING", "montly prices arent working"), which surfaced practical add-in gotchas: `NONTRADINGDAY=PREVIOUS_VALUE` to avoid blanks on weekends/holidays, using month-start dates (`07/01`) rather than mid-month for `PERIOD=MONTHLY`, and confirming the terminal is logged in. The session ended with him asking to make a price lookup **dynamic** so he wouldn't re-edit dates manually — landing on `TEXT(EDATE(TODAY(),-12),"mm/dd/yyyy")` for a self-updating "price one year ago" cell, and pulling the ticker from a cell reference (`A1`) for reusability.

## What it shows
Concrete evidence of [[Traveler Stansberry]] doing professional-grade financial modeling on a live Bloomberg Terminal — building reusable, parameterized Excel sheets rather than one-off lookups. The instinct to make formulas dynamic and cell-driven reflects the same systematizing, tool-building bent behind [[Homework Hatch (startup)]] and his [[Coding Club]] teaching, applied here to his [[UVA and the Quant Question|finance]] track and [[Investment Club]] interests.
