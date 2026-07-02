---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2026-04-10
author: Traveler Stansberry
source_type: chat
tags: [chat, math/ib-sl, math/calculus]
status: active
---

# Glitched Screenshot IB Math SL Problems - Trig Tangents and Runner Kinematics

A short, practical [[IB Math (SL)]] homework session whose only memorable framing is its opening: Traveler uploaded three corrupted phone screenshots — a "glitchy collage" fusing overlapping images, a snake strip, a pool scene, and a sliver of a readable math prompt — which ChatGPT described as the phone having "a full existential breakdown." After being told to just "solve the questions," the model worked two full IB-style exam questions. The glitch is incidental; the substance is standard SL calculus practice.

## Question 7 — trig function, tangent and normal lines
Given $f(x)=\tfrac{2}{\pi}\sin(3\pi x)+2$ on $0\le x\le 2$:
- Amplitude $\tfrac{2}{\pi}$, period $\tfrac{2}{3}$.
- Tested whether point $P(1.63, 2.16)$ lies on the curve — found it sits *below* the graph since $f(1.63)\approx 2.216$.
- Given normal line $L_1: x-6y+11=0$ (gradient $\tfrac16$) at $A(1,2)$, derived the tangent $L_2$ gradient as the negative reciprocal $-6$, cross-checked via $f'(x)=6\cos(3\pi x)$, giving tangent $y=-6x+8$.
- Found the second intersection $B\approx(1.67, 2.11)$ numerically and the area between curve and line $\approx 0.0385$ square units.

Notable: the model openly fumbled the $B$ calculation mid-derivation ("Wait, that is not 0... Good catch. Humans love assuming nice numbers") before bisecting to a numerical root — a reminder of why Traveler routinely cross-checks AI math rather than trusting first answers.

## Question 9 — runner velocity model (calculus in context)
Two velocity functions for runners Fiona $v(t)=\tfrac{8.14t}{\sqrt{t^2+0.2}}$ and Lucy $w(t)=\tfrac{8t}{\sqrt{t^2+0.3}}$. Work covered:
- $v(1)\approx 7.43\ \mathrm{m\,s^{-1}}$; time to reach $5\ \mathrm{m\,s^{-1}}$ ($t\approx 0.348$ s).
- Differentiated to acceleration $v'(t)=\tfrac{1.628}{(t^2+0.2)^{3/2}}$, solving $v'=4$ for $t\approx 0.591$ s.
- Limit $\lim_{t\to\infty}v(t)=8.14$, with the contextual caveat that the 200 m race ends in finite time so the asymptote is not physically meaningful.
- Integrated velocity to displacement $s_F(t)=8.14(\sqrt{t^2+0.2}-\sqrt{0.2})$, found Fiona finishes 200 m in $\approx 25.0$ s, and computed Lucy is $\approx 4.23$ m from the line at that moment.

## What it shows
A typical slice of Traveler's SL toolkit: trig amplitude/period, tangent–normal reciprocal gradients, numerical root-finding when exact answers don't exist, the product rule, and definite integration for displacement — including the "interpret in context" wrinkle ([[IB Math (SL)]] paper-2 style with calculator). It fits the large cluster of his calculus homework chats. Low-stakes, no deep reflection here; just getting an exam set done after a phone hiccup, consistent with his heavy reliance on AI for routine coursework throughput while saving scrutiny for the steps that matter.
