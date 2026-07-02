---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2025-09-06
author: Traveler Stansberry
source_type: chat
tags: [chat, startup, aws, devops, ai/training]
status: active
---

# AWS Identity Center Setup for Homework Hatch and Wikipedia Training Dataset

A hands-on infrastructure session in which Traveler walks ChatGPT (GPT-5) through giving his co-founder Josh access to the [[Homework Hatch (startup)]] AWS account, screenshot by screenshot. It closes with a pivot to the logistics of downloading all of Wikipedia to train an AI model. The chat is a window into Traveler operating as the de-facto solo devops/founder of his startup, learning cloud account administration in real time.

## What he was doing

He starts by asking the broad question of how to "share permissions and the account with someone." The assistant lays out the three standard paths: per-person **IAM users** (recommended for teammates), **cross-account roles** with trust policies and an external ID (for contractors with their own AWS account), and the newer centralized **IAM Identity Center** (formerly AWS SSO). Traveler is doing it through Identity Center, so most of the session is a guided walkthrough of that console.

Notable real-world friction he hit, all from his actual screenshots:
- Identity Center was already enabled in **us-east-1 (N. Virginia)** but he was viewing the **Ohio (us-east-2)** region, so the console appeared locked — AWS Organizations only supports one Identity Center region at a time. Fix: switch region.
- He briefly wanted to **delete and recreate** the instance (Actions → Delete instance), warned that all users/permission sets/assignments would be lost.
- He renamed his AWS Organization (org id `o-uxn6ma8s5o`) to "Homework Hatch."
- He created a group named **Homework Hatch** containing two Identity Center users — himself (`travstans`) and Josh (`j_hop`) — and learned the model: users → groups → **permission sets** assigned per AWS account (the "travstans management account").
- Confusion over "assign a new application": he meant an **Elastic Beanstalk** app he'd deployed, not a SAML SaaS app. Key clarification — Beanstalk apps live inside the AWS account and are reached via IAM/account permissions, not the Identity Center Applications tab. With `AdministratorAccess` on the group, Josh should already see the app; if not, it's almost always a **region mismatch** or he's logging in via root instead of the Start URL (`https://d-xxxx.awsapps.com/start`).

The assistant repeatedly offered a least-privilege custom permission-set JSON (full `elasticbeanstalk:*` + read-only S3/CloudWatch logs, no IAM/billing) instead of blanket admin, plus best-practice notes: never share root, require MFA, keep root for billing/emergencies only.

## The Wikipedia tail

The session ends with an unrelated thread: the file size of all of Wikipedia (~58 GB current English text uncompressed, ~24 GB compressed dump, tens of TB with full revision history, ~110 GB offline ZIM with images) and "how would I go about safely downloading it to train an AI model." The recommended pipeline: pull the maintained `wikimedia/wikipedia` parquet dataset from Hugging Face (easiest), or download official `enwiki-latest-pages-articles.xml.bz2` dumps via `aria2c`, verify checksums, extract with WikiExtractor, dedup (MinHash/LSH), tokenize and shard — plus the CC BY-SA / GFDL attribution and share-alike obligations.

## What it shows

This is Traveler wearing the infra hat for his startup, learning AWS account administration the way he learns everything for [[Homework Hatch (startup)]] — by doing it live and asking for the exact clicks. It confirms his stack uses **Elastic Beanstalk** (consistent with [[Deploying a Flask App - AWS Elastic Beanstalk, GitHub Actions, and IAM Keys (chat)]]) and that he's onboarding a co-founder/collaborator, **Josh (`j_hop`)**, into the cloud account. The closing pivot to scraping Wikipedia for model training fits his recurring ambition to build or train a custom model (see [[Custom LLM Build and SPHW Buddy Terms of Service (chat)]] and [[PC Build, Local LLM Training, and the AI Workstation Ladder (chat)]]) — a teenage founder reaching, perhaps over-reaching, toward training his own AI rather than just calling an API. It reinforces his self-taught, build-it-yourself bent documented in [[Coding Club]] and his [[Intellectual Interests]].
