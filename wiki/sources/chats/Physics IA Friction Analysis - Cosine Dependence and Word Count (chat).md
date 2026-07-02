---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2026-03-03
author: Traveler Stansberry
source_type: chat
tags: [chat, physics, ib, internal-assessment]
status: active
---

# Physics IA Friction Analysis - Cosine Dependence and Word Count

A mid-IA check-in on Traveler's [[IB Physics (HL)]] Internal Assessment, which investigates **how frictional force varies with the angle of an inclined plane**. He opens by asking the model to recall what it knows about his IA, then works through a conceptual confusion and a logistics question. The chat is a window into both the physics he's wrestling with and his characteristic habit of stress-testing his own assumptions before an examiner can.

## The experiment
Traveler places an object on a ramp, varies the incline angle, measures the object's **acceleration**, and back-calculates friction via dynamics. The model he's working from:

- Friction: \( F_f = \mu N \), with normal force on an incline \( N = mg\cos\theta \), giving \( F_f = \mu mg\cos\theta \).
- From resolving forces along the ramp (\( mg\sin\theta - F_f = ma \)) he derived \( \mu g\cos\theta = g\sin\theta - a \), letting him compute friction from measured acceleration.

He had already done IA-level data work: propagating uncertainties on each friction value and the average, handling acceleration and angle uncertainty (\( \Delta\theta \)), and deliberately **avoiding the √3 method** in favor of a more generalizable, IB-friendly justification. He'd also noticed his graph trended slightly *upward* when theory says friction should *decrease* with angle, and worried aloud whether his data "looked shitty."

## The conceptual untangling
Two genuine physics misconceptions get cleared up:

1. **"Shouldn't force vs angle be perfectly proportional?"** No — \( F_f \propto \cos\theta \), not \( \theta \), so the raw graph is a *decreasing curve*. The strong IA move is to plot \( F_f \) vs \( \cos\theta \), which linearizes to \( y = kx \) through the origin (slope \( \mu mg \)). Showing both the raw curve and the linearized fit demonstrates understanding rather than "graphing random stuff and praying."
2. **"If the angle is 0, how is there any friction?"** Friction comes from surface contact, not the angle; at \( \theta = 0 \) the normal force \( N = mg \) is at its *maximum*, so the *capacity* for friction is greatest — there's just no driving force (\( mg\sin 0 = 0 \)) for it to oppose. Static friction self-adjusts up to \( \mu mg \). So friction is strongest at flat, exactly where it appears to do nothing.

## The logistics
The IA word limit is **3000 words max**, counting all prose (intro, theory, method, captions, table text) but not raw data, equations, calculations, units, or references. Examiners reportedly stop reading at 3000, so burying the high-mark evaluation past the cap is self-sabotage. Suggested target ~2200–2600 words, with a rough section budget (data processing ~800, analysis ~700, evaluation ~600).

This connects to his earlier [[Physics IA Topic Selection - Friction Coefficient and Rotational Energy (chat)]], where the friction-coefficient idea was chosen, and fits his broader [[Academic Record]] as an IB Diploma candidate at [[St. Paul's School]].
