---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2026-03-31
author: Traveler Stansberry
source_type: chat
tags: [chat, math/calculus, physics/electromagnetism]
status: active
---

# Antiderivatives, Solenoid Field Derivation, and a Drift into Double Integrals

A rapid-fire homework session that jumps from [[IB Math (SL)]] calculus into [[IB Physics (HL)]] electromagnetism and then overshoots into university-level multivariable calculus — the kind of curiosity-driven drift that recurs across Traveler's chats (cf. the [[UVA and the Quant Question]] and his stated [[Intellectual Interests]]).

## Calculus (IB Math SL)
- Antiderivatives of `-2sin x` (→ `2cos x + C`) and `sin(2x)` (→ `-½cos(2x) + C`), with the chain-rule "extra 2" called out as the usual trap.
- For `f(x) = ln(xe^x + 1) - x⁴`: x-intercepts at `(0,0)` and `≈(1.099, 0)`, and a local max at `≈(0.709, 0.640)` — solved numerically (GDC territory, no clean closed form), the calculator-active style IB expects.
- **Area** bounded by the curve, the x-axis, and `x = 2`. The assistant first gave a wrong `≈1.139`, treating the region too small.

> [!note] Traveler caught the model's error
> He pushed back: "i got 4.6 i think youre wrong?" — and he was right. The corrected area is `≈4.611`, because the curve drops to `f(2) ≈ -13.24`, making the negative region large. A small example of him not trusting the AI blindly and trusting his own work, consistent with his [[Core Convictions]] as a skeptic.

## Physics (IB Physics HL)
- **Potential difference**: `V = W/Q` (1 volt = 1 J/C), the hill analogy, EMF vs. potential vs. potential difference, and `V = IR` (Ohm's Law).
- **Solenoid field**: why `B` is uniform inside (symmetry + superposition + the long-solenoid approximation, field ≈ 0 outside), then the full Ampère's Law derivation `∮B·dl = μ₀I_enc` → `B = μ₀nI`, using a rectangular Amperian loop. Notes the IB "magic words" examiners want: long solenoid, parallel/equally-spaced field lines, negligible external field.

## The drift beyond syllabus
Seeing the closed-loop integral sign `∮` prompted a chain of off-syllabus questions: what `∮` means (closed line integral vs. `∫`), whether it's for "spherical stuff" (no — that's surface/volume integrals, `∯` for Gauss's Law), and finally **how double integrals work** (`∬f(x,y)dA` as volume under a surface, iterated inner-then-outer, non-rectangular regions with variable limits). This reaches past [[IB Math (SL)]] into the multivariable calculus he'll meet pursuing a math minor at UVA.

The whole exchange shows Traveler using ChatGPT as a fast tutor across two HL/SL subjects in one sitting, verifying answers against his own, and following symbol curiosity well beyond what the test requires.
