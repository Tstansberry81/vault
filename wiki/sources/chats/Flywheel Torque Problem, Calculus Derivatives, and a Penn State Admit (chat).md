---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2025-11-19
author: Traveler Stansberry
source_type: chat
tags: [chat, physics, math, japanese, college-apps]
status: active
---

# Flywheel Torque Problem, Calculus Derivatives, and a Penn State Admit

A grab-bag homework session that begins as an [[IB Physics (HL)]] rotational-dynamics problem and then sprawls across [[IB Math (SL)]] calculus, [[IB History (HL)]], [[IB Japanese (SL)]] vocabulary, a college-admissions moment, and an [[Extended Essay (Economics)]]-adjacent polling-methodology question. It is a snapshot of Traveler using ChatGPT as a one-stop tutor across his whole IB course load in a single evening.

## The flywheel problem (the spine of the chat)
The bulk of the session is a multi-part rotational mechanics question: a solid-cylinder flywheel (mass 1.22 kg, flywheel radius 240 mm, axle radius 60 mm) is spun by a falling mass on a string wrapped around the axle. Working through it, Traveler establishes the toolkit:
- Moment of inertia of a solid cylinder, $I = \tfrac12 MR^2 = 0.0351\ \text{kg·m}^2$ (he initially mis-stated $I = 0.5$, prompting the model to push back hard that this was physically impossible for the given geometry).
- Angular acceleration from $v = r\omega$ and $\omega = \alpha t$: $\alpha = v/(rt) \approx 7.92\ \text{rad/s}^2$.
- Torque via $\tau = I\alpha \approx 0.28\ \text{N·m}$ ("about 0.3 N·m").
- String tension from Newton's second law on the falling mass, $T = m(g-a)$, and back-solving the falling mass as $\approx 0.50$ kg.

The intellectually revealing part is his **insistence on understanding, not just answers**. He repeatedly probes the *why*: can the problem be solved without using $\tau = Tr$; isn't the falling mass itself twisting the flywheel; and crucially "why isn't it $mgr = $ torque, isn't that the force making the torque?" The model walks through lever-arm geometry, the work-energy derivation ($\tau\theta = Tr\theta$), and the chain of causation (gravity → tension → torque), stressing that only tension acts *on* the flywheel and that $mgr$ only coincidentally lands near 0.3 N·m because it wrongly assumes free-fall. This is the same conceptual-foundations instinct that shows up across his [[IB Physics (HL)]] work.

## The other subjects, in passing
- **[[IB Math (SL)]] calculus:** derivative of $2\sin x + \cos(2x) = 2\cos x - 2\sin(2x)$; evaluating $f(\pi/2)=1$; the second derivative; and a quotient/product-rule problem $y = x/\sqrt{1-3x}$ giving $y' = (1 - \tfrac32 x)/(1-3x)^{3/2}$.
- **[[IB History (HL)]]:** a quick "Cultural Revolution intent" rundown (Mao's purge of rivals, ideological purification, Red Guards, cult of personality, permanent revolution) — fitting his Asian/modern-history syllabus.
- **[[IB Japanese (SL)]]:** vocabulary checks — 森本 (Morimoto), なくなって, ほとんど, 性格 vs 正確, 年生 — plus the model correcting his garbled attempt at "are you really a high schooler?" (本当に高校生ですか).

## The Penn State admit
Mid-session he interjects: "penn state came out today and i got in." This is a dated data point for his [[College Search]] timeline (19 Nov 2025) — an early big-state admit alongside his eventual [[UVA and the Quant Question|UVA]] destination, landed while juggling IB, coding, and his startup [[Homework Hatch (startup)]]. See also [[Extracurriculars and Achievements]].

## Pew polling methodology
He closes by having the model read a Pew Research article, "How Public Polling Has Changed in the 21st Century," and asks specifically for the **limitations pollsters face**, sourced only from the article: methodology churn (61% of pollsters changed methods 2016→2022), decline of live-phone polling, disclosure/transparency gaps, exclusion of state-level polls, and non-comparability over time. He then asks whether a sentence ("the polls will always be inaccurate no matter what method they use") is grammatically correct. This research has the flavor of his [[Extended Essay (Economics)]] / [[Theory of Knowledge]] work — interrogating data provenance and the reliability of measurement, a recurring thread in his [[Intellectual Interests]].
