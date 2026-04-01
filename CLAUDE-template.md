# My App — Claude Code Instructions

@~/Documents/git/claude-code-quickstart/CLAUDE.md

---

## About This App

**Name:** <!-- e.g. Recipe Finder -->
**Purpose:** <!-- One sentence: what does this app do and for whom? -->
**Stack:** <!-- e.g. Next.js, Supabase, Tailwind CSS -->
**Key constraints:** <!-- e.g. mobile-first, must work offline, free tier only -->

---

## Project Structure

<!-- Describe the top-level folders once you've scaffolded the project.
Example:
- `app/` — Next.js app router pages
- `components/` — shared UI components
- `lib/` — utilities and API clients
- `supabase/` — database migrations and types
-->

---

## Key Decisions

<!-- Log important architectural or product decisions as you make them.
Example:
- Using Supabase Auth over NextAuth for simplicity
- All API calls go through `lib/api.ts`, never directly from components
-->

---

## Slash Commands

Use these commands during development (defined in `.agent/workflows/`):

| Command | When to use |
|---|---|
| `/brainstorm` | Starting something new — turn an idea into a design doc |
| `/plan` | Break an approved design into TDD-ready tasks |
| `/build` | Execute a plan using subagents and TDD |
| `/audit` | Review finished code for quality and UX |
| `/fix` | Resolve bugs and technical debt |
| `/log` | Log a bug, idea, or debt item to track later |
| `/teach-me` | Extract lessons from the session |
| `/closeout` | Wrap up — changelog, history, push |
