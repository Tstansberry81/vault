---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2025-10-20
author: Traveler Stansberry
source_type: chat
tags: [chat, startup, finance, coding, poker]
status: active
---

# Texas Hold'em Algorithm then Homework Hatch Valuation and AWS Cost Modeling

A grab-bag ChatGPT (GPT-5) session that opens on a coding/math curiosity and pivots into the business mechanics of [[Homework Hatch (startup)]]. It captures [[Traveler Stansberry]] thinking like a founder — equity, valuation, unit economics — alongside his recurring instinct to formalize problems mathematically.

## Texas Hold'em as a probabilistic algorithm
He asks for the "general algorithm" of Texas Hold'em, then immediately demands a "more math based" version — characteristic of his preference for rigor over narrative. The model formalizes the game as state-variable evolution \(S_{t+1} = f(S_t, \text{action}_i)\), and frames optimal play as expected-value maximization:
- **Win probability** via Monte Carlo over remaining community-card combinations.
- **EV of call/fold/raise**, with the optimal action as \(\arg\max EV\).
- **Pot odds** rule: call when \(P_{\text{win}} > \frac{B}{P+B}\).

This is recreational/coding curiosity (likely a poker-bot or simulator idea) but reflects the same EV-and-probability lens he applies to investing — see [[Intellectual Interests]] and his work in [[Investment Club]].

## Homework Hatch: equity, obligations, valuation
The bulk of the chat is startup work. He asks about **member obligations in a Maryland multi-member LLC** (Md. Code Title 4A — capital contributions, fiduciary duties, Operating Agreement primacy, pass-through tax, the non-absolute limited-liability shield) and **how to negotiate the initial equity split**. The framework: value each founder's contribution (cash, IP, sweat equity), set baseline percentages by proportion, then adjust for role/time/risk, with **4-year vesting and a 1-year cliff** on sweat equity. This connects to the formal entity setup documented in [[Maryland LLC Setup, EIN, and Domain Transfer for Homework Hatch (chat)|Maryland LLC Setup, EIN, and Domain Transfer for Homework Hatch]] and [[Filing the Maryland LLC for Homework Hatch - Articles, EIN, and Stripe (chat)|Filing the Maryland LLC for Homework Hatch - Articles, EIN, and Stripe]].

He then asks how to **value a pre-revenue startup**. The model walks Berkus, Scorecard, Risk-Factor Summation, Cost-to-Duplicate, and the VC Method (\(V_{pre} = V_{exit}/(R(1+r)^n)\)), landing on a **$1.0–1.5M pre-money** anchor for Homework Hatch with a functioning MVP and early testers.

### Pricing and unit economics
He locks in pricing: **$10/month base, $20/month premium**. With 25% premium mix, average revenue is $12.50/user/month → ARR \(= 150N\). A scenario table puts 5,000 users at ~$750K ARR and a defensible ~$1–1.2M valuation. Break-even arrives at roughly **400–500 paying students** (fixed costs ~$2K/mo, ~$2.50/user compute) — a key talking point he could use with investors. Founder split logic he entertains: ~50–60% to himself as technical/AI founder, 20–30% biz co-founder, 10–15% option pool.

## AWS cost modeling
He clarifies he runs "the entire application through AWS" and wants to know whether [[Deploying a Flask App - AWS Elastic Beanstalk, GitHub Actions, and IAM Keys (chat)|Elastic Beanstalk]] scales cost per user. Key takeaway: EB itself is free; you pay for the underlying EC2 / load balancer / S3 / RDS / CloudWatch / data transfer, and **cost scales with concurrent traffic, not total signups**. Modeled baseline ~$80–150/mo for 1–2 t3.medium instances plus a small DB, falling to **$0.03–0.10 per active monthly user** as auto-scaling spreads fixed cost — comfortably under his $10–20 price point. This is the unit-economics complement to the architecture discussions in [[HW Buddy App Architecture Analysis and GPT-5 Model Choice (chat)|HW Buddy App Architecture Analysis and GPT-5 Model Choice]].

## Throwaway tangents
Two unrelated interruptions: a "stuck in the Shift key" tech-support question (Sticky Keys / jammed switch) and the AWS pricing question that launched the cost-modeling thread — minor, but they fit the pattern of him multitasking real product work with whatever else is on screen.

> [!note] What it reveals
> Traveler is genuinely operating Homework Hatch as a business, not a school project: he reasons about Maryland LLC law, founder vesting, pre-revenue valuation methods, and cloud unit economics in the same sitting. His habit of converting any problem (even poker) into EV/probability math is the throughline tying his [[finance]] instincts to his coding and startup work.
