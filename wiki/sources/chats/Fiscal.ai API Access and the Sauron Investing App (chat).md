---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2025-08-21
author: Traveler Stansberry
source_type: chat
tags: [chat, coding, finance, investing, data-providers]
status: active
---

# Fiscal.ai API Access and the Sauron Investing App

A working session in which Traveler shops for a financial-data provider to power a personal stock-analysis web app and pressure-tests where the data will come from. It is one of the clearest windows into **Sauron Investing**, a Flask project that sits squarely at the intersection of his [[Investment Club]] research interests and his [[Coding Club]] / [[Homework Hatch (startup)]] engineering practice — and it foreshadows the broader quant ambitions tracked in [[UVA and the Quant Question]].

## The data-provider question
He opens by asking whether **Fiscal.ai**'s $199/mo Enterprise plan includes API data. ChatGPT initially says yes; Traveler corrects it by pasting a screenshot of Fiscal.ai's own fine print — *"API access is not included in the Enterprise plan… contact sales"* — forcing the model to walk back its answer. The takeaway: Enterprise gives manual export only; programmatic API access is a separately negotiated, higher-cost custom contract. This is characteristic of how he uses the model as a fallible research assistant he fact-checks rather than trusts.

He then surveys alternatives:
- **TradingView** — confirmed to have *no* public market-data API (only a broker-integration REST API).
- **Alpha Vantage vs. Fiscal.ai** — Alpha Vantage is Nasdaq-licensed, broad (equities/forex/crypto/macro/technicals), cheap, developer-friendly, but with flagged fundamental-data discrepancies vs. SEC 10-K figures. Fiscal.ai is "institutional-grade," audit-to-filing, AI-enriched (KPIs, IR transcripts), but narrowly focused on company fundamentals. Recommendation: Alpha Vantage for breadth/scale, Fiscal.ai for accuracy-critical fundamental research.

## Sauron Investing (the project)
He has ChatGPT summarize the project from its README/structure. **Sauron Investing** is a Flask stock-analysis web app that ingests Fiscal.ai premium data (250 daily API calls) and computes:
- 5-year annualized **revenue and EPS growth**
- **Valuation/cash-flow** metrics: current P/E, free-cash-flow multiple, 5-year P/E chart with standard-deviation bands
- **Insider activity** as net buying/selling % of market cap
- A **capital-efficiency grade** (A = 20%+, B = 10–15%, C = <10%)
- A **data-accuracy grade** that cross-checks against Google Finance (A = 90–100%)
- **Specialized insurance metrics** — echoing his real insurance-equity research on Arch Capital and Palomar

Architecture: `app.py`/`application.py` entry points, `fiscal_ai_client.py` for API calls, `company_database.py`, `verify_data.py` for the accuracy cross-check, Jinja `templates/`, a suite of `test_*` files, and Heroku-style `Procfile`/`runtime.txt` deployment. This mirrors the Flask/cloud-deploy stack seen in his other build chats.

## What it reveals
The app is essentially an automated, opinionated screener encoding the **same valuation philosophy** Traveler applies by hand in his investing work: growth + reasonable valuation (P/E vs. its own history), capital efficiency, insider alignment, and a built-in distrust of any single data source (hence the Google Finance verification layer). He closes by having ChatGPT draft a professional sales email requesting Fiscal.ai API access for Sauron — showing he was seriously pursuing data infrastructure for the project, not just prototyping.

The naming ("Sauron," all-seeing eye over the market) fits his pattern of themed coding projects. The whole exchange captures his builder profile: research the data layer rigorously, verify the model's claims, and translate a fundamental-analysis thesis into shippable code.
