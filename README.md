# TalentSpottingAI: build notes

Public notes on an AI-powered career platform I built solo with AI-assisted development. The production code is private; this repo documents what was built and how.

## What it is

TalentSpottingAI connects university students with employers and universities on one platform. Students get a job board and AI-powered matching ("matches based on fit, not just keywords"), free forever. Employers get curated candidates from 40+ Greek universities, plus a built-in applicant tracking system: staffing pipelines, talent search, NLP-based skills extraction, and event management with QR check-ins. Universities get real placement analytics for their career offices. Four role-based dashboards (Student, Employer, University, Admin) and 27 transactional email templates tie it together.

## Status, honestly

Developed July to December 2025. Launched early 2026 in a free-launch mode. Taken offline in April 2026 to eliminate roughly $50/month of infrastructure costs while there were no paying customers; the full deployment spec was captured first so it can be relaunched, and a landing page with a waitlist is live at [talentspottingai.com](https://talentspottingai.com). The numbers below were measured on the full product at hibernation, with a 100% test pass rate.

## The numbers, and how they were counted

Headline figures, kept deliberately conservative: **200,000+ lines of source code and 10,000+ automated tests.**

Measured at hibernation (April 2026): about 295K source lines plus 118K test lines, with documentation excluded from both counts, and 10,311 unit tests, 188 integration tests, and 888 end-to-end tests.

## Stack

Next.js, React, and TypeScript on the frontend; Node.js and TypeScript on the backend; PostgreSQL with Prisma; Redis, including a Redis adapter for multi-instance Socket.IO; Clerk multi-role auth; Stripe; Docker Compose for local development; GitHub Actions CI with sharded end-to-end runs; Sentry for error tracking; Resend for transactional email; Netlify for the landing page; DigitalOcean for the former staging environment.

## How a non-developer shipped this

I am not a developer by trade. The project ran on Claude Code with a disciplined context system, which is the part I would show a hiring manager:

- a project CLAUDE.md as the single operating manual, updated at the end of every session
- auto-loaded scoped rule files: testing rules, security rules, git workflow, infrastructure, documentation guides
- 85 documented working sessions with monthly archives
- 670+ recorded lessons, each written down the day it was learned, with the most important ones pinned into context
- database-safety and pre-commit verification protocols that keep the test suite trustworthy

## A few of those lessons

- Check the basics first (code paths, data types, environment variables, logs) before building a theory. This alone saved days of debugging.
- A successful build proves nothing about behavior. Every change gets functionally tested.
- Local behavior can differ from production behavior. Multi-instance Socket.IO silently drops events without a Redis adapter.
- Never run destructive migration commands against real data, and always back up before touching the database.

## Links

- Landing page and waitlist: [talentspottingai.com](https://talentspottingai.com)
- The live product I run: [yourjobremote.com](https://yourjobremote.com/en)
- LinkedIn: [dimitris-chatz](https://www.linkedin.com/in/dimitris-chatz/)
