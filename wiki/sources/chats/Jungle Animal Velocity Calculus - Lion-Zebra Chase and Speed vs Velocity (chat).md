---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2026-03-27
author: Traveler Stansberry
source_type: chat
tags: [chat, math/calculus, coursework-math]
status: active
---

# Jungle Animal Velocity Calculus - Lion-Zebra Chase and Speed vs Velocity

A [[IB Math (SL)]] kinematics-via-calculus homework session in which Traveler works two problems through ChatGPT (gpt-5). It is pure mechanics of differentiation, integration, and the perennially confusing distinction between **speed** and **velocity**.

## The lion-and-zebra word problem
The first item (submitted as an image worksheet) models a predator-prey chase with exponential velocity functions: lion $v_1(t)=15e^{-0.1t}$, zebra $v_2(t)=20-20e^{-0.1t}$, initial gap 40 m. The assistant runs the full multi-part solution:
- Speeds at $t=1$: lion 13.57 m/s, zebra 1.90 m/s.
- Differentiation to show the lion decelerates ($v_1'=-1.5e^{-0.1t}<0$) and the zebra accelerates ($v_2'=2e^{-0.1t}>0$).
- $\int_0^3 v_1\,dt = 150(1-e^{-0.3})\approx 38.88$ m (distance the lion travels).
- The gap closes by 30.72 m in the first 3 s.
- The minimum-distance condition is where $v_1=v_2$, solved as $t=10\ln(7/4)\approx 5.60$ s. The lion does **not** catch the zebra, reaching within ~1.92 m.

A nice methodological touch: the closing distance at the closest moment is computed by integrating the velocity difference, exploiting that $e^{-0.1t}=4/7$ at that instant to avoid re-evaluating the exponential.

## Where did the negative go?
Traveler catches what looks like a vanished sign when solving $e^{-0.1t}=4/7$ and asks about it directly. The answer walks the log identity $-\ln(a)=\ln(1/a)$, so $-\ln(4/7)=\ln(7/4)$ — the negative is absorbed by flipping the fraction. This is characteristic of him: he doesn't accept a result he can't reconstruct, the same instinct that drives his [[Theory of Knowledge]] doubt essays and his refusal to "vibe code" without understanding (see [[Learning to Code for Homework Hatch - Beyond Vibe Coding (chat)|Learning to Code for Homework Hatch - Beyond Vibe Coding]]).

## Speed vs velocity confusion
The second problem ($s(t)=12t-2t^3-1$) exposes a real misread on both sides. ChatGPT initially treats the cubic as a *velocity* function and produces a wrong sign chart; Traveler pushes back twice ("the graph of velocity goes down after t=0", then "s(t) was the function i gave u"), forcing the correction. With $s$ as position: $v(t)=12-6t^2$, $a(t)=-12t$. The key takeaway he was missing: **speed** $=|v|$ increases when $v$ and $a$ share a sign, not simply when the velocity graph rises. Final: speed increasing on $(-\sqrt2,0)\cup(\sqrt2,\infty)$.

This is a small but telling exchange — Traveler corrected the model's framing rather than trusting it, and only conceded the speed sign-chart was genuinely the tricky part once the position/velocity mix-up was cleared. It fits his broader pattern of using ChatGPT as a checkable scratchpad for [[Academic Record]] coursework rather than an oracle.
