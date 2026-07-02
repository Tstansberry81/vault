---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2025-10-06
author: Traveler Stansberry
source_type: chat
tags: [chat, coding, coding-club, ai-tools]
status: active
---

# GitHub Copilot vs Cursor - Free Agentic Coding Tools for the Coding Club

A short tooling-selection chat (Oct 2025, GPT-5) in which Traveler scopes out a **free, easy, effective agentic coding setup** he can deploy for the [[Coding Club]] he teaches at [[St. Paul's School]]. It opens as a Copilot-vs-Cursor comparison and narrows into a concrete shortlist of free/open-source agents — exactly the kind of pragmatic infrastructure decision that recurs across his [[Homework Hatch (startup)]] and club work.

## What he asked
Three escalating questions: (1) can GitHub Copilot be used free in VS Code and how does it stack up against Cursor for small projects; (2) what to use for *agentic* coding in a school club — free, easy, effective; (3) "yeah go for it" — give a deployable stack.

## Key takeaways
- **Copilot Free** exists but is throttled: ~2,000 completions/month and ~50 "premium" (chat/agent) requests/month, limited model access (GPT-4o, Claude 3.5 Sonnet). Fine for genuinely small projects; mature and low-friction.
- **Cursor** is the more agentic option (project-wide edits, Composer-style bulk operations, cross-file awareness) but its strongest features sit behind Pro, and it can confidently produce buggy code.
- For a club specifically, the chat recommends a free/open-source stack and ranks five options:
  - **Continue.dev** (open-source VS Code extension; bring-your-own API key for OpenAI/Anthropic, or local models).
  - **Ollama + Continue** — fully local (CodeLlama/Mistral/Phi-3), works behind school firewalls, zero cost, privacy-friendly, but needs real hardware ("a school Chromebook won't survive this").
  - **Zed** — fast open-source editor with live collaboration and an agent panel, good for teaching/hackathons.
  - **Replit Agent** — instant, no-setup, best for beginners, heavily throttled free tier.
  - **Cline** — most autonomous ("LLM employee" that runs commands), with the warning to review every command it suggests.
- **Verdict:** Continue + Ollama for a real, free, offline-capable teaching setup; Replit Agent for absolute beginners, migrating to Continue once members get serious.

## What it reveals
This is Traveler in his **teacher/club-organizer mode** rather than as a coder for his own startup: the explicit constraints are *free*, *easy for classmates*, *works on school Wi-Fi*, and *safe to supervise* — i.e., picking tools that a roomful of students can actually run without a three-week setup slog. It complements his hands-on use of Cursor in his own work (see his [[Homework Hatch (startup)]] coding chats) and shows him weighing the local-model / privacy angle (Ollama behind a firewall) that also surfaces in his startup's privacy pivots. The emphasis on treating AI output as drafts to be reviewed — not final code — matches the verification-minded habits visible elsewhere in his projects.
