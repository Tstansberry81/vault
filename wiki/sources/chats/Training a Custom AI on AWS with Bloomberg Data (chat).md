---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2025-07-07
author: Traveler Stansberry
source_type: chat
tags: [chat, coding, ai/ml, finance, aws]
status: active
---

# Training a Custom AI on AWS with Bloomberg Data (chat)

A July 2025 ChatGPT (gpt-4o) session that opens as a one-line math question — "what is a lambda function in mathematics" — and is answered in terms of lambda calculus (Alonzo Church, λx. f(x) anonymous-function abstraction, and its echo in Python's `lambda x: x+1`). The math framing is a feint: the rest of the chat is a practical roadmap for **building and training a custom AI model**, with a clear finance/quant intent behind it.

Traveler pivots immediately to infrastructure: which AWS service is best for training (answer: **Amazon SageMaker** as the all-around managed choice, with EC2 + Deep Learning AMIs for custom GPU control, and Lambda/Batch/Fargate for orchestration rather than training itself). He then asks the broader "how to train and make your own AI," getting a six-stage pipeline — define problem, collect/prepare data, choose framework (TensorFlow/PyTorch/scikit-learn/Hugging Face), train, evaluate (over/underfitting), deploy (Flask/SageMaker endpoint/Gradio).

The revealing turn is the last question: **how to feed Bloomberg Terminal data into a custom model**. This ties his ML curiosity directly to his investing work — pulling data via the Bloomberg Excel add-in (`BDH`/`BDS` formulas) or the Python `blpapi`/`xbbg` API, preprocessing with pandas + `StandardScaler`, and loading into a PyTorch `DataLoader` for something like stock-price prediction. ChatGPT flags the **Bloomberg data license** caveat: internal research is fine, but redistribution/commercial deployment needs review.

This sits at the intersection of his two technical lives — the [[Coding Club]] teacher / [[Homework Hatch (startup)]] builder, and the [[Investment Club]] / Bloomberg user. It's the seed of a quant-style "train an AI on financial data" idea, echoing the ambition tracked in [[UVA and the Quant Question]] (UVA finance + math minor). It also shows his self-taught, top-down learning pattern: start from a primitive (lambda calculus), jump straight to "how do I build the real thing on cloud GPUs." No code was actually run here — it's scoping, not implementation. See also [[Stock Valuation Metrics, Bonds, Options, and Bloomberg ROIC (chat)]] and [[Bloomberg EQS Screening and Insurance Stock Research (chat)]] for his hands-on Bloomberg work, and [[Intellectual Interests]] for the broader CS/finance blend.
