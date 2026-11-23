---
layout: page
title: Daap
permalink: /daap/
---

<img src="{{ '/assets/daap/daap-icon.png' | relative_url }}" alt="Daap app icon" width="80" height="80">

**Daap is a local discovery app: it helps people find the businesses, communities, jobs and conversations around them.**
I founded it and build it end to end: backend, web app, mobile app, cloud infrastructure and the IT behind the company.
It started in 2025 as the Fleen platform and continued as Daap from February 2026; the company was incorporated in Nigeria in November 2026.

Daap is **pre-launch**. The source code is private; I'm happy to walk through it, the architecture and the runbooks in an interview.

## Screens

Screens from the iOS app on the test environment, with sample data.

<p>
  <img src="{{ '/assets/daap/thoughts.jpg' | relative_url }}" alt="Local feed showing nearby posts with distance bands" width="240">
  <img src="{{ '/assets/daap/business.jpg' | relative_url }}" alt="Business listings ranked by distance" width="240">
  <img src="{{ '/assets/daap/job.jpg' | relative_url }}" alt="Posting a job with an AI-drafted title and description" width="240">
</p>

Left to right: the local feed, with each post's distance band; nearby businesses, closest first; posting a job, where AI drafts the title and description from one sentence.

## What I built

**Product**
- Businesses, communities, jobs and a local feed, with likes, bookmarks, shares, notifications and blocking.
- Location features: region scope by country, state and city; ranking by distance; a "local pulse" that spots what is suddenly busy in your area. I tune the ranking rules with simulations on seeded test cities.
- Search that combines full-text and vector embeddings, with AI tagging and categories.
- AI features: job drafting, job details extracted from images, and AI-assisted content moderation whose prompts admins can change at runtime.
- 13 languages.

**Engineering**
- Backend: Java and Spring Boot, split into feature modules (core, admin, owner, search, social, tag, moderation, notification).
- Web app in Angular; iOS and Android app in React Native (Expo).
- Data: PostgreSQL with pgvector, Redis-compatible cache (Valkey).
- Ready to run on several servers at once: durable work queues on AWS SQS, locked scheduled jobs, and no state kept in a single server's memory.
- New features ship behind switches that are off by default, so they can be turned on gradually and off quickly.

**Operations, security and IT**
- AWS: EC2, S3 behind CloudFront, SQS, IAM; Cloudflare in front; Firebase for real-time updates; Expo for push notifications.
- CI/CD with GitHub Actions; deployments through AWS Systems Manager with no SSH open; a zero-downtime blue/green deployment rehearsed end to end and written up as a runbook.
- Monitoring with metrics and alerts to a team chat channel.
- Security work: an access-control (IDOR) audit, uploads served only through the CDN, refresh-token sign-in, Google sign-in, account alerts and signing out other sessions.
- Company IT: I administer the Google Workspace (users, app access, domain-wide delegation for service accounts) and the AWS, Cloudflare, Google Cloud and Firebase accounts.
- Engineering guides and runbooks for every setup and recovery step, and an archive of Bash and Python scripts for deployments, database checks and data clean-ups.

**Java** \| **Spring Boot** \| **PostgreSQL** \| **TypeScript** \| **Angular** \| **React Native** \| **AWS** \| **Cloudflare** \| **AI**

[Back to home]({{ '/' | relative_url }})
