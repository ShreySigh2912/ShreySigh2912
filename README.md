# Shrey Singh

**Founder / Program Director. I run executive education programs with IITs and IIMs, and I build the software that runs them.**

Most of what I ship lives in private repositories because it carries learner data, institution branding, and partner integrations that I cannot open-source. This page is the tour of what is behind the wall.

---

## What I do

I design, launch, and operate professional certification programs for working professionals, in partnership with institutions such as **IIT Patna, IIM Trichy, NITK Surathkal, and IIT Jammu**. That means owning the whole funnel and the whole delivery stack:

- Landing pages and lead capture that feed a CRM within seconds
- Counsellor routing, call analytics, and sales coaching driven by transcripts
- Learner operations: enrolment, attendance, refunds, batch transfers, support, certificates
- An LMS, Slack communities, and the automation glue between every tool a cohort touches
- AI agents that score applications, flag dropout risk, and brief the program team

I write most of this myself in TypeScript and Node, with Python where it fits, and I ship it to production. The list below is a selection, not the full inventory.

---

## Selected work

### Operations platforms

**LearnOS + Sales Module** · React, Vite, Hono, Supabase, Resend · private
Internal operations platform for 8+ certification programs across partner universities. Two modules on one backend and one auth layer. LearnOS handles the learner lifecycle: enrolment, Zoom attendance, refunds, batch transfers, tickets, KYC and custom forms, Q&A boards. The Sales Module ingests MCube call recordings, transcribes them with Whisper, analyses each pitch with GPT-4o, and lets team leads see their full reporting tree. Role-based access for admin, ops, counsellor, and sales. Live in production.

**Cortex** · Hono, Inngest, Next.js 15, Neon Postgres with pgvector, Clerk, Claude · private
A multi-tenant "company brain" for edtech. Every tool a cohort runs on (Tally, Razorpay, Zoom, AiSensy, Meta lead ads, Sheets, Gmail, Slack) posts into Cortex via webhooks. Records are normalised into edtech-native entities: leads, applications, students, cohorts, payments, sessions, mentors. Agents then score applications, monitor engagement, flag dropout risk, chase payments, and write the Monday briefing. Monorepo with a strict logging protocol and a documented security posture.

**GenAI Certifications LMS** · Moodle 4.5 LTS, Docker Compose, Caddy, MariaDB · private
Production LMS on a hardened Ubuntu VPS in India, serving institution-branded programs. Auto-TLS, nightly encrypted backups to Drive with 14-day retention, custom certificate and attendance plugins, an admin guide for the ops team, and scripted install and hardening so the whole thing can be rebuilt from the repo.

### Lead and growth infrastructure

**Lead Routing Service** · Hono, Airtable, Calendly · private
A sub-300ms redirect service that distributes inbound leads to counsellors. Replaced a percentage-based rotator with a least-recently-booked algorithm that reads the latest confirmed Calendly booking from Airtable, so counsellors with different conversion rates still get a fair share of actual bookings. Ops can add or pause a counsellor in Airtable with zero deploys. Documented with an operator runbook, failure modes, and performance targets.

**Program landing pages** · Static HTML, Tailwind, Supabase, Superleap CRM · private
Conversion-focused landing pages for IIT Patna, IIM Trichy, NITK, and IIT Jammu programs. No framework and no build step, so any team member can edit them. Every form posts to a self-hosted Supabase instance as the system of record, and a Postgres trigger forwards each lead to the CRM. Undelivered leads can be replayed. Pages ship with thank-you flows, policy pages, and campus sections.

**Certificate Verification Platform** · React, Vite, Supabase Edge Functions · private
Public verification portal plus admin dashboard for issuing digital certificates. Bulk CSV import, webhook-triggered generation, and per-program branding.

### Voice and AI

**MCube Call Processor** · Python, Whisper, Claude · [public](https://github.com/ShreySigh2912/mcube-call-processor)
Receives call webhooks from the CRM, downloads the recording, transcribes with Whisper, extracts a structured analysis with Claude, and pushes enriched results back onto the lead card. The small, readable version of the pipeline that powers the Sales Module above.

**Voice Transcript Service** · Node, Express, ffmpeg, OpenAI · private
Standalone transcription and analysis service with audio normalisation. Sits between telephony and the ops platform.

**VoiceAI SaaS** · Turborepo, TypeScript, Docker, Render · private
A Vapi-style platform for building and deploying AI voice agents on real phone numbers. Monorepo with apps and shared packages, containerised for deployment.

**PromptLens** · React, Supabase · private
An evaluation platform for prompt and model behaviour. Versioned prompts, CSV or JSON benchmark datasets, deterministic and LLM graders, optimisation and regression-gate runs, baseline comparison, and a human review queue for low-confidence cases. Ships with a detailed handbook on building reliable benchmarks.

**GPU Broker for MPL** · Next.js, Supabase, OpenRouter · private
A GPU advisor chatbot over a cloud provider's hardware catalogue. Lookup-first, with an animated UI and PostHog analytics.

**AgentRelay** · Node, Baileys, grammY, discord.js, MCP · [public, on npm](https://github.com/ShreySigh2912/agentrelay)
Self-hosted gateway that connects Gemini, Claude, and OpenAI to WhatsApp, Telegram, and Discord. One command to onboard, one to run.

### Community and automation

**Admission Bot** · Node, Slack Bolt · private
Production Slack bot that greets new members of the announcement channel, collects name and batch over DM, and invites them into the right batch channel with graceful fallbacks for every Slack error case.

**Cohort tooling** · React, Vite, shadcn/ui, Supabase · private
A set of smaller internal apps: cohort pulse surveys, a skill navigator for prospective learners, a learner hub, and a program discovery portal.

---

## Stack I reach for

| Layer | Tools |
|---|---|
| Languages | TypeScript (strict), Node 20, Python, SQL |
| Backend | Hono, Express, Inngest, Supabase, Neon Postgres, MariaDB |
| Frontend | React, Next.js 15, Vite, Tailwind, shadcn/ui |
| AI | Claude, GPT-4o, Whisper, OpenRouter, Voyage embeddings, MCP |
| Infra | Vercel, Render, Docker Compose, Caddy, Hostinger VPS, Cloudflare R2 |
| Ops glue | n8n, Zapier, Airtable, Superleap CRM, Slack, Zoom, Calendly |

---

## Public repositories worth opening

- [agentrelay](https://github.com/ShreySigh2912/agentrelay): AI agent gateway for WhatsApp, Telegram, and Discord
- [mcube-call-processor](https://github.com/ShreySigh2912/mcube-call-processor): call transcription and analysis pipeline
- [jo-scholarship-funnel](https://github.com/ShreySigh2912/jo-scholarship-funnel): scholarship application funnel

---

## Get in touch

If you run programs, work in institutional partnerships, or are building tooling for education operations, I am happy to compare notes.

Email: shreysingh29@gmail.com
