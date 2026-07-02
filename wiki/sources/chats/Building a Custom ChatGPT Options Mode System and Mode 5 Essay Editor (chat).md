---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2025-10-07
author: Traveler Stansberry
source_type: chat
tags: [chat, productivity/prompt-engineering, english/death-of-a-salesman, ib/english]
status: active
---

# Building a Custom ChatGPT Options Mode System and Mode 5 Essay Editor

A 2025-10-07 conversation (GPT-5) in which [[Traveler Stansberry]] designs and iteratively refines a personal **"options mode" system** for ChatGPT — a set of numbered personas he activates by prefixing a message with a digit and colon (e.g. `5:`). The bulk of the chat is him hand-tuning **Mode 5 (Read/Write Editor)** through roughly a dozen rounds of "save it to memory," then stress-testing it on his own [[Death of a Salesman]] essay. It's a revealing window into how he engineers AI tools to serve his own learning rather than do the work for him.

## The mode system
He had already built modes 0–4 and adds Mode 5 here. The full lineup, per his "definitions of options" command:
- **0 = Normal (Cynic Core)** — default; sarcastic, blunt, factual, calls out lazy reasoning.
- **1 = Researcher** — neutral academic summarization, no analysis or opinion.
- **2 = Data Analyst** — step-by-step math/stats/econ with shown work and verification (ties to [[IB Economics (SL)]], [[IB Math (SL)]]).
- **3 = Advice Giver** — ranked, practical recommendations.
- **4 = Coder** — production code in Python, JS, C++, Flask, n8n; explicitly scoped to [[Homework Hatch (startup)]] integrations.
- **5 = Read/Write Editor** — IB/college-rubric essay feedback (the focus of this chat).
- A global `definitions of options` command regenerates explicit outlines of all modes, auto-updating as he edits them.

This is a small but telling artifact of his [[Intellectual Interests|intellectual profile]]: he treats the model as a configurable instrument with named operating modes, an engineer's instinct applied to his own study workflow.

## How he tuned Mode 5
The iterative design is the real content. Across the chat he forces increasingly strict constraints, all pointed at one principle — **the AI must not think for him.** Key rules he locks in:
- No wholesale rewording into "complex language"; suggest, don't ghostwrite.
- Originally a 5-round enhancement loop (borrowed from a teacher-style prompt); he later deletes the loop and makes it grade-and-critique a full essay or paragraph dynamically.
- Grade out of 100 calibrated to **IB and college rubrics** (Criteria A–D after he uploads an IB English Literature rubric image), with explicit point breakdowns and quantified improvement magnitudes ("+0.5 in Analysis").
- **Feedback must stay inside his own thesis** — no suggesting new interpretive angles he didn't raise. He catches the model recommending "postwar commentary / expressionism" and bans it: only refine within his chosen frame (fatherhood, masculinity, identity, ethics, success, work ethic).
- Final rule: instead of supplying a better sentence, the model must **ask him a guiding question** so he figures out the fix himself. Stated goal: "all the thinking power is within me, and you only suggest fixes."

> [!note] What this reveals
> This is the same self-directed-learning ethic that underlies [[Homework Hatch (startup)]] (a study tool, not a cheating tool) and his [[Learning to Code for Homework Hatch - Beyond Vibe Coding (chat)|resistance to "vibe coding"]]. He deliberately engineers AI to scaffold his reasoning rather than replace it.

## The test essay
He repeatedly feeds in his own essay, **"An Exploration of Male Identity in Death of a Salesman"** (prompt: how Miller questions traditional masculine identity through character development). His thesis: the collapse of male identity in [[Death of a Salesman]] is tied to ethical values, conception of success, and work ethic — all inherited from flawed father figures. Body paragraphs cover Willy's affair with "The Woman" and dishonesty, Biff's stealing, the Ben-derived "be liked and you will never want" myth of success, and both men's aversion to hard work (Biff's failed UVA football scholarship via a flunked math class). The essay connects directly to wiki concepts [[Masculinity]], [[Identity and Its Collapse]], and the father-son inheritance theme.

GPT-5 grades successive versions 91 → 94 → 95/100 (IB 7 / college A+ band), the rise tracking his tightening of the mode's feedback rules rather than edits to the essay itself. Recurring critiques: a few paragraphs lapse from analysis into summary, and over-reliance on weak verbs ("shows," "demonstrates," "reveals").

This essay is itself documented across his [[English Curriculum 2022-2026|English coursework]] and overlaps the [[Masculine Identity in Death of a Salesman, then HW Buddy and P&G Tangents (chat)|other Death of a Salesman chat]], where the same draft appears.
