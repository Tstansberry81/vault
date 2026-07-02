---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2025-11-04
author: Traveler Stansberry
source_type: chat
tags: [chat, physics, math, history, japanese, homework]
status: active
---

# Mixed Homework - Japanese, Markov Chains, Chain Rule, Chinese Civil War, and HL Gravitation

A sprawling single-session homework grab-bag from November 2025 (GPT-5) that touches five of [[Traveler Stansberry]]'s subjects in one thread. It is a good cross-section of his day: drilling vocabulary for [[IB Japanese (SL)]], a curiosity tangent into Markov chains, mechanical [[IB Math (SL)]] differentiation, a [[IB History (HL)]] reading question on the Chinese Civil War, and a long, genuinely engaged stretch of [[IB Physics (HL)]] gravitation and circular motion.

## Japanese and a Markov-chain tangent
Opens with quick lookups — *kirai* (嫌い, dislike) vs. *suki* (好き, like), and *suwarimasu* (座る, to sit) — the kind of low-stakes [[IB Japanese (SL)]] drilling that recurs across his chats. He then pivots to "markov chain," gets a plain-English explanation (the Markov property, a weather transition table, PageRank/text-gen uses), and asks how to build one in Python — a small flash of his coding-curiosity side ([[Coding Club]], [[Homework Hatch (startup)]]).

## Chain rule and a hard geometry puzzle
A run of [[IB Math (SL)]] composite-function derivatives via the chain rule — g(f(x)) for cases like (3x+10)³ → 9(3x+10)², (7−2x)⁵, and (5x−1)⁻⁴ — which he says he already understands ("I know how to plug into the equations").

The more revealing math moment is a square-side-length puzzle (a small 19×7 right triangle on the base/right edge, with a segment from the square's center meeting the hypotenuse at 90°). Traveler insists on solving it **algebraically without vectors, coordinates, or slope formulas**, reporting he "ended up proving the Pythagorean identity on accident." The assistant fumbles repeatedly here — producing 361/13, 133/13, and 27.77 before landing on the correct **s = 361/6 ≈ 60.17** via the perpendicularity dot-product. The episode shows Traveler's preference for first-principles reasoning over machinery, and his ability to notice when the model is wrong and push back ("that is different from the previous solution").

## Chinese Civil War (History HL)
He asks for textbook-quote answers on the Warlord Period, the May Fourth Movement, and the causes of the Chinese Civil War. The assistant **refuses to fabricate quotes** without the source text, but gives the conceptual scaffolding: post-1911 warlord fragmentation breeding demand for a strong unifier (Chiang/Mao), the 1919 May Fourth anti-imperialist student movement (Shandong/Versailles) feeding Marxism and the 1921 CCP founding, and the GMD–CCP split after the 1927 Shanghai Massacre. Connects to his broader [[IB History (HL)]] coursework on 20th-century authoritarianism.

## HL2 gravitation and circular motion (the bulk)
The longest and most substantive section. Traveler works through an IB Physics HL gravitation problem set:
- escape-energy MCQ (GMm/R) and the definition of gravitational field strength as g = −dV/dr;
- the distinction between potential V (energy per unit mass) and potential energy U = mV;
- a full reference table of the fundamental equations (F, g, V, U, v_esc = √(2GM/r), v_orbit = √(GM/r), with v_esc = √2·v_orbit);
- the zero-field point between two stars, x = √M₁/(√M₁+√M₂)·R, read off a V-vs-x graph at ≈5.4×10⁹ m.

He explicitly rejects baby-tier practice problems — "I'm in HL 2 physics... I need some harder ones" but "no calculus stuff, it's just algebraic" — and gets reasoning-chained problems (rotating-planet escape boost, same-density escape-speed scaling v_esc ∝ R, binary-system period T = 2π√(R³/G(M₁+M₂)), vis-viva ellipse). He also confirms E_K = ½|E_P| holds **only for circular orbits**.

The "flying cow problem" turns out to be a **conical pendulum**: a mass tracing a horizontal circle on an angled string (radius 75 cm, vertical drop 45 cm). Traveler had wrongly set mv²/r = mg; the assistant corrects the classic trap (gravity is vertical, centripetal is horizontal — they're perpendicular), giving T·cosθ = mg, T·sinθ = mv²/r, tanθ = v²/rg, and T = 2π√(Lcosθ/g) ≈ 13.4 s. This leads into a tour of **tension**: conical-pendulum free-body diagrams, multiple-tension equilibrium, vertical stacked hanging masses (T₃=4g, T₂=7g, T₁=12g — "tension supports all mass below it"), the horizontal-acceleration analog (ΣF=ma), and **rotational kinetic energy** K = ½Iω² with moment of inertia I = Σm_ir_i² (and why I = mr² only holds for point masses and thin rings).

## What it shows
A snapshot of Traveler as a senior juggling all six IB subjects in one sitting, leaning hardest into [[IB Physics (HL)]]. He is an active, skeptical learner: he flags when his own method (mv²=mg) is physically wrong, refuses to accept the model's wrong geometry answers, and insists on algebraic/first-principles solutions over coordinate-and-vector machinery he hadn't yet learned.
