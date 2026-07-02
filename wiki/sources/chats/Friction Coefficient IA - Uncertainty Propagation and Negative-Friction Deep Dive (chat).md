---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2026-01-28
author: Traveler Stansberry
source_type: chat
tags: [chat, physics, ib-physics, internal-assessment, uncertainty, friction]
status: active
---

# Friction Coefficient IA - Uncertainty Propagation and Negative-Friction Deep Dive

A long (278 KB) [[IB Physics (HL)]] working session on Traveler's **Internal Assessment** measuring the coefficient of kinetic friction of a Vernier cart sliding down an inclined plane. The experiment varied the incline angle (3°, 6°, 9°, 12°, 15° — set by stacking physics textbooks), ran 3 trials per angle, used a cart of mass ~0.26 kg, and derived acceleration from the slope of the Vernier velocity-vs-time data. This is the deeper, calculation-heavy companion to [[Friction Coefficient IA - Inclined-Plane Excel Formula and Negative-Mu Breakdown (chat)|Friction Coefficient IA - Inclined-Plane Excel Formula and Negative-Mu Breakdown (chat)]] and follows the topic-selection chat [[Physics IA Topic Selection - Friction Coefficient and Rotational Energy (chat)|Physics IA Topic Selection - Friction Coefficient and Rotational Energy (chat)]].

## The core problem: negative friction and non-constant μ
Traveler opened by asking why his spreadsheet produced **negative frictional force values** and why μ wasn't constant across angles. The diagnosis: using μ = (g·sinθ − a)/(g·cosθ), whenever measured acceleration exceeds g·sinθ the numerator goes negative — physically impossible, so it signals that **experimental uncertainty overpowers the signal at low angles** where g·sinθ is tiny. The 15° and 12° trials looked sane; 9°, 6°, 3° "went feral." The pedagogical framing that stuck: *"your spreadsheet is a confession booth"* — every un-modeled error (air resistance, track imperfection, release bias, rotational losses) gets dumped into μ because that's the only place the equation lets error hide. The IA-friendly move is to **frame this as analysis, not failure**: report that error magnification at small angles makes the ideal F = μN model break down.

## What he actually built
- **Data restructuring** in Excel: averages of friction force per angle, separation of "real" (positive) friction values from the noise-corrupted negative ones, and matching uncertainty values — with the plan to show multiple graphs (all values vs. averages-only vs. positive-only) to justify his data choices to the examiner.
- A decision to **plot only positive average friction values** for the graph that "counts," while discussing the discarded negatives as evidence of uncertainty dominance.
- Excel formula debugging: his μ formula was returning `FALSE`; he needed a corrected column formula for F_f = mg·sinθ − ma given his existing variable columns.

## The uncertainty obsession
The bulk of the chat is Traveler grinding through **uncertainty propagation** because his teacher wanted relative uncertainty carried through the whole calculation chain (angle → mass → acceleration → force), not a lazy "±0.1 on everything." He repeatedly reset the explanation ("explain the whole thing again," "where does the square root of 3 come in," "what does Δf even mean anymore") until the method clicked. Key threads:
- Acceleration uncertainty from repeats via **range/2**, and the physical meaning of that as a spread estimate.
- Mean-acceleration uncertainty and the standard-error / √n reasoning (and his teacher's preference for a single **broad uncertainty term** rather than per-point error bars).
- Angle uncertainty from the textbook-stacking method, and mass uncertainty (~0.01 in grams).
- Propagating relative uncertainties through products and quotients to get force uncertainty.

This shows Traveler's characteristic learning style: relentless re-questioning until he can *explain the equation himself* ("I'ma need to explain it in my IA"), distrust of black-box formulas, and tight coupling to his teacher's specific grading expectations and Logger Pro workflow. It also reflects his [[IB History (HL)]]-adjacent and [[IB Math (SL)]] comfort — the session closes with an unrelated math tangent (the indefinite integral of the 9th root of x⁵). A brief detour also covered the **IB Diploma pass rate**, fitting his recurring status-anxiety about [[Academic Record|grades and odds]].

## Connections
Reinforces his [[Extracurriculars and Achievements|IB Diploma candidate]] workload at [[St. Paul's School]] and the empirical-skeptic streak in his [[Intellectual Profile]]: he treats a misbehaving dataset not as a failed experiment but as physics "tattling on his assumptions."
