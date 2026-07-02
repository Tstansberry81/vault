---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2025-09-01
author: Traveler Stansberry
source_type: chat
tags: [chat, physics, lab, momentum]
status: active
---

# Vernier Cart Explosion Lab - Momentum Conservation

A [[IB Physics (HL)]] lab-analysis session (GPT-5, Sept 2025) in which Traveler works through a **Vernier/Go Direct "exploding carts" lab** measuring conservation of momentum. Two carts (grey and teal) start together at rest, a spring plunger pushes them apart, and their masses and travel distances are recorded across trials. The goal is to show that an internal explosion produces equal and opposite impulses, leaving total momentum constant.

The chat opens with a diagnostic kit for "cursed" data (symptom → cause → fix: unlevel track, sticky wheels, wrong masses, missing the speed peak, Bluetooth dropouts) but pivots into the core conceptual work. Traveler is clearly trying to *understand and explain* the physics, not just get numbers — he repeatedly asks for derivations and for plain-English, calculus-free phrasings he can drop into a lab report, noting "im a 17 year old physics student with no calculus knowledge and i barely understand this."

## Key physics derived
- The **two king equations**: definition of momentum \(p = mv\), and conservation \(\sum p_{before} = \sum p_{after}\).
- Both derived from the **center-of-mass argument**: with no external horizontal force and both carts starting at the origin, \(m_1x_1 + m_2x_2 = 0\), so the distance ratio equals the inverse mass ratio \(\frac{|x_1|}{|x_2|} = \frac{m_2}{m_1}\). Differentiating gives \(m_1v_1 + m_2v_2 = 0\) — conservation falls straight out, and the conserved additive "piece" is \(mv\), which is *why* momentum is defined that way.
- The **impulse-momentum theorem** \(\vec{J} = \Delta\vec{p}\), derived by integrating Newton's second law over the collision time, plus the airbag/soft-landing intuition (longer \(\Delta t\) → smaller average force).

## His actual data
He pastes a trials table and two fitted graphs. Defining MR = grey/teal mass ratio and DR = teal/grey distance ratio (distance ∝ velocity for equal coast time), conservation predicts **DR = 1/MR**.
- Inverse fit: \(DR = A/MR\) with \(A \approx 0.95\), correlation 0.97.
- Linear fit (DR vs 1/MR): slope 0.80, intercept 0.196, correlation 0.988.

The session ends with him probing what the constant **A** means: ideally A = 1; his 0.95 shows the lighter cart "under-performed" — it traveled slightly less than predicted because lighter carts lose proportionally more speed to friction/drag, plus track tilt and uneven plunger release. The "see-saw effect": heavy cart barely moves, light cart zips farther to balance momentum.

## What it shows
A window into Traveler's hands-on [[IB Physics (HL)]] coursework and his learning style — he leans on the AI as a tutor to derive equations from first principles and then convert them into accessible report prose, asking follow-up after follow-up ("so what does the A value tell us", "what does this mean about the motion of the carts") until the concept is solid. Methodical, error-analysis-minded, and focused on being able to *explain* rather than just report. Consistent with his quantitative bent toward [[UVA and the Quant Question]] finance and math.
