---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2025-12-17
author: Traveler Stansberry
source_type: chat
tags: [chat, math/trigonometry, math/calculus, coursework]
status: active
---

# Trig Equation Factoring, Sine vs Cosine Rule, and a First Integration Primer

A long, image-heavy [[IB Math (SL)]] homework session (Dec 2025) in which Traveler works through a chain of trigonometry, non-right triangle, and intro-calculus problems by photographing textbook questions and asking for worked solutions. It captures him mid-unit, moving from trig identities into differentiation and finally asking for a from-scratch explanation of integration — a snapshot of the SL course sequence and of how he learns: solve, get stuck, ask *why*, then ask for the general rule.

## What he worked through

- **Trig equation factoring.** Solving `cos2x + cosx = 1 + sin2x − sinx` on `[−π,π]` by reducing to `(cosx+sinx)(1−2sinx)=0`, giving `x ∈ {−π/4, 3π/4, π/6, 5π/6}`. The double-angle identities (`cos2x−1=−2sin²x`, `sin2x=2sinxcosx`) are the load-bearing trick.
- **Graphing form of trig functions** — `y=a·sin(b(x−c))+d`, with amplitude `|a|`, period `2π/|b|` (or `π/|b|` for tan), phase shift, and midline. Applied to a Ferris-wheel / rotating-wheel harmonic-motion word problem: modeling height as `H(t)=3cos(πt/2)+4` and solving for when point X first enters the water (`≈1.46 s`).
- **Sine rule vs cosine rule** — he explicitly asked "how do you know if it's cosine rule or sine rule," and got the decision heuristic: **opposite angle–side pair → sine rule; included angle (SAS) or three sides (SSS) → cosine rule.** Applied to several triangle area/length problems, including the **ambiguous SSA case** yielding two possible lengths.
- **A 3D-looking angle-of-depression problem** (cliff, two ships "Black Pearl" and "Hispaniola"). Traveler got 126 m and 130 m by flattening it to 1D; the chat diagnosed his error — he'd applied the sine rule across two *different* triangles, treating the 100 m cliff height as a side of triangle POH where it doesn't live. Correct answer `PH ≈ 209 m` via right-triangle trig then cosine rule. A clean example of him surfacing and correcting a real misconception rather than just copying an answer.
- **Differentiation drills** — repeated derivatives of `e^(−3x)` (pattern `(−3)ⁿe^(−3x)`), quotient rule on `lnx/x` (max at `(e, 1/e)`), chain rule on `sin(3x)`, product rule, and the full natural-log derivative toolkit including logarithmic differentiation of `xˣ`. Then a multi-layer chain-rule problem `cos(2π sinx)` and solving its derivative `=0` over `[0,π]`.
- **Circle/sector geometry in radians** — `A=πr²`, sector `A=½r²θ`, arc length `s=rθ`, with emphasis that these only work in radians.
- **Conceptual integration primer** — he closed by asking "explain integration to me" and "explain the antiderivative," getting first-principles explanations (Riemann-sum intuition, indefinite vs definite integrals, the `+C`, rates→totals). This marks his transition point into the SL calculus unit.

## What it shows

This is bread-and-butter [[IB Math (SL)]] coursework, but the texture is revealing. Traveler is a strong but pragmatic math student: he asks for the *general rule* after each specific problem ("trig graphing form," "natural log derivative rules," "how do you know if it's sine or cosine rule"), trying to compress procedure into reusable heuristics rather than memorize cases. His angle-of-depression mistake (and the follow-up "how'd you get 5π/6") shows him genuinely debugging his own reasoning — consistent with the [[Intellectual Profile]] of someone who wants the underlying structure, not just the boxed answer. The math here also underpins his quantitative ambitions noted in [[UVA and the Quant Question]] and the calculus he leans on across [[IB Physics (HL)]].
