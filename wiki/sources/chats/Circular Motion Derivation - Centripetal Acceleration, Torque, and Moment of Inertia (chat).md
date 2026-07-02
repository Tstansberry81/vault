---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2025-10-17
author: Traveler Stansberry
source_type: chat
tags: [chat, physics, rotational-motion, derivation]
status: active
---

# Circular Motion Derivation - Centripetal Acceleration, Torque, and Moment of Inertia

A focused [[IB Physics (HL)]] tutoring session (GPT-5, Oct 2025) in which Traveler asks ChatGPT to "explain circular motion to me very intuitively and derive each equation (torque, uniform angular acceleration, inertia, etc)." Notably, he sends a sharpened second prompt insisting that by "derive" he means **explain from graphs or from a physical situation**, and flags himself as "a complete beginner with only knowledge of forces and friction and momentum." This is characteristic of his study style across the [[IB Physics (HL)]] chats: he refuses rote formula-memorization and demands first-principles intuition before accepting an equation.

## What was covered
The model builds the full rotational-mechanics toolkit from scratch:
- **Centripetal acceleration** — derived geometrically from two tangent velocity vectors separated by Δθ, giving |Δv| = vΔθ, then a_c = vω = v²/r (using v = ωr). Center-seeking, not a new force.
- **Centripetal force** — F = mv²/r = mω²r, just Newton's 2nd law applied inward (string tension, road friction, or gravity for orbits).
- **Linear → angular analogues** — the "holy table" mapping x↔θ, v↔ω, a↔α, m↔I, p↔L, F=ma ↔ τ=Iα, ½mv² ↔ ½Iω².
- **Torque** — τ = rF sin θ, motivated by the door-handle-vs-hinge intuition, and re-derived from work: W = F(rΔθ) = τΔθ ⟹ τ = Fr.
- **τ = Iα derived** — summing per-particle torques: F_i = m_i a_i, a_i = r_iα, so τ_i = m_i r_i²α, and τ_net = α Σm_i r_i² = Iα.
- **Moment of inertia** — I = Σm_i r_i² (or ∫r² dm), with standard results for point mass (mr²), solid disk (½mr²), hoop (mr²), rod about center (1/12 mL²).
- **Uniform angular acceleration** — the three rotational kinematics equations mirroring linear motion, with the note that ω(t) is a straight line of slope α and area-under-curve gives θ.
- **Angular momentum** L = Iω and conservation (I₁ω₁ = I₂ω₂, the ice-skater effect), plus rotational KE = ½Iω².

## What it shows
This is straightforward exam-prep for the rotational/circular-motion unit, but it documents his learning preference precisely: connect-the-dominos derivation over memorization, graphs and everyday situations (spinning ball on a string, door handle, ice skater) over abstract symbol-pushing. It sits alongside his momentum-conservation problem sets ([[IB Physics (HL)]]) as part of the HL mechanics sequence. The session is entirely conceptual — no problem-solving or lab data — and produced no images despite the model repeatedly offering a labeled vector diagram.
