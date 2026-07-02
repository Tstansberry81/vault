---
type: entity
created: 2026-06-17
updated: 2026-06-18
tags: [finance, quant, project, ai, code]
sources: ["[[personal quant model.zip]]", "[[quant model.zip]]"]
status: active
---

# Personal Quant Model

A multi-factor **quantitative equity model** + Flask web app **conceived and directed by [[Traveler Stansberry]]** (git initial commit June 2026). Internally nicknamed **"Slow Burn"** — the long-term, fundamentals-driven portfolio engine, split from a sibling **"Edge"** short-term trading product. Source archived at `raw/personal quant model.zip` (~185 MB, mostly cached yfinance/fiscal.ai data; the code itself is a tidy `qmodel/` Python package + Flask front end).

> [!update] The codebase split (2026-06-18)
> A newer archive (`raw/quant model.zip`) shows the project **divided into two repos** — *"this repo is now the Edge product only."* The long-term **Slow Burn** engine described on this page is preserved in `qmodel/` (and `qmodel_original/`), while the short-horizon trader is now its own product with a consumer front-end. Those are tracked on **[[The Edge (trading model)]]** and **[[Vision (Porter Intelligence)]]**. This page remains the canonical writeup of the original combined model / Slow Burn engine.

> [!important] Authorship
> Per Traveler: **the ideas, strategy, factor choices, and methodology are his — but he did not write the code; it was AI-generated.** This fits his documented [[Cursor (AI code editor)|vibe-coding]] workflow and the AI-as-scaffolding pattern in [[Tensions and Open Questions]]. Read the model as evidence of his quant *judgment and fluency*, not of hand-coding skill.

It is the strongest artifact in the wiki for the **conceptual** side of the [[UVA and the Quant Question|quant question]]: the design is real **statistical factor modeling** — cross-sectional scoring, regime switching, risk overlays, and factor attribution — not the verbal/fundamental stock-picking of his [[Investment Club]]. It is very likely the matured realization of the AI stock-ranking idea he scoped in chats as [[Sauron Investing]].

## What it does (the pipeline)
1. **Universe** — top ~1,000 US-listed common stocks by market cap (fiscal.ai), deliberately **including inactive/delisted names to reduce survivorship bias** (the exact critique he absorbed on the [[Honeycomb Portfolio]]).
2. **Factors** (`qmodel/equations.py`) — a library of fundamental and price factors, each tied to academic literature:
   - *Fundamental:* ROIC, diluted EPS, P/E, FCF margin & FCF yield, revenue growth (a **hard filter**), shareholder yield, size.
   - *Price/quant:* 12-1 momentum, **momentum acceleration** (Ardila-Sornette 2020), **52-week-high** (George-Hwang 2004), **residual/beta-neutral momentum** (Blitz-Huij-Martens 2011), **short-term reversal** (Jegadeesh 1990), Sharpe, Sortino, realized volatility.
3. **Scoring** (`qmodel/scoring.py`) — winsorize → **sector-neutral rank/z-score** → weighted composite. Defaults to **equal weight on purpose**, with a sharp note on overfitting: *"Tuned weights are the fast road to a backtest that looks great and works never."*
4. **Regime** (`qmodel/hmm_regime.py`) — a **Gaussian Hidden Markov Model** (`hmmlearn`) on S&P 500 returns labels bull/neutral/bear, which drives a **gold sleeve** (GLD at 8% / 14% / 25%) and an optional equity-exposure overlay.
5. **Portfolio & risk** — ~10 equities + the gold sleeve; weight schemes (equal / inverse-vol / min-variance / max-Sharpe), per-name caps, a **turnover hold-band**, and a **vol-targeting crash overlay** (Barroso-Santa-Clara 2015) that cut backtested max drawdown from ~-58% to ~-44%.
6. **Backtest** (`qmodel/backtest.py`) — an *honest* point-in-time test: fundamentals lagged 90 days to filing, scored only on data known at each monthly rebalance, reporting **Information Coefficient, IC-IR / t-stats, and decile monotonicity** vs S&P 500-TR / Nasdaq / gold. It even **self-flags a mild lookahead caveat** (the HMM is fit on the full sample) — the same intellectual honesty as his [[Physics IA]].
7. **Attribution** (`carhart_attribution.py`) — a **Carhart 4-factor** decomposition (Mkt-RF, SMB, HML, UMD) plus net-of-cost (10bps turnover) and survivorship sensitivity, asking the hard question: *once you control for the buyable momentum and size premia, does any real selection alpha survive?* This is graduate-level rigor.

## The app
A **Flask** site with a live **"equation editor"** (adjust every threshold/weight from the browser and re-run), per-stock vs-S&P charts, and an in-app **"explain the numbers" assistant powered by the Claude / Anthropic API** — tying his quant work to his heavy AI tooling ([[Cursor (AI code editor)]], [[Homework Hatch (startup)]]). Stack: pandas, numpy, scipy, scikit-learn, hmmlearn, yfinance, Flask, anthropic; deployable via gunicorn (Render/Railway).

## Why it matters
- **Updates the quant question — on the conceptual axis.** The doubt on [[UVA and the Quant Question]] was whether he could handle real quantitative rigor (he took math at SL). This shows he can *specify and reason about* that rigor — the right factors, attribution, regimes, and overfitting traps. But since he **directed rather than coded** it, it's evidence of quant **judgment and vocabulary**, not of implementation or proof-level math. The motivation question was already settled ([[Quantitative Finance]]); this strengthens the conceptual side while leaving the hands-on test (college proofs, building something himself) still ahead.
- **The design ethos is his fingerprint.** The anti-overfitting stance, survivorship-bias mitigation, and self-flagged lookahead caveat echo the instincts in his [[Honeycomb Portfolio]] critique and [[Physics IA]] — though with the code AI-generated, how much of the fine methodology was his call vs. the tool's default is genuinely unclear.

> [!warning] Security
> The archived repo includes a `.env` and full **git history that previously contained a hard-coded Fiscal.ai API key** (the code's own comment says to rotate it at fiscal.ai). Treat the zip's `.env` and history as sensitive; rotate the Fiscal.ai key (and any Anthropic key) if still live.

## See also
[[The Edge (trading model)]] · [[Vision (Porter Intelligence)]] · [[Quantitative Finance]] · [[UVA and the Quant Question]] · [[Investment Club]] · [[Honeycomb Portfolio]] · [[Sauron Investing]] · [[Homework Hatch (startup)]] · [[IB Math (SL)]] · [[Traveler Stansberry]]
