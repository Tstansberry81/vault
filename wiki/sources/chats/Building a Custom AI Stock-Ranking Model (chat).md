---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2025-07-08
author: Traveler Stansberry
source_type: chat
tags: [chat, finance, coding, machine-learning, investing]
status: active
---

# Building a Custom AI Stock-Ranking Model (chat)

A July 2025 ChatGPT (GPT-4o) session in which Traveler tries to design his own AI system that ingests market data, scores every stock, and writes investment reports ranking the best picks. It sits squarely at the intersection of his two biggest interests — [[Investment Club]]-style equity analysis and the [[Coding Club]] / [[Homework Hatch (startup)]] technical side — and reads like an early, ambitious spec for an automated stock screener of his own.

## What he was doing
He opened by asking broadly "how can I create a custom LLM?" and was walked through three paths: fine-tuning an open model (LLaMA 2 via Hugging Face + LoRA/PEFT), training from scratch, and prompt-engineering/RAG. He quickly homed in on the real goal: **"train an AI model to look at different stocks and find stocks that are performing well so I can invest."** He chose the most ambitious route — pulling data from the **Bloomberg Terminal API** (`blpapi` / `xbbg`), engineering features, scoring with a tabular model (LightGBM / time-series Transformer), ranking all stocks, then feeding the top names into a fine-tuned **LLaMA 2** that writes natural-language reports. ChatGPT eventually generated a full `ai_stock_pipeline.py`, then iterated on error-handling, and finally swapped the Bloomberg integration for a simulated data generator since he lacked live `xbbg` access.

The architecture proposed: `Bloomberg API → feature engineering (P/E, EPS, momentum, volatility, Sharpe, RSI, MACD) → LightGBM scoring → rank → LLaMA 2 report generation → daily output (cron / Streamlit / email)`.

## What it reveals
- His genuine ambition to **automate** equity research rather than just learn the metrics — a more builder-minded extension of the manual Bloomberg screening seen in [[Bloomberg EQS Screening and Insurance Stock Research (chat)|Bloomberg EQS Screening and Insurance Stock Research]] and [[Stock Valuation Metrics, Bonds, Options, and Bloomberg ROIC (chat)|Stock Valuation Metrics, Bonds, Options, and Bloomberg ROIC]].
- A realistic gap between ambition and resources: he assumes Bloomberg Terminal access and A100-class GPUs, and the session ends with the AI quietly stubbing out the data source he can't reach. The "see errors and fix code" loop shows him iterating without yet having an environment to actually run any of it.
- The session drifts back into **fundamentals review** in its second half — he asks for the meanings of beta's benchmark (S&P 500), loss ratio / expense ratio / combined ratio (insurance underwriting), [[Bloomberg ROIC|ROIC]] vs. WACC, FCF yield vs. FCF margin, plus quick lookups (Hershey/HSY, Cardinal Health/CAH tickers) and an Excel "convert table to range" tip. The insurance-ratio focus connects to his ongoing insurance equity work in [[Insurance Equity Research - Arch Capital and Palomar (chat)|Insurance Equity Research - Arch Capital and Palomar]].

> [!note] "Sir Dorman"
> ChatGPT repeatedly addresses him as "Sir Dorman" here — a custom-instruction persona/nickname, useful as a fingerprint that this is Traveler's own account.

## Connections
Reinforces his [[Intellectual Interests]] in quantitative finance and the [[UVA and the Quant Question]] thread (finance major, math minor, quant-curious). The desire to build an ML-driven stock ranker echoes the technical ambition behind [[Homework Hatch (startup)]], showing the same instinct applied to investing rather than edtech.
