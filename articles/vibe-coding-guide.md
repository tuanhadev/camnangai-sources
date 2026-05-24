# Everything Vibe Coding

The complete guide to vibe coding — tools, prompts, production mistakes, and 17 articles from someone who's shipped 12 apps this way.

By Jenny Ouyang | Apr 21, 2026

**Last updated:** April 2026

---

## Introduction

Starting 2025, I've shipped twelve products using AI tools and plain English prompts, with hundreds of paying customers running in production.

Vibe coding got good enough that writing code myself stopped making sense.

That story is what this hub is about. There is a right order to learn it, a wall you'll hit at 80% of every first build, and mistakes that only show up after you've already launched. I hit every one of them.

I build AI systems and write about what happens when they run. Not what's possible. What actually works, and what breaks.

**Related hubs:** Claude Hub · AI Agents · Shipped Products · Substack Growth

---

## Quick Navigation

### What is vibe coding, and is it right for me?

Vibe coding means building apps with AI from plain English prompts. No programming background required. You describe what you want. The AI writes the code. You review and guide.

Most first-time vibe coders have a working prototype in an afternoon.

It also has a specific learning curve. Most beginners stall at 80% done. The articles below explain where that wall comes from and how to get through it.

#### What is the right roadmap for starting vibe coding from scratch?

Most guides point you to the tool. This is the map that comes before:

- The spec habit that separates shipped builds from abandoned ones
- What the first 30–60 minutes actually look like
- Where the 80/20 wall comes from and the two moves through it
- The 5-project arc from first loop to a system that runs itself

I went from ChatGPT to Cursor to Claude Code over eight months without this map. Writing it felt like writing the thing I needed at the start.

**Read:** How to Start Vibe Coding: The Roadmap Nobody Gave You

#### What is the right mindset and workflow for AI builders?

Most people start with the tool and skip the operating model. That's why they hit the same walls on every project.

This is the overview:

- What the AI builder workflow looks like day-to-day
- How to stay in control of what the AI produces
- What separates builders who ship from builders who keep starting over

Plain framing. No hype.

**Read:** The AI Builder's Playbook

**Start with the roadmap. Everything else builds on it.**

---

### How do I build my first AI app step by step?

Pick a project you would actually use. Plan the architecture before opening your coding tool. Build in phases. Deploy early, even before the app is complete.

The gap that kills most first builds is not the code. It is the distance between "it runs in preview" and "it works with real users." Planning before you build is what closes that gap.

#### How do I go from an app idea to a live web app in one session?

Most tutorials skip the part that matters: what happens between "it runs in preview" and "it survives real users." This one doesn't.

Real Replit billing upfront, including the $100/month trap most people hit. A ChatGPT planning session before any code is written. Five structured build phases: database, hosting, AI integration, deployment, production fix.

The "plan before you open the tool" step sounds obvious. I skipped it on every project until this one. Don't.

**Read:** How to Build an AI App with Vibe Coding: Zero to Launch

#### What does an actual AI tool build look like: the code, the decisions, the breaks?

Overflowing inbox. One afternoon. Cursor builds an AI-powered reading list that scores and summarizes emails automatically. Every decision shown, including what broke and what the fix looked like.

Written the day after the build, before the lessons faded.

The relevance scoring took three sessions to get right. The AI summarization was the easy part.

**Read:** How I Built an AI Email Digest App with Cursor

**Pick the walkthrough that matches your tool. The lessons transfer.**

---

### How do I write prompts that actually work in AI coding?

AI-generated code breaks in production because the prompt was wrong, not because the AI was.

Vague prompts produce clever-looking code that does not do what you meant. Constraint prompts produce boring code that ships.

Lock your architecture before you start building. Use constraint prompts to stop the AI from doing more than you asked for.

#### What is the best system for prompting AI to build any app?

Most failed builds start the same way: open the coding tool, type a prompt, figure it out as you go. This is the opposite. A 7-round conversation that locks architecture before any code is written. Works with Claude Code, Cursor, Replit, Lovable, or Bolt.

The projects where I skipped this were the projects I had to rebuild from scratch. Every time.

**Read:** How to Prompt AI to Build Any App

#### How do I get AI to write code that works in production, not just dev?

The AI is not the problem. The prompt is. Two fixes covered here:

- A 5-round conversation that locks architecture before any code is written
- Four debugging techniques that use screenshots and error logs together instead of text descriptions

Pasting a screenshot of the broken UI alongside the error message gets better results than three paragraphs describing it. That one change cut my debugging time in half.

**Read:** How Two Prompting Strategies Made My AI Code Production-Ready

