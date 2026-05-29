# How to Use Vibe Coding Effectively as a Dev

*By Ankur Tyagi*

It may seem like everyone is a vibe coder these days, and prompting seemed like it would become the new coding. But is this AI-generated code really deployable?

Bragging on social media about a clever script is one thing, but pushing a vibe coded app to prod comes with many security risks.

With so many AI dev tools out there now, code reviews become more critical than ever.

This article will explore what vibe coding means and how code reviews should adapt in the era of AI.

## Table of Contents

- [What is Vibe Coding?](#what-is-vibe-coding)
- [How to Implement Vibe Coding in Practice](#how-to-implement-vibe-coding-in-practice)
- [Why isn't Vibe Coded Output Production Ready?](#why-isnt-vibe-coded-output-production-ready)
  - Context gaps are the first crack.
  - Those gaps lead directly to integration blind spots.
  - The most serious risk is security by omission.
  - Testing and correctness evidence are thin.
  - Operability lags behind.
- [Guidelines for AI Code Reviews](#guidelines-for-ai-code-reviews)
- [Code Review Process in Vibe Coding](#code-review-process-in-vibe-coding)
- [Checklist for Reviewing AI Generated Code](#checklist-for-reviewing-ai-generated-code)
- [How to Work Effectively with AI Tools](#how-to-work-effectively-with-ai-tools)
- [Conclusion](#conclusion)

---

## What is Vibe Coding?

In early 2025, AI researcher Andrej Karpathy popularized the term **vibe coding** to describe a new way of development in which you "fully give in to the vibes" and let AI write code while you focus on high level intent.

A developer expresses their desired functionality in plain language, and an AI system (like an LLM) generates the source code to implement it.

This code-by-prompt approach allows even beginners to produce working code without deep knowledge of programming languages. Karpathy joked that with advanced IDE agents (like Cursor's Composer mode), "I barely even touch the keyboard... I 'Accept All' always, I don't read the diffs anymore... and it mostly works".

So, vibe coding is coding by vibe and trusting AI to handle the heavy lifting.

---

## How to Implement Vibe Coding in Practice

In practice, vibe coding usually involves using AI assistants and adapting your workflow to a more interactive, prompt-driven style.

Here's an overview of how you can "vibe code" a project:

### Step 1: Choose an AI assistant

Select a development env that supports AI code generation. Popular choices include Cursor and GitHub Copilot.

### Step 2: Define your requirements

Instead of writing boilerplate code, describe what you want to build. Provide AI with a specific prompt detailing functionality. The more context and detail you give, the better AI can fulfill your intent.

For example, when running an SEO inspection for the website DevTools Academy, this prompt was used in Cursor:

> "Now, act as a senior product engineer and UX strategist. Evaluate and improve https://www.devtoolsacademy.com with a practical, no-fluff lens.
>
> Scope:
> - UX
> - SEO and technical SEO
> - Positioning and messaging
> - Copywriting and information architecture
> - What to add to stand out in the developer tools space."

This prompt works well because it gives the AI a clear role, a defined scope, and a specific intent. AI knows it's not just fixing SEO but also reviewing how the site communicates value to devs. That combination of clarity and context produces actionable insights instead of surface-level suggestions.

### Step 3: Review the code

AI will produce initial code based on your prompt. Think of this as a prototype – it's not perfect. Run the code and see how it behaves.

For example, CodeRabbit can review pull requests on GitHub. When pushing a small fix to sort blog posts correctly and make sure the RSS feed reflects the latest publish date, CodeRabbit analyzes the diff, understands the intent behind the change, and explains exactly what the new code does.

It pointed out that the fix now sorts posts before mapping them, uses the sorted data for both items and the lastBuildDate, and ensures proper chronological order throughout the feed.

It's like having a senior reviewer who not only checks syntax but also validates logic and confirms that your reasoning holds up.

This is a reminder to expect imperfections. Vibe coding embraces a "code first, refine later" mindset. This means you get a working version quickly, then iteratively improve it. You might go through a few cycles of: **prompt → code → test → tweak**.

### Step 4: Validate, debug, polish

Once AI generated code meets your expectations, do a final review.

Throughout the process, the core idea is that you collaborate with the AI. The AI agent serves as a coding assistant, making real-time suggestions, automating tedious boilerplate, and even generating entire modules on your behalf.

---

## Why Isn't Vibe Coded Output Production Ready?

Vibe coding moves fast: you describe intent, the AI produces something that runs, and you're off to the next prompt. What's missing is the slow, unglamorous work that usually turns a draft into shippable software — like shared context, architectural alignment, verification, and documentation.

AI generates plausible code based on patterns it has seen. But it doesn't understand your team's history, your system's constraints, or the implicit rules that keep everything coherent over time.

That mismatch shows up the moment a "works on my machine" demo meets a real codebase.

### Context gaps are the first crack.

AI only sees what you show it, so it's easy for it to make the right local choice and the wrong global one: duplicating logic that already exists, choosing defaults that conflict with prior decisions, or introducing functions that don't respect domain boundaries.

The result is code that looks reasonable in isolation but collides with existing assumptions and conventions once integrated.

### Those gaps lead directly to integration blind spots.

Drafts often ignore the lived details of your environment – shared utilities, cross-cutting concerns, configuration, deployment hooks, and operational policies. Interfaces may line up at a glance and still fail at runtime because the draft doesn't fit how your system composes modules, handles errors, or manages state across services.

### The most serious risk is security by omission.

AI rarely includes robust input validation, clear authentication and authorization paths, or rate limiting unless you spell it out. Secrets handling and logging tend to be superficial or missing. That leaves common exposure points like request handlers, job processors, and webhook endpoints without the checks that prevent injection, SSRF, mass assignment, or data exfiltration.

Even when the surface looks tidy, the absence of explicit security controls means you're trusting defaults you didn't choose.

### Testing and correctness evidence are thin.

Quality suffers in quieter ways, too. Beyond "it runs," there's little to demonstrate behavior across edge cases or to guard against regressions.

Performance and scalability remain unknowns: extra network calls, N+1 patterns, and quadratic loops sneak in because nobody measured them. Dependencies and environments drift as versions aren't pinned, infrastructure isn't declared, and configuration lives only in the author's head, making behavior differ across machines and CI.

### Operability lags behind.

A lack of metrics, missing health/readiness probes, and no runbook make failures harder to detect and slower to recover from. Add in data quality and compliance concerns (PII handling, encoding assumptions, transitive license obligations), and you have code that demos well but isn't ready for production's reliability, security, and audit demands.

In short, vibe-coded output accelerates drafting but skips the shared understanding and evidence that make software safe to ship.

Until those gaps are closed, it's a prototype, not a release.

---

## Guidelines for AI Code Reviews

Your team should keep pre-AI engineering standards as the bar, including security, tests, readability, maintainability, performance, and docs. AI should change how fast you gather the evidence for those standards, not how much evidence you require. In other words, use AI to accelerate the path to your existing bar, never to lower it.

Using AI, you can generate code at speed. But if reviews take the same amount of time (or more time), you lose some of the benefit. The goal isn't to relax standards, it's to shorten the time to prove you met them. That means layering in automation (tests, static analysis, secret scans, SCA) and AI-assisted review to catch obvious issues quickly so human reviewers can focus on intent, architecture, and risk.

Well-used assistants can help here. Tools like CodeRabbit, GitHub Copilot PR Reviewer, Claude Code, Cursor's Bugbot, Graphite's AI Review, and Greptile can highlight potential bugs, security gaps, style deviations, and mismatched intent, and summarize diffs for faster context. Treat these as accelerators for your existing process, not as replacements for judgment.

---

## Code Review Process in Vibe Coding

The fundamentals of good code reviews haven't changed – and in fact, they're more critical now.

Below are some key principles to maintain speed without sacrificing quality.

### 1. Trust, but verify.

A reviewer usually assumes the author understands the system. With vibe-coded output, the "author" may be an AI with limited context. If something looks odd or unnecessary, question it. Run the code, add/execute tests, or ask the developer/AI for clarification on intent and constraints.

### 2. Don't let reviews become a bottleneck.

Vibe coding generates code quickly. If human review takes as long as hand-writing the change, you've erased the gain.

Combat this by front-loading automation: run unit/integration tests, static analysis (lint/SAST), secret scans, SCA, and basic perf checks in CI to clear the noise. Then reviewers spend their time on design trade-offs, boundary cases, and risk. The balance is: high standards, faster evidence.

### 3. Use AI code reviews wisely.

AI can help review code just as it helps generate it. Modern "pair reviewer" tools scan a PR and surface likely bugs, security issues, missing tests, or style violations in minutes plus give natural-language summaries of the change.

Tools you can consider include CodeRabbit, GitHub Copilot PR Reviewer, Claude Code, Cursor Bugbot, Graphite, and Greptile. Many integrate with the CLI/IDE and GitHub/GitLab to leave actionable comments.

Think of them as fast first-pass reviewers that increase coverage and consistency across PRs.

### 4. Human judgment is still irreplaceable.

Even the best AI reviewer is an assistant. Keep humans accountable for correctness, security posture, architectural fit, and user impact. A healthy pattern is: AI first-pass → human second-pass that inspects invariants, failure modes, and long-term maintainability.

### 5. Maintain a high bar for quality.

It's tempting to accept "it runs" when an AI wrote it. Don't. Stakeholders still expect software to be robust, secure, and maintainable. Keep DRY, readability, and testability standards. Insist on input validation, authZ checks where relevant, and sensible logging/metrics. If you can't provide evidence that you met the bar, you haven't met it.

### 6. Educate and document.

When reviewers find bugs or security flaws in AI-generated code, capture the lesson.

Update internal guides with patterns like: "When generating handlers, validate and bound inputs, add rate limits, log request IDs, avoid N+1 queries, and sanitize user-visible output." Over time, bake these into prompts, templates, repo scaffolds, and CI checks so the next AI draft starts closer to done.

---

## Checklist for Reviewing AI Generated Code

Before approving any vibe-coded change, make the standards explicit and verifiable. Use this checklist to confirm behavior, security, performance, integration, and documentation so the draft you got from AI becomes code you can safely ship.

### 1. Define the code's purpose (scope & non-goals).

Be explicit about what this change does and does not do. Tie it to a user story/ticket and call out non-goals so "helpful" AI changes don't creep in.

### 2. Verify behavior and edge cases.

Be clear about what you're verifying. For example, verify input parsing and pagination boundaries, verify that error paths return the correct status and body, and verify that database writes are idempotent. Run existing tests, add missing unit/integration tests, and reproduce edge inputs (empty, null, huge, unicode).

### 3. Perform code-quality checks (readability, DRY, refactor needs).

AI often produces verbose or duplicated logic. Ensure names are meaningful, side effects are clearly stated, and duplication is removed or minimized. Run linters/formatters, collapse repetition, and extract helpers where they aid clarity.

### 4. Analyze organization and structure.

AI writes code in isolation. Confirm the change uses existing utilities, layers, and boundaries (domain/services/controllers/jobs). Check imports and module placement, avoid reinventing existing helpers, and align with repository conventions.

### 5. Validate inputs and assumptions.

List the assumptions the AI made (default locale/timezone, allowed ranges, required fields). Add schema validation (DTO/class validators/JSON Schema). Handle empty, null, over-max, non-ASCII, unexpected enum, and malicious strings. Enforce limits/timeouts.

### 6. Perform security audits (minimum pass).

- **AuthN/AuthZ:** Confirm endpoint checks identity and authorization paths; deny-by-default.
- **Inputs:** Sanitize/validate inputs, prevent injection (SQL/NoSQL/command), and escape user-visible output.
- **Secrets:** No secrets in code/diff/logs, use env/secret manager, and rotate any test keys.
- **Abuse controls:** Add rate limits, size limits, and timeouts on network and disk operations. Run SAST/secret scan/SCA, and fix or justify findings.

### 7. Do a performance evaluation.

Look for N+1s, needless network calls, unbounded loops, quadratic sorts. Add a micro-benchmark or run a quick load test for hot paths. Set sensible cache/timeout/retry with jitter where applicable.

### 8. Manage dependencies (pin, justify, minimize).

Review any new libraries. Are they necessary? Maintained? License compatible? Pin versions, add lockfiles, or remove unused transitive adds.

### 9. Review documentation.

Ensure the docs are in line with the code. AI often changes some parts or adds code blocks at different places while resolving various issues. These changes might not make it into the docs.

### 10. Observability (see problems early).

Use structured logs with request/trace IDs, key counters/timers (success/error/latency), health/readiness probes, and a basic dashboard or alert stub.

### 11. Compliance and data handling (when applicable).

Identify any personally identifiable information (PII), document collection/retention, ensure masking/redaction in logs, verify dependency licenses and data-residency constraints.

---

## How to Work Effectively with AI Tools

At this point, you can probably see why it's very important to understand the actual skills involved in AI-assisted development.

There's a pretty big difference between an experienced developer who uses AI tools to help them get more done, and a newbie who thinks AI can build the next Facebook or Google just with a simple prompt.

An inexperienced dev will ask AI something like:

> "Hey, Build me Twitter and make no mistakes"

But an experienced developer who has solid fundamentals might say something like:

> "AI, we're building a Twitter replica. Use $SQL_Database, Use $Language, Avoid $Common_Pitfalls, Follow $Standard_Practices."

> "The generated code is prone to X problem, implement this fix."

> "Implementation of $X is flawed because of $Y, do $Z instead."

So as you can see, you still need to know the how's and the why's and what depends on what. Often you'll just need to make the changes manually, because it will be faster. And you don't want to outsource the critical thinking part, which is the part that AI can't actually do.

LLMs are good at information retrieval. If you know nothing about what you're looking for, then asking an AI isn't going to be that helpful (or that reliable). But if you have an idea, some background knowledge/context, and the skills to verify AI's responses, then it can be really helpful.

A practical coding loop looks like this: draft with Claude Code (or Copilot/Cursor), open a PR, and let an AI reviewer like CodeRabbit (or Copilot PR Reviewer / Cursor Bugbot or Greptile) do the first pass. CI runs tests and scans. Repeat until everything's green and the PR is ready to merge. It's fast, but it's still disciplined.

---

## Conclusion

AI-generated code can boost productivity – but production value still comes from software that is robust, secure, and maintainable.

Mindless code generation creates technical debt. But when you integrate AI thoughtfully, with guardrails, verification, tests, security checks, and documentation, you can go faster without lowering your standards.

If you have any questions about code reviews, engineering, startups, or business in general, find Ankur on Twitter: [@TheAnkurTyagi](https://twitter.com/TheAnkurTyagi).
