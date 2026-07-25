---
type: analysis
created: 2026-07-25
updated: 2026-07-25
tags: [quant, the-edge, backtest, survivorship, risk]
sources: [raw/quant model (survivorship_stress.py, edge_ic.py, fetch_membership.py)]
status: active
---

# The Edge — Survivorship Bias, Measured

First honest quantification of the survivorship handicap in [[The Edge]]'s
backtest (2026-07-25, product config: 42-day clock / 10 names / 75% growth mix,
net of 10bps).

## Method
Free true point-in-time S&P 500 membership (1996→present, ~2,700 snapshots,
github.com/fja05680/sp500; `fetch_membership.py`) wired into the Edge's
pluggable PIT layer, plus a new delisting-stress knob (`EDGE_DELIST_HAIRCUT`)
that holds dying names through their last trade instead of silently dropping
them. Suite: `survivorship_stress.py`; signal quality: `edge_ic.py`.

## Results (20Y, CAGR / excess vs S&P)

| Variant | CAGR | Excess |
|---|---|---|
| A. Proxy top-1000 (product) | 19.9% | +8.5% |
| B. Proxy top-500 (size control) | 18.2% | +6.9% |
| C. True-PIT S&P 500 (priced subset) | 13.6% | +2.2% |
| D/E. Delist truncate / −30% haircut | 19.9% | +8.5% (unchanged) |

## What it means
- **A−B (~1.6%/yr)** — size/breadth effect: mid-caps carry part of the edge.
- **B−C (~4.7%/yr)** — universe composition at matched size class. Part is
  survivorship (C's early years are only ~41–60% priced, so even C flatters),
  part is the *index-inclusion effect*: the mcap proxy legitimately holds
  tomorrow's index entrants during their run-up, which a live trader of this
  strategy would too. The two cannot be separated without real delisted data.
- **D/E = A exactly** — the drop-rule is *not* where the bias lives: all 111
  inactive names in the data died 2024+, so there is zero delisted-return data
  before 2024. The bias is in *missing* dead names, unfixable in code.
- **Honest floor:** a large-cap-only, true-membership Edge still beats the S&P
  by ~+2%/yr over 20Y (Sharpe 0.86 vs 0.96 proxy). The product's +8.5% is an
  upper bound; truth for the tradeable top-1000 strategy lies between.
- **Signal quality:** broad cross-sectional IC of acceleration is ~0 — the
  Edge is a pure top-tail strategy, not a rank factor. The tail statistic
  (top-10 by accel vs universe mean forward return): **+7.34%/rebalance
  (t=1.9) on the proxy top-1000, but only +0.48%/reb (t=0.9, 50% hit rate)
  on true-PIT S&P 500.** The raw signal's edge is concentrated in mid-caps —
  exactly where missing-dead-names bias is worst — so the proxy backtest
  deserves real suspicion and the full-pipeline PIT result (+2.2%/yr, which
  adds growth mix / corr cap / regime on top of the raw signal) is the
  defensible number.

## Consequences
1. The **forward paper-trading record** ([[The Edge]] tracker) is the only
   fully bias-proof evidence — priority is keeping it accruing and making the
   live book truly current (today it lags one hold period).
2. Real de-biasing needs a delisted-securities dataset (Norgate ~$270/yr);
   the adapter layer is already built for it.
3. Marketing numbers for [[Vision (Porter Intelligence)]] should quote the 20Y
   figure with the survivorship caveat, or the true-PIT +2.2% as the floor.
