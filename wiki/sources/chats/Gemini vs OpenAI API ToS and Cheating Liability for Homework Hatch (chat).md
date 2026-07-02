---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2025-08-21
author: Traveler Stansberry
source_type: chat
tags: [chat, startup, legal, compliance, ai]
status: active
---

# Gemini vs OpenAI API ToS and Cheating Liability for Homework Hatch

A compliance-focused conversation in which Traveler interrogates the legal terms of using third-party LLM APIs commercially for [[Homework Hatch (startup)]] (referred to here as "HW Buddy"). It is one of the clearer windows into him thinking like a founder weighing regulatory risk rather than a coder — and it surfaces a real, unresolved compliance problem at the heart of his product.

## The core finding: Gemini's 18+ rule breaks his model
Traveler reveals that **Gemini powers the chatbot in his application**. ChatGPT flags that Google's Gemini API ToS imposes a hard **18+ requirement on both developers and end users** — apps may not be "aimed at or accessible by" anyone under 18. Since [[Homework Hatch (startup)]] targets high-school students (a population at [[St. Paul's School]] and beyond that is overwhelmingly under 18), running it on Gemini is squarely out of compliance. The suggested fixes were: age-gate the app, route under-18 users to a self-hosted open-source model, or negotiate an enterprise exception with Google Cloud.

> [!warning] Compliance gap
> Other Homework Hatch chats describe the product as built for high schoolers, yet here he states it runs on Gemini, whose ToS bans under-18 use entirely. By contrast OpenAI's API allows 13+ with parental consent. This is a material legal mismatch he had not resolved as of Aug 2025 — relevant to any later decision to switch model providers (see [[Agentic AI, MCP, and LMS Credential Ingestion for Homework Hatch (chat)]]).

## The cheating-liability question
The more revealing thread is Traveler probing whether his chatbot creates legal exposure if students use it to cheat. He zeroes in precisely on the word "**encourages**" in OpenAI's policy, arguing — correctly, per the assistant — that an essay written at a user's request isn't "encouraged" by the developer. The distinction drawn: **active framing** ("instant essay writer," "ace your homework") is encouragement and prohibited; **passive, user-initiated** output is not. He confirms his own ToS already states the bot is "for learning only" even though students can technically misuse it, and gets reassurance that this is the smart, defensible posture (the calculator/Texas Instruments analogy: a neutral tool, misuse on the user). This connects to his broader stance in [[Canvas LMS Adoption Research for Homework Hatch (chat)]] and [[Political and Economic Views]] — a deterministic, individualist framing where responsibility sits with the actor, not the tool.

## Other ToS specifics he extracted
- **OpenAI age rule:** 13+; 13–17 with guardian consent; under-13 banned — far more workable for a student audience than Gemini.
- **Branding:** can say "powered by GPT" but cannot put "GPT" in the product name (trademark/consumer-confusion rule) — directly relevant to naming HW Buddy / SPHW Buddy.
- **Universal prohibitions:** no reverse-engineering, no using outputs to train a competing model (he quips "trust me i'm not trying to compete w openai"), no reselling API keys, no scraping, respect safety filters.
- **Compliance frameworks** flagged for student data: FERPA, GDPR — a foreshadowing of the data-handling questions a real edtech product faces.
- He asks whether OpenAI and **GPTZero** have litigated (they have not; GPTZero is an AI-detection tool by Edward Tian), and probes the apparent contradiction of OpenAI banning "GPT" in names yet not suing GPTZero — answered via nominative/descriptive use.

The chat ends with a hard pivot into types of Italian liqueurs and the ABV of grappa (35–60%), an off-topic tangent typical of his mixed-purpose sessions.

## What it shows
Traveler is doing genuine pre-launch legal due diligence on [[Homework Hatch (startup)]], reading ToS like contracts and pressure-testing edge cases (the "encourages" semantics, the GPTZero contradiction) with a lawyerly precision. It documents that his chatbot was on Gemini as of Aug 2025, that he had already written a "learning only" ToS clause, and that he understood the cheating-liability landscape well enough to defend it. Reinforces his [[Extracurriculars and Achievements]] profile as a founder, not just a builder.
