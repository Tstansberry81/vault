---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2026-04-01
author: Traveler Stansberry
source_type: chat
tags: [chat, physics, electromagnetism]
status: active
---

# Electric Field Direction and Electron Deflection - HL Physics Fields Set

A homework-help session for [[IB Physics (HL)]] in which Traveler photographs four exam-style questions on charged particles in electric and magnetic fields and asks ChatGPT (GPT-5) to "answer and explain with steps." The chat is notable less for the answers themselves than for the two conceptual follow-ups he raises — which expose exactly where the field-vs-force distinction and vector subtraction were tripping him up.

## What the problems covered
- **Q10 — electron between charged plates.** Field strength \(E = V/d = 30/0.040 = 750\ \text{V m}^{-1}\); force \(F = qE\) gives acceleration \(\approx 1.3\times10^{14}\ \text{m s}^{-2}\) directed *upward* (opposite the field, since the electron is negative). Projectile-style decomposition into constant horizontal velocity and uniform vertical acceleration yields a horizontal travel of \(\approx 0.16\ \text{m}\). Part (c) is a velocity-selector: setting \(F_E = F_B\) gives \(B = E/v \approx 8.0\times10^{-5}\ \text{T}\).
- **Q11 — electron accelerated then deflected in a magnetic field.** \(eV = \tfrac12 mv^2\) recovers the \(9.4\times10^6\ \text{m s}^{-1}\) speed; \(qvB = mv^2/r\) gives \(r \approx 4.5\times10^{-4}\ \text{m}\); a quarter-circle arc gives time-in-field \(\approx 7.5\times10^{-11}\ \text{s}\). Then a momentum/impulse sub-problem: two perpendicular equal-magnitude momenta combine via Pythagoras to \(\Delta p \approx 1.2\times10^{-23}\ \text{N s}$, and \(F_{avg} = \Delta p/\Delta t \approx 1.6\times10^{-13}\ \text{N}\).
- **Q11(c) — electromagnetic induction.** A loop moving toward a current-carrying wire: rising flux induces an emf (Faraday) and an opposing current (Lenz), so external work is needed to keep constant speed, and that work dissipates as heat in the loop's resistance.

## What it reveals
The two interjected questions are the tell. First: "for q10 how do you know the direction of the electric field" — answered by the rule that fields run **positive → negative** as marked on the plate labels, kept strictly separate from the *force* direction on a negative charge. Second: "does electric energy equal voltage times charge" — confirming \(E = qV\) and untangling it from the time-dependent \(E = IVt\). Finally he photographs his own attempted momentum-change diagram ("like this? idk how you explained the tip to tail method tho") and gets corrected: \(\Delta\vec p = \vec p_f - \vec p_i\) is **tip-to-tip** (subtraction), not the tail-to-tip addition he had drawn. This is a recurring pattern across his [[IB Physics (HL)]] chats — strong at plugging into formulas, but checking the conceptual scaffolding (field vs. force, vector subtraction) before a test. The session ties together the electrostatics, magnetic deflection, and induction strands the HL course bundles into a single fields unit, alongside his other electricity work like [[Permittivity, Lightning Discharge, and Circuit Derivations - HL Physics Electricity (chat)]] and [[Series vs Parallel Circuits and Electric Field MCQs (chat)]].