#### How do I stop AI from adding features I didn't ask for or breaking things it just fixed?

The AI breaks working code while fixing broken code. It adds features you didn't ask for. It patches on top of patches until the source is untraceable. Four prompts that stop each of these:

- **Scope lock** — stops feature creep before it starts
- **Surgical change control** — touches only the files you name
- **Context preservation** — loads standards at the start of every session
- **Patch reset** — breaks the loop when fixing a bug creates three more

These feel restrictive the first time. That's the point.

**Read:** Master Constraint Prompts for Vibe Coding

#### Where do I get ready-to-use prompts and rules files for vibe coding projects?

Most vibe coders re-explain their project standards at the start of every session. Rules files end that. You write them once; the AI reads them automatically.

12 copy-paste prompts included:

- Planning prompts
- CLAUDE.md templates
- Debugging prompts
- Session handoff prompts

Rules files → less re-explaining. Less re-explaining → more building.

**Read:** Vibe Coding Prompt Templates and Rules Files

**The prompts are the shortcut. The methodology is what makes them work.**

---

### How do I make my vibe-coded app production-ready?

Your app works locally. Real users find it differently.

Security holes don't surface in development. Performance breaks under traffic, not in testing. The authentication break that's invisible in preview mode is critical after deployment.

Three fixes to make before you ship. Eight mistakes to avoid that only appear after you already have. One smoke test checklist that takes 30–60 minutes and a phone.

#### What vibe coding mistakes break apps after you ship them?

These are the ones that pass every dev test and break in production. The AI built them silently and never flagged them.

- Plaintext passwords in the database (caught it myself by looking)
- Dirty context causing AI to re-break things it just fixed
- The "works on my machine" fallacy
- Skipping version control
- Four more, each with a specific fix

I found my own plaintext passwords. Not because Claude Code warned me. It didn't.

**Read:** 8 Vibe Coding Mistakes That Break Apps After You Ship

#### How do I make a vibe-coded app safe and stable for real users?

Security holes → technical debt → skill atrophy. Three problems, roughly in that order. This covers what to do about each one, the role shift that makes it click, and a pre-ship checklist.

The "skill atrophy" section was uncomfortable to write. Still the one I send to people who say they're "just vibe coding for now."

**Read:** How to Make Vibe Coding Production-Ready Without Losing Your Mind

#### How do I test a vibe-coded app before I ship it?

Your app works on your machine. Real users break it differently.

3 phases. A browser, a phone, 30–60 minutes. No coding required. Catches mobile layout failures, production environment mismatches, and silent auth breaks your tests miss.

A payment double-charge bug. Found in Phase 2. Ten minutes. Would have been a support disaster.

**Read:** Your Vibe-Coded App Isn't Production-Ready — Until You Smoke Test It

#### What software engineering fundamentals do vibe coders actually need to know?

Not everything. Just the subset that prevents the failures AI won't flag.

- **Security patterns:** what to understand, not implement
- **Version control habits:** that prevent the "AI can regenerate it" fallacy
- **Error handling logic:** that makes debugging survivable

**Read:** The Essential Software Engineering Practices Every AI Builder Needs to Know

**Most of what breaks in production is preventable before you start building.**

---

### How do I plan a bigger vibe coding project?

Most AI builders treat planning like a formality. Prompt, get code, debug later.

That works for demos. It fails in production because the decisions that cost the most hours are invisible at prompt time.

**60 minutes of structured planning saves 23+ hours of debugging.**

#### What is the best methodology for planning a vibe coding project before writing any code?

5 rounds, one before you open the coding tool. Each round builds structure the next one needs:

1. Problem statement
2. Architecture
3. Data model (the one that hurts most when skipped)
4. Constraints
5. Master initialization prompt

Templates for every round. Worked examples included.

The rounds where I cut corners were the rounds that cost me time later. Every time.

**Read:** The 5-Round Planning Methodology: How 60 Minutes Saves 23+ Hours

#### What does the 5-Round Methodology look like applied to a real project?

Theory becomes obvious when you see it applied. AI Daily Digest. Zero to production in 18 hours. Every planning decision explained, every break documented, every architectural pivot shown.

Real timestamps. Real debugging sessions. Real costs.

This is the article I needed for my second project, when I had the theory but no reference point.

**Read:** Real Example: AI Daily Digest Built with the 5-Round Methodology

#### How do I prove the methodology works before I commit to it?

Three timed challenges, in order of commitment:

- **30 minutes:** ship one production-ready feature
- **2 hours:** add a database and proper architecture to an existing app
- **Weekend:** deploy a complete multi-feature app in 13 hours

