---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2026-04-15
author: Traveler Stansberry
source_type: chat
tags: [chat, physics, math]
status: active
---

# Phase Angle, Pendulum SHM, and a Geometric Series Solve

A tightly focused [[IB Physics (HL)]] / [[IB Math (SL)]] session anchored on **phase angle**. [[Traveler Stansberry]] asks for the concept, gets the full treatment (\(x(t) = A\sin(\omega t + \phi)\), phase as position in a cycle, phase difference for interference, \(\phi = \omega\Delta t\), AC-circuit lead/lag), then asks for it "simpler" and gets the core intuition: **phase angle is just the angle of a point spinning around a circle, projected as a wave**. He probes whether these are genuinely unit-circle angles — yes, with \(\omega t + \phi\) being the same angle, just time-driven rather than drawn. The circle-to-sine-wave model here is the same one he chased in his [[Chasing ChatGPT's Interactive Animations - Angular Velocity and a Feature Rollout (chat)|interactive-animations chat]] from the same day.

He nails it down with a **pendulum example**: for small-angle SHM, \(\theta(t) = \theta_0\cos(\omega t + \phi)\) with \(\omega = \sqrt{g/L}\), and the three release cases — from the side (\(\phi = 0\)), pushed through center (\(\phi = \pi/2\)), opposite side (\(\phi = \pi\)). What this reveals is Traveler's preference for collapsing scary notation into a single physical picture before trusting the math — a habit that recurs across his SHM and wave prep.

The chat then turns to a string of [[IB Math (SL)]] series problems: the alternating sum \(1-2+3-4+\dots\) to 100 terms (pair into 50 × −1 = −50), an arithmetic series \(7, 12.5, 18, \dots, 106\) (\(n=19\), \(S = 1073.5\)), and an infinite geometric series \(\sum (4x/3)^{k-1} = 5/2\) solved via \(S = 1/(1-r)\) to \(x = 9/20\), with the convergence check \(|r| = 3/5 < 1\). These geometric/arithmetic-series mechanics feed directly into his [[IB Math SL Paper 1 and 2 Walkthrough - Binomial, Series, and TI-84 Drills (chat)|series and binomial drills]] and overlap conceptually with the [[Kanji Fill-In Worksheet, Work-Energy Theorem, and Compound Interest (chat)|compound-interest as geometric growth]] work.
