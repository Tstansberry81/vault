---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2025-10-27
author: Traveler Stansberry
source_type: chat
tags: [chat, physics, gravitation, energy]
status: active
---

# Gravitational Potential Energy and Work Done by Gravity

A conceptual [[IB Physics (HL)]] tutoring session (ChatGPT, GPT-5, 2025-10-27) in which Traveler works to genuinely *understand*, not just memorize, why gravitational potential energy carries a negative sign and how to compute the work gravity does on a satellite. The chat is notable for his insistence on the "why": he repeatedly pushes back ("explain more thoroughly, i still dont get it… not the why") and asks for plain-English and then calculus-free derivations. This reflects his characteristic conceptual stubbornness — he wants the first-principles logic, not the formula handed down.

## Key physics covered
- **Why U is negative.** Potential energy is a bookkeeping function whose gradient gives the force ($\mathbf{F} = -\nabla U$); only differences matter, so a reference must be chosen. The standard convention sets $U(\infty)=0$. Because gravity is attractive, $U(r) = -\dfrac{GMm}{r}$ — bound systems sit in a potential well *below* zero, and the negative sign means "you owe energy to escape."
- **Bound vs. unbound.** With $E = K + U = \tfrac{1}{2}mv^2 - \dfrac{GMm}{r}$: $E<0$ is bound, $E=0$ is the escape threshold, yielding escape velocity $v=\sqrt{2GM/r}$.
- **Reconciling with $mgh$.** Near Earth's surface, $\Delta U = U(R_E+h)-U(R_E)\approx mgh$. The familiar $mgh$ is a *difference between two negative values*, not an absolute potential — the higher position is just "less negative."
- **Work done by gravity.** Gravity is conservative, so work depends only on start/end radii: $W_{\text{grav}} = -\Delta U = GMm\left(\dfrac{1}{r_f}-\dfrac{1}{r_i}\right)$. Moving inward → positive work (gravity speeds the object up); moving outward → negative work. Net work over one full orbit is zero.
- **Sign of work / who does it.** Lowering a mass slowly means the *external agent* does negative work while gravity does positive work — the confusion he flags is resolved by tracking direction of force vs. displacement.

He asked for a calculus-free version and got the algebraic route ($W=-(U_f-U_i)$) with worked numeric examples (e.g. ~$5.7\times10^{10}$ J for a satellite dropping in, ~$-1.96\times10^{10}$ J for one moving outward).

## What it shows
This is core HL gravitation content (Newtonian fields, energy, escape velocity) — the same energy-and-work reasoning that recurs across his physics work like [[Circular Motion Derivation - Centripetal Acceleration, Torque, and Moment of Inertia (chat)|Circular Motion Derivation - Centripetal Acceleration, Torque, and Moment of Inertia]] and [[Physics Work and Energy then Interwar Nationalism (chat)|Physics Work and Energy then Interwar Nationalism]]. The session is a clean window into his learning style: he treats the AI as a tutor to interrogate until the conceptual logic clicks, escalating from analogy to first-principles integral to plain English.
