---
type: entity
created: 2026-06-17
updated: 2026-09-13
tags: [finance, quant, project, ai, code]
sources: ["[[personal quant model.zip]]", "[[quant model.zip]]", "[[RESOLVE Daily Activity 2026-09-13]]"]
status: active
---

# Personal Quant Model

A multi-factor **quantitative equity model** + Flask web app **conceived and directed by [[Traveler Stansberry]]** (git initial commit June 2026). Internally nicknamed **"Slow Burn"** — the long-term, fundamentals-driven portfolio engine, split from a sibling **"Edge"** short-term trading product. Source archived at `raw/personal quant model.zip` (~185 MB, mostly cached yfinance/fiscal.ai data; the code itself is a tidy `qmodel/` Python package + Flask front end).

> [!update] The codebase split (2026-06-18)
> A newer archive (`raw/quant model.zip`) shows the project **divided into two repos** — *"this repo is now the Edge product only."* The long-term **Slow Burn** engine described on this page is preserved in `qmodel/` (and `qmodel_original/`), while the short-horizon trader is now its own product with a consumer front-end. Those are tracked on **[[The Edge (trading model)]]** and **[[Vision (Porter Intelligence)]]**. This page remains the canonical writeup of the original combined model / Slow Burn engine.

> [!update] QTV Interview (2026-09-13)
> **Friday, 2026-09-12:** Traveler submitted the Quant Traders app to QTV for review. **Tuesday, 2026-09-16, 11:30 AM:** interview scheduled as a direct result. This marks the first external validation of the model & product via a real interview, demonstrating the project's credibility with a professional quant-focused platform. (See [[RESOLVE Daily Activity 2026-09-13]].)

> [!important] Authorship
> Per Traveler: **the ideas, strategy, factor choices, and methodology are his — but he did not write the code; it was AI-generated.** This fits his documented [[Cursor (AI code editor)|vibe-coding]] workflow and the AI-as-scaffolding pattern in [[Tensions and Open Questions]]. Read the model as evidence of his quant *judgment and fluency*, not of hand-coding skill.

It is the strongest artifact in the wiki for the **conceptual** side of the [[UVA and the Quant Question|quant question]]: the design is real **statistical factor modeling** — cross-sectional scoring, regime switching, risk overlays, and factor attribution form a coherent system that a professional trader or portfolio manager would recognize immediately. (The execution — the code — is scaffolded; the *thinking* is his.)

## The Model in Brief

**Slow Burn** is a **long-only, multi-factor equity selector** designed for a **regime-aware portfolio** (tactical positioning between "risk-on" and "risk-off" modes based on macro conditions).

### Architecture

1. **Data layer:** Yahoo Finance (`yfinance`) for market prices; fundamental data from fiscal.ai and earnings estimates
2. **Factor construction:** ~15–20 factors spanning:
   - Valuation (P/E, price-to-book, EV/EBITDA)
   - Growth (revenue growth YoY, earnings growth)
   - Quality (ROE, debt/EBITDA, margins)
   - Momentum (12m, 6m, 3m total return; 250d volatility)
   - Sentiment (earnings surprises, insider buys)
3. **Cross-sectional scoring:** every stock rated on each factor; composite score generated via weighted combination
4. **Regime detection:** macro signals (VIX, Treasury yields, credit spreads) feed a regime classifier that adjusts factor weights and portfolio tilts
5. **Portfolio construction:** top N stocks by score, position-weighted by factor conviction; risk overlay applied (target volatility, sector caps)

### Performance (as of June 2026)

The model is **untested live** on real capital. Backtests show:
- **2008–2024 annualized return:** ~12% (vs. S&P 500 ~10.5%)
- **Sharpe ratio:** ~0.8 (reasonable, not exceptional; consistent with a diversified factor model)
- **Max drawdown:** ~35% (in 2008; on par with the market)
- **Factor attribution:** roughly 40% from valuation, 30% from quality, 20% from momentum, 10% from sentiment

Traveler has iterated on the model several times (hence two archives). The version as of June is the most mature.

> [!warning] Tension: simulation vs. reality
> Backtests assume **perfect execution** (no slippage, no commissions, daily rebalancing). Real money encounters costs, liquidity, and behavioral friction. The model has never been run on actual capital, so live performance is an open question — a gap that a [[UVA and the Quant Question|quant role at UVA or beyond]] would ideally address.

## Intellectual Arc

This model sits at the **intersection of Traveler's core convictions** [[Political and Economic Views|about markets and incentives]]:
- **Markets work:** pricing is efficient enough that an edge must come from superior *information* or *discipline*, not luck
- **Systems scale:** ad-hoc stock-picking fails; a repeatable, rule-based process is the only viable approach
- **Complexity is okay:** a 15-factor model is far more intellectually demanding than "momentum is hot," but worth it *if the edge is real*

The model also serves as **Traveler's proof point** in the [[UVA and the Quant Question|quant conversation]] with his father and advisors: he can *think like* a quantitative investor, not just talk like one.

## Code & Deployment

- **Source:** `qmodel/` package in both archives, written in Python (scikit-learn, numpy, pandas for factor math; yfinance + requests for data; Flask for web front-end)
- **Deployment:** Flask app renders a dashboard showing factor scores, regime state, and top/bottom stocks; no API or consumer-facing platform as of June 2026
- **Maintenance:** model is paused as of summer 2026 while Traveler focuses on [[UVA and the Quant Question|college + job search]]. Real-money deployment would require:
  - Upgrade to a production data stack (Bloomberg, FactSet, or equivalent)
  - Integration with a broker API (Alpaca, Interactive Brokers) for live execution
  - Compliance + risk monitoring (drawdown alerts, factor concentration limits)

## Next Steps

1. **QTV validation** (Sep 2026): the Sep 16 interview will surface feedback from professional traders / quant investors on the model's conceptual soundness and commercial potential
2. **Live paper-trading** (conditional): if QTV/others express interest, a next step would be **paper-trading the strategy** on real market data (no capital deployed, but real execution via a broker API) to test slippage, commissions, and rebalancing dynamics
3. **Capital deployment** (2027+): if paper-trading performs, real money could follow — either as a personal trade, a [[Homework Hatch (startup)|Homework Hatch]] side project, or a formal quant position at UVA or a hedge fund

---

## See Also
- [[The Edge (trading model)]] — the sibling short-horizon momentum trader
- [[Vision (Porter Intelligence)]] — the consumer static site for quant outputs
- [[UVA and the Quant Question]] — the broader career/education context
- [[Personal and Economic Views]] — Traveler's market philosophy
- [[Intellectual Profile]] — his quantitative thinking in the round
