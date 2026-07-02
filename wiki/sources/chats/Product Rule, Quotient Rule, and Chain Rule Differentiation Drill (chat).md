---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2025-11-21
author: Traveler Stansberry
source_type: chat
tags: [chat, math/calculus, coursework/math]
status: active
---

# Product Rule, Quotient Rule, and Chain Rule Differentiation Drill

A [[IB Math (SL)]] calculus homework session in which Traveler worked through a batch of differentiation problems, debugging a specific recurring error in his application of the **product rule**. The chat's persona-model answers in an abrasive, mock-insulting tone ("Kid, breathe", "Fine, gremlin"), but the underlying math instruction is correct and clean.

## The core confusion
Traveler's opening problem reveals exactly where he was getting stuck: when differentiating a product `y = u·v` where `v` is itself a composite function, he kept multiplying `u` into *every piece* of the chain-rule expansion of `v'`, rather than multiplying `u` by the finished `v'` once. The clarification — product rule applies only at the top level (`y' = u'v + uv'`), and inside `v'` you ignore `u` entirely and just use the chain rule — was the conceptual fix he needed. This is a typical intermediate-calculus slip, not a gap in the rules themselves.

## Problems covered
- `y = 4x(2x+1)^3` — product + chain rule, factored to `4(2x+1)^2(8x+1)`.
- `y = x²√(3−x)` — product rule with a radical rewritten as a `1/2` power.
- `g(x) = √(x+5)/x²` — done both as a product (rewriting `1/x²` as `x^-2`) and again with the **quotient rule** when he asked for it explicitly.
- `d/dx[sin x cos x] = cos²x − sin²x = cos(2x)` — and the related double-angle identities (`cos(2x) = cos²x − sin²x = 2cos²x − 1 = 1 − 2sin²x`).
- `d/dx[½sin(2x)] = cos(2x)` — constant-multiple + chain rule, the ½ and 2 cancelling.
- `y = ((x+3x)²)^4` — solved both by simplifying first (`= 65536x^8`, `y' = 524288x^7`) and, on request, by pure nested chain rule without expansion.
- `y = cos x/(sin x + 2)` — quotient rule, simplified via the Pythagorean identity to `(−1 − 2sin x)/(sin x + 2)²`.

## What it shows
A snapshot of where Traveler was in the [[IB Math (SL)]] differentiation unit in late 2025: comfortable with mechanics but tripping on the *scope* of each rule, and conscientious enough to ask for the same problem solved multiple ways (product vs. quotient, simplified vs. unexpanded chain rule) to see the equivalence. The trig double-angle work overlaps with his broader trig-identity practice seen in related chats. Low-stakes coursework grinding rather than conceptual exploration.
