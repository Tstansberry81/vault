---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2025-10-22
author: Traveler Stansberry
source_type: chat
tags: [chat, coding, aws, docker, startup/homework-hatch, deployment]
status: active
---

# Fixing the Docker-to-ECR Push Failure for Homework Hatch - App Runner and the 12GB Image

A deployment-debugging session for [[Homework Hatch (startup)]], where Traveler was trying to host his Flask backend on AWS and kept hitting walls. It opens with a screenshot of an AWS **App Runner** failure ("Invalid Access Role in AuthenticationConfiguration… Failed to copy the image from ECR") and ends with the real root cause: a **12 GB Docker image** that choked on every push to ECR. This chat is a strong window into how Traveler actually ships product — and how thin his coding foundation was at the time (his own words: *"I know nothing about coding, and a slight bit about aws"*).

## The presenting problem: the IAM role
The App Runner error was a permissions mismatch. ChatGPT diagnosed it as the classic foot-gun: App Runner's image-fetcher needs an **ECR access role** whose trust policy names `build.apprunner.amazonaws.com` (not the runtime **instance role** that trusts `tasks.apprunner.amazonaws.com`). Fix: create `AppRunnerECRAccessRole`, attach `AmazonEC2ContainerRegistryReadOnly`, and set it as the service's `AccessRoleArn`. This continues Traveler's long, painful tour through AWS IAM — see [[Deploying a Flask App - AWS Elastic Beanstalk, GitHub Actions, and IAM Keys (chat)|Deploying a Flask App - AWS Elastic Beanstalk, GitHub Actions, and IAM Keys]] and [[Launch to AWS Elastic Beanstalk - Flask Deploy and WebSocket Config (chat)|Launch to AWS Elastic Beanstalk - Flask Deploy and WebSocket Config]].

## The conceptual lesson he asked for
Traveler then asked to be taught the whole pipeline from scratch. The mental model given: **Docker** packs the app into a container ("lunchbox"), **ECR** stores it ("fridge"), an **IAM role** is the keycard, and **App Runner** is the waiter that pulls and serves it. He probed whether Docker "simplifies the code" — answer: no, it *quarantines* it, freezing the OS/Python/Flask versions so "works on my machine" failures vanish, but it doesn't fix logic bugs. He confirmed the value: if a Flask app runs locally in the same image, it works in App Runner ~90% of the time (gotchas being port mismatch — App Runner wants 8000 — missing env vars, and ephemeral disk).

## The hosting tour: EB → ECS → App Runner
The chat reveals his actual migration path across three AWS services, each abandoned for being too fiddly:
- **Elastic Beanstalk** — "old-school, more control, more pain."
- **ECS (Fargate)** — required wiring an ALB, security groups, task execution vs. task roles, health checks; "looks up but sits at 0 healthy targets."
- **App Runner** — least ceremony, the recommended endpoint for his use case.

## The real bug: a 12 GB image stuffed with venv + PyTorch
The decisive reveal came when he shared the actual project (via Google Drive connector) as `HOMEWORK HATCH TM-3 DAYS.zip`. ChatGPT unzipped it and found he had bundled his **entire `venv/` and `__pycache__/`** into the build context — "you tried to ship your whole computer." The size was compounded by **full (CUDA) PyTorch**, which he was using for **live quiz management** in the app. Fixes prescribed:
- A real `.dockerignore` excluding `venv/`, `__pycache__/`, data, media, model weights.
- **CPU-only PyTorch wheels** (`--index-url https://download.pytorch.org/whl/cpu`) since App Runner has no GPU anyway.
- **Multi-stage builds** with `python:3.12-slim`, gunicorn instead of `flask run`, and pulling model weights from **S3** at runtime rather than baking them in.
- Architecture suggestion: split a small CPU **web tier** (Flask + websockets + quiz orchestration) from a separate GPU **inference tier**, weights in S3.

## What it shows
This is the engineering reality behind the [[Homework Hatch (startup)]] product: a self-taught founder shipping a Flask app with real-time quiz features (echoing the [[Study Materials Spec for Homework Hatch - Flashcards, Live Quiz, Practice Banks (chat)|Study Materials Spec for Homework Hatch - Flashcards, Live Quiz, Practice Banks]]), learning DevOps live by failing repeatedly. It fits his pattern of using ChatGPT as both tutor and pair-debugger, and his stated ambition to move past "vibe coding" toward real competence — see [[Learning to Code for Homework Hatch - Beyond Vibe Coding (chat)|Learning to Code for Homework Hatch - Beyond Vibe Coding]]. The Google Drive connector behavior here also overlaps with [[AWS Identity Center Setup for Homework Hatch and Wikipedia Training Dataset (chat)|AWS Identity Center Setup for Homework Hatch and Wikipedia Training Dataset]] and his broader file-management experiments. Connects to [[Traveler Stansberry]], [[Coding Club]], and his [[Intellectual Interests]].
