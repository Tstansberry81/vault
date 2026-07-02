---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2025-08-18
author: Traveler Stansberry
source_type: chat
tags: [chat, hardware, ai, homework-hatch, gaming]
status: active
---

# PC Build, Local LLM Training, and the AI Workstation Ladder

A GPT-5 conversation (2025-08-18) that begins with Traveler asking ChatGPT to recap his gaming PC's specs and spirals into a long discussion about training his own LLM, scaling up to workstation/data-center hardware, and the implications for [[Homework Hatch (startup)]]. It doubles as a window into both his high-end consumer setup and his ambitions to bring AI model work in-house.

## The rig
ChatGPT recites his build: NZXT H9 Flow case, MSI Pro X870E-P WiFi board, **AMD Ryzen 7 9800X3D**, Lian Li Hydroshift II 360 AIO, **ASUS RTX 5090 ROG Astral (32GB)**, 64GB DDR5-6000, Samsung 990 Pro 2TB NVMe, Lian Li Edge 1200W PSU. Peripherals: ASUS PG27AQDP WOLED 1440p monitor (the same panel that recurs in his [[ASUS ROG OLED Monitor - RGB Lighting and Key-Lock Firmware Loop (chat)]] and other monitor-troubleshooting chats), SteelSeries Arctis Nova Pro, Logitech Pro 2 Lightspeed, Keychron V1 Max. A genuine enthusiast/[[Extracurriculars and Achievements|gaming]] machine, used here partly to play Red Dead Redemption.

## "How to create your own LLM"
The substantive thread. ChatGPT lays out the three paths: (1) run a pretrained 7B–13B model locally via Ollama/LM Studio/llama.cpp plus a RAG pipeline (LangChain/LlamaIndex + FAISS/Chroma); (2) **fine-tune** a 7B–13B base with QLoRA (the recommended "best ROI" path, with a full PyTorch/transformers/trl/peft/bitsandbytes recipe); (3) pretrain from scratch — dismissed as impractical at home. Verdict for his 5090/64GB rig: comfortable fine-tuning at 7B, workable at 13B, inference-only above 30B.

> [!note] LLM provider context
> ChatGPT's recipe centers on open-weight models (Llama 3.1 8B, Mistral 7B) for local fine-tuning. For Homework Hatch's actual production stack, Traveler's other chats lean on hosted APIs; this conversation is about what he could run on his own hardware, not a final architecture decision.

## The workstation ladder
The back half climbs the hardware tiers: RTX Pro 6000 Blackwell (96GB) vs. Threadripper Pro (why pair CPU + GPU — PCIe lanes, ECC RAM capacity, orchestration), then a "beast" AI-modeling build (Threadripper Pro 7995WX + 1TB ECC + dual/quad Blackwell, ~$35k–50k), an even bigger "Overkill Rig 2.0" (~$65k–75k), and finally the jump to DGX racks, InfiniBand clusters, and GPT-scale supercomputers ($500k → $10M+). Traveler frames it in startup terms: his current PC "will cut it for a while handling user data and running code," and he'll buy a workstation "when I need to actually make a decently sized LLM." This is the same instinct that drives [[Building a Custom AI Stock-Ranking Model (chat)]] and [[Training a Custom AI on AWS with Bloomberg Data (chat)]] — a recurring desire to own the model layer rather than rent it.

## Two persistent ChatGPT instructions
He sets two account-wide memory rules here that explain the tone of his later chats:
- "From now on if I'm repetitive or asking dumb questions I want you to be a bit sarcastic (5/10)... add more humor and nuance... apply for ALL FURTHER CHATS." (The half-roast persona.)
- "From now on when I say 'hw buddy ai ideas' I want you to send me a list of 10 AI implementation ideas for my application." ChatGPT, prompted, summarizes his app: a **Canvas-API-integrated college learning companion** that summarizes assignments, makes study guides/flashcards/Kahoots, gives grade-tailored recommendations, runs class-specific chatbots, and generates explanatory videos — a concise snapshot of the [[Homework Hatch (startup)]] feature set as of mid-2025, consistent with the [[Canvas LMS Adoption Research for Homework Hatch (chat)]] and [[Agentic AI, MCP, and LMS Credential Ingestion for Homework Hatch (chat)]] threads.

## What it reveals
The chat captures Traveler in characteristic mode: a [[Traveler Stansberry|finance-bound builder]] casually conflating gaming, AI engineering, and his startup, treating a $40k workstation as a "when I'm hella rich" milestone rather than a fantasy. The duck/Bloomberg-terminal banter ("Duck Capital Management") reflects his self-image as a serious markets person. It also documents how he deliberately shaped ChatGPT's personality, which colors the voice of much of his exported chat history.
