---
type: source
created: 2026-06-17
updated: 2026-06-17
source_date: 2025-07-15
author: Traveler Stansberry
source_type: chat
tags: [chat, coding, devops, startup, aws]
status: active
---

# Deploying a Flask App - AWS Elastic Beanstalk, GitHub Actions, and IAM Keys

A summer 2025 (July 15) DevOps troubleshooting session in which Traveler works through how to **host and auto-deploy a Flask web app** — almost certainly the backend for [[Homework Hatch (startup)]] (SPHW Buddy / HW Buddy). The conversation is a window into the unglamorous infrastructure side of his startup: not the AI or product, but the plumbing of getting a Python app onto the internet and keeping it updated.

## What he was doing
The chat opens cryptically ("iam role eb") and unfolds as a beginner-level walk through AWS deployment, where Traveler is clearly hitting walls and asking increasingly basic clarifying questions:

- **IAM roles for Elastic Beanstalk** — the service role (`aws-elasticbeanstalk-service-role`) vs. the EC2 instance-profile role (`aws-elasticbeanstalk-ec2-role`).
- **Alternatives to AWS** — he asks for "other free web hosting servers besides aws," getting the standard rundown: Render, Vercel, Netlify, Glitch, Replit, Fly.io, PythonAnywhere. The recommendation for a *real Flask app* lands on **Render** (native Flask, auto-deploy from GitHub) or PythonAnywhere for beginners.
- **CI/CD / "automatic updating"** — he wants the app to redeploy on every code push; the answer covers Render, Vercel, Netlify, GitHub Actions, and Fly.io.
- **GitHub Actions confusion** — he asks "does github actions make a website for you" (no — it's automation/CI, not a host) and "can you link aws and github actions" (yes, via an IAM user + GitHub Secrets + a `deploy.yml` workflow using the `einaregilsson/beanstalk-deploy` action).
- **Access keys** — a long, frustrated thread: "where do i find them," "what do they look liked," and finally "i never saw a secret key" — learning the hard way that AWS shows the secret access key exactly once and you must regenerate it if missed.

## What it reveals
This is Traveler operating well outside his comfort zone. His coding fluency is real but self-taught and application-driven (see [[Coding Club]]); here he is bumping against the steep, jargon-heavy learning curve of cloud infrastructure (IAM, instance profiles, CI/CD pipelines, secrets management) with no prior mental model — asking what an access key literally "looks like." It documents a concrete build phase of [[Homework Hatch (startup)]]: a Flask backend being pushed toward a live, auto-updating deployment, weighing AWS Elastic Beanstalk against cheaper free tiers (Render). It pairs with his other AWS chats (e.g. *Training a Custom AI on AWS with Bloomberg Data*) showing AWS as a recurring tool he wrestles with rather than commands.

The arc — start on AWS/Elastic Beanstalk, then immediately ask for free alternatives — also hints at a cost-sensitive, scrappy founder pattern: he wants production deployment but on a student budget.