Copy-paste templates and quality checklists for each.

Start with the 30-minute one. It changes your relationship to everything else in this section.

**Read:** Quick Wins: Tactical Challenges

#### What are the advanced vibe coding patterns for complex production systems?

The problems after "it works" are harder than getting it to work. Multi-API orchestration. State management. Background jobs. Production resilience under real edge cases, not just real traffic.

12,447 words. Everything in it came from a real failure.

This one required breaking things in production first. No shortcuts.

**Read:** The Production Playbook: Advanced Patterns

#### Where do I find the full paid vibe coding playbook in one place?

The paid library has a lot of pieces and they build on each other. This is the index: Quick Wins, Templates, Real Example, Methodology, and Advanced Patterns, with navigation between every piece.

Start here if you want to work through the full system in order.

**Read:** The Production-Ready Playbook for Vibe Coding

**If you're past your first project, start with the methodology. Then the advanced patterns.**

---

### Should I use Cursor or Claude Code for vibe coding?

Cursor is an IDE. It connects to your filesystem, GitHub, and databases. It has four modes: Inline, Ask, Agent, and Plan. Best for builders who want to see and control every change.

Claude Code is an agent. It runs in the terminal, reads your full codebase, and handles multi-file tasks autonomously. Best for builders who want to delegate more and supervise less.

Most serious vibe coders end up using both. Cursor for focused feature work. Claude Code for large-scale tasks and automation. Start with Cursor.

#### How do I set up Cursor and use it beyond autocomplete?

Most Cursor users stay in basic chat mode for months. This is 8 months of daily use compressed:

- The four editing modes and when each one becomes your main tool
- .cursorrules setup for persistent project standards
- MCPs for browser testing and database access
- Background Agents that keep building while you step away

**Read:** Cursor AI Setup Guide: Config, Models, and GitHub Integration

#### What actually changed in Cursor 2.0 and is it worth switching?

One week. Real builds. Parallel agents, 4x faster Composer, built-in browser integration, tested against actual projects, not release notes. Verdict by experience level included.

Parallel agents held up better than I expected. Running independent features in the same session changes how you structure a build day.

**Read:** Cursor 2.0 Is Rewriting the Future of AI Coding

**Start with Cursor. Add Claude Code when you want to delegate more and supervise less.**

---

### What do I need to know after my first app launches?

Shipping is when the real education starts.

Hosting choices cost money you did not expect. The 10/90 rule hits harder than most builders anticipate: 10% of the work creates 90% of the user-visible result. API costs sneak up fast between zero users and a few hundred.

#### What are the most important lessons from launching a first vibe coding app?

Everyone warns you about the code. Nobody warns you about hosting hell, the 10/90 rule, or what the first real users actually break.

Seven lessons. Written the week after launch, before the discomfort faded.

Lesson 3 changed how I scope every project. I thought I understood the 10/90 principle. I didn't.

**Read:** 7 Things Nobody Warns You About Launching Your First Vibe Coding App

#### How do I control API costs and choose the right model as I build more?

Your first API bill is small. Your second is not.

Once you have real users and more features running, model selection starts costing real money. This is the framework for picking the right model at the right cost, and the patterns that catch builders off guard between zero users and a few hundred.

"Use the cheapest model that works" sounds obvious until you see a week of bills from using the wrong model on everything.

**Read:** Cost-Effective AI Building Guide

---

## About This Hub

### Who is this for?

This hub is for people who've decided to try vibe coding, not people still deciding if it's real. It assumes you have a project idea, a basic sense of the tools, and a tolerance for learning by doing. Non-technical background is fine. No prior coding experience required.

### How is this different from the official Cursor and Claude documentation?

The official docs explain what the tools can do. I show what works in practice: the workflows, the failures, the workarounds they don't cover. The production-ready guide came from breaking real apps in production. The smoke testing checklist came from a payment bug I almost shipped. The planning methodology came from a refactor that cost me 23 hours of debugging I could have avoided.

### How often is this hub updated?

New articles are added as I publish them, typically weekly. The "Last updated" line at the top reflects the most recent sync.

---

## Key Principle

**Vibe coding isn't about the tools. It's about the judgment to know when to let the AI run and when to pull it back.**

---

**The Cursor guide, advanced patterns, and planning methodology are part of the paid Build to Launch library. Subscribe to get access.**

**The path through this library:** start → first build → prompts → production → planning → tools → launch.

**Every article above fits somewhere on that path. Start wherever you are.**

---

**Source:** https://buildtolaunch.substack.com/p/vibe-coding-guide
