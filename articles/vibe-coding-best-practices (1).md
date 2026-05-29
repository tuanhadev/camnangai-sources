# Vibe Coding Best Practices: Avoid the Doom Loop with Planning and Code Reviews

**Teresa Torres**

*01 Apr 2026 · 49 min*

I've written more software in the past six months than I've written in my entire lifetime.

I started vibe coding in March 2025. My first foray was extraordinarily successful and then resulted in complete failure. I was blown away when Replit helped me build a custom chat interface for my first Interview Coach, but was extremely disappointed when I couldn't extend it. I ended up rebuilding the Interview Coach from scratch—the old-fashioned way, writing one line of code at a time.

Fast-forward a couple of months and I had moved to Lovable. I had some ups and downs. I tried to build a custom health tracker for my dog and wasted a full weekend trying to get Lovable to fix bugs. I eventually gave up, killed the project, and started over. I was surprised when Lovable got it right on the second try in less than an hour. Starting over was the key.

Since then, I've moved to Claude Code for all of my AI coding and I'm building real production products. I've built an Interview Coach, a Business Fundamentals Coach, and an Outcome Coach for our courses. I'm building AI-generated Interview Snapshots and Opportunity Solution Trees for Vistaly. I built challenge software (a scoring system, leaderboards) to support the challenges we run in our on-demand courses. I integrated a TeresaBot into my Slack community that answers members' questions by searching everything I've ever written. And I've built countless utilities that I use to run my business.

It's empowering to have an idea and to be able to build it. But even in the best vibe coding tools, it's not always smooth sailing. I've had to level up to be able to graduate from compelling prototype to real production software. Today, I want to help you do the same.

We'll cover:

- What vibe coding is
- The most popular vibe coding tools and which to use when
- Where vibe coding breaks down (and how to fix it)
- The two feedback loops that took me from broken prototypes to production software: plan-review-fix and implement-review-fix
- How to debug when things go wrong

And paid subscribers will get:

- Full transcripts of my actual conversations with Claude so you can see how this works in practice.
- Downloadable skills to help you apply these ideas yourself.

## What Is Vibe Coding?

Vibe coding is a way to create software—not by writing code—but by describing what you want in natural language and letting an AI write the code for you.

The term was coined by AI researcher Andrej Karpathy in February 2025. He described a new way of working where you "say stuff, run stuff, and copy-paste stuff, and it mostly works." You don't write code line by line. You describe what you want, the AI generates it, and you react to what you get.

In the year since Karpathy named it, vibe coding has gone from a novelty to a legitimate way to build software. The tools have matured, the output quality has improved, and people with no engineering background are building real products. It's clear that vibe coding works. The question now becomes what can we build with it.

## Vibe Coding Tools: Compare and Contrast

Not all vibe coding tools are created equal. They fall into two broad categories: vibe coding apps that handle everything for you (hosting, database, deployment) and AI coding agents that give you more control but expect you to manage the infrastructure yourself.

If you're just getting started, start with a vibe coding app. When you're ready for more control—or when you hit the limits of what a vibe coding app can do—move to an AI coding agent.

### Vibe Coding Apps

| Tool | Known For | Pick This One When... |
|------|-----------|----------------------|
| Base44 | Now owned by Wix. Fastest path from description to working app. The least to learn. | You want to describe what you need and get a working app with the fewest steps possible. |
| Lovable | Visual editing—click on any element to modify it. Native Supabase integration for database and auth. Multiple building modes. | You want to see and tweak what you're building as you go, with a real backend behind it. |
| Figma Make | Turns Figma designs into working apps. Lives inside Figma, so designers can go from mockup to functional prototype without leaving their tool. | You already work in Figma and want to turn your designs into real, interactive apps. |
| Bolt | Full dev environment running in the browser—no setup, but you can see and edit the code if you want to. Figma import. | You want the speed of an app builder with the option to look under the hood. |
| Replit | The most complete all-in-one platform: editor, database, hosting, deployment, collaboration. 50+ languages. | You want everything in one place and never want to think about infrastructure. |
| v0 | Made by Vercel (the company behind Next.js). High-quality code output. Git integration with branching and PRs. | You want hosting that scales from prototype to production and a more developer-oriented workflow. |

### AI Coding Agents

| Tool | Known For | Pick This One When... |
|------|-----------|----------------------|
| GitHub Copilot | The original AI coding assistant. Deepest GitHub integration. Free tier. Agent Mode for autonomous tasks. | You're already in the GitHub ecosystem and want the easiest entry point. |
| Codex | OpenAI's coding agent. Runs tasks in parallel cloud sandboxes. Can work on multiple tasks at once and propose PRs. | You want to assign tasks and let the AI work independently, then review the results. |
| Claude Code | Terminal-based AI agent with a 1M token context window. Strong reasoning and code quality. | You want the most capable AI for complex, multi-file projects. |

I personally have used Replit, Lovable, Codex, and Claude Code. Claude Code is my current tool of choice. But I still like Lovable for toy projects (like my dog's health tracker) where I don't want to think about the UX, but want it to feel nice.

I chose not to include integrated-development environments (IDEs) like VS Code, Windsurf, and Cursor in this list. But many of them have their own coding agents built in. Cognition also makes a coding agent Devin, but it also didn't seem to fit here.

Finally, I didn't include Magic Patterns or other design-only prototyping tools, as our focus today is on building apps.

## Where Vibe Coding Breaks Down (And How to Fix It)

Once you choose a vibe coding app or AI coding agent, it's time to start building. You can literally type what you want and the agent will build it for you.

But this is where most projects start to go wrong. If you aren't sure what you want or you change your mind, you can end up with a lot of messy code.

### The Vibe Coding Doom Loop

Every vibe coder eventually has the experience where they end up in the vibe coding doom loop. They encounter a bug, the agent says it fixed it, but it's not fixed. No matter what you say or do, the agent struggles to fix it. It can be incredibly frustrating.

These types of problems tend to arise for a few reasons:

- You weren't clear about what you wanted.
- You changed your mind a lot and the code reflects all those twists and turns.
- The agent switched technologies midstream and different parts of the code base use different technologies (usually the result of the requirements changing too much).

### Understanding 3 Software Layers: Data, Controller, View

To avoid this fate, it's important to understand a little bit about how software works. Software has three layers: the data layer (where the data is stored), a controller layer (the logic of how the software works), the view layer (what you see in the interface).

Most of these problems arise when these layers are out of sync. When you initially tell an agent what you want, it makes assumptions about what data will need to be stored, how the logic will work, and what to display in the interface. When you change your mind, the agent has to remember to update all three of these layers.

If you ask for a simple interface change, it might only affect the view layer. The agent will probably handle this well. But if it's a complex interface change, maybe you want to change how things are sorted, this might affect all three layers. The agent might need to change how the data is stored and how and when it's retrieved, so that it can change how it's sorted in the interface.

This is where coding agents tend to make mistakes. Intractable bugs appear when the agent forgets to make changes across all three layers. Or it makes inconsistent changes across the three layers.

### My Experience with the Vibe Coding Doom Loop

This is what happened with my dog's health tracker app. As I iterated on the app, my requirements changed. I added new things that I wanted to track. I wanted to optimize the interface to make data entry easy, but some of my refinements meant we had to store data differently. The more changes I made, the more subtle bugs were introduced into the app.

And this compounds over time. As the agent works, it tends to follow the patterns of what's in the code it's looking at. If it's looking at an outdated view layer, it might make bad decisions when updating the data layer.

This is why starting over worked. When I described the app the second time, I knew exactly what I wanted. My requirements didn't change. Lovable was able to build the three layers correctly and I got exactly what I wanted.

### Two Principles Help Us Avoid the Vibe Coding Doom Loop

If you want to avoid the vibe coding doom loop, you have to keep two key principles in mind as you work:

1. The clearer you are about what you want, the better output you'll get from the agent.
2. Agents make mistakes. It's our job to manage those mistakes.

We can fumble our way through the vibe coding doom loop—like I did with my dog's health tracker—or we can learn a better way.

Next, I'll introduce two agent cycles that will help avoid the vibe coding doom loop:

- The **plan-review-fix cycle** will help you get clarity on what you want.
- The **implement-review-fix cycle** will help you catch and fix agent mistakes.

Let's dive in.

## The Plan-Review-Fix Cycle: Clarify What You Want

Every good product manager knows an idea sounds great in theory right until you start to spec it out. The details are where it all tends to fall apart.

When we work through the details as we vibe code, we are working through the details in code. This is expensive—even when an agent is writing the code. It's also likely to lead to bugs. The agent makes mistakes. Every time we change our mind, we incur a little more tech debt—vestiges of the old ideas still hanging around in the code. This tech debt confuses future agents who are working in the code, which leads to a vicious cycle of more and more bugs.

To avoid this fate, I always start with a plan. Instead of iterating in code, I iterate on the plan. And, of course, I do this with the vibe coding agent.

Sometimes I start with a vague idea and I work with the agent to make it more concrete. Other times I have a very specific idea and I just need to write it down. Either way, every vibe coding session starts with a plan.

Now when you hear plan, you might think product requirements document or technical specification. But most of us are familiar with these artifacts in the context of project-based work, and I want to be clear, I'm still working in small, iterative batches.

I recently built a TeresaBot—an agent that answers questions about product discovery. I have a grand vision for TeresaBot. I want it to be a versatile discovery coach. But I know it will take time to get there.

My first goal was to give TeresaBot access to all of my writing, so it could answer the many questions I get where I already have a written answer. But I didn't know how to make this happen. I turned to Claude for help and we started to work through a plan.

Claude outlined how it could work end-to-end. It explained things that I didn't know about. It helped me choose vendors (like a vector database and an embeddings API). As we discussed, I added and refined my requirements. We iterated together in markdown, not in code.

Once the plan was in good shape, we didn't just start coding. Instead, I ran the plan through my AI plan-reviewer—this is a skill that you can download below. This step is key.

Over the course of my initial conversation with Claude, Claude is learning my preferences (that's good) and my biases (that's bad). It inherits my blind spots. We are both likely to forget key details that will cause issues once we start implementing. The plan-reviewer's job is to evaluate the plan from a fresh perspective.

The reviewer verifies that the plan is consistent with the project's coding patterns and architecture. It makes sure that we aren't over-engineering anything. It identifies logical flaws, gaps in our thinking, blind spots, or anything else that is notable to call out. It doesn't fix the plan, it just reports back.

I then share the plan reviewer's feedback with the planning agent and we work together to integrate the relevant feedback. We repeat this cycle until all three parties are happy: me, the planning agent, and the plan-reviewer.

I find that this cycle is critical for avoiding the doom loop where coding agents struggle to fix bugs. Starting with a strong plan means we aren't thinking in code. We are thinking in markdown and only coding when we are sure we know what we want—at least for the first small chunk.

As you plan with the coding agent, keep the following best practices in mind:

- **Start fresh conversations often.** The longer you talk to an agent the worse the performance you'll get. This is due to a phenomenon called context rot. I often plan in chunks. I'll start with the high-level overview of what I want, work to understand what the end-to-end process might look like, document it, and then start a new conversation. In the next conversation, I might dive deeper into one area of the plan. When we are done, I'll clear the context and dive into the next section. This ensures that I'm always getting high-quality output from the agent.
- **Don't just rely on the agent's training data.** I often ask a second agent to do research on whatever we are building. I ask it to research the best strategies and identify the most common mistakes people make. I then feed this report back into the planning agent.
- **Question the agent's suggestions.** If something sounds off or you aren't sure about an agent's suggestion, ask it to clarify or even justify its answer. You might not be an expert, but you should still understand the choices and make sure you are choosing the right path. And on that point ...
- **Ask the agent to explain anything you don't understand.** If there's anything you aren't familiar with or don't understand, just ask the agent to explain it to you. If you still don't understand, tell the agent what confuses you and ask it to explain again. Remember, agents are infinitely patient.

Planning can take time. It's a lot of work. But it pays off. It sets the agent up to build the right thing from the very beginning.

Later, I'll share a full transcript of one of my planning sessions with Claude. You'll see exactly how I put these tips into practice and how much time I spend in planning. Then I'll share a transcript of our implementation session and you'll get to see just how seamless it is. The planning paid off. It always does.

## The Implement-Review-Fix Cycle: Catch and Fix Coding Agent Mistakes

Once the plan is ready, I start a fresh conversation. This resets the context window and helps to avoid context rot. I ask the new agent to implement the plan.

If planning went well, the agent should be able to work on its own to implement the plan. When it's done, its inclination is to ask me to test the changes. But I don't do this yet. Instead, I want an agent to check the coding agent's work.

That's what the AI code review is for. The AI code-reviewer reads the plan, scans the code base, and evaluates the changes. It looks for bugs, duplicate code, and new patterns or technologies that are not needed. It looks for over-engineering.

The primary goal of the AI code-reviewer is to help us avoid the vibe coding doom loop. It makes sure that the coding agent follows good software engineering practices.

There are three areas where I have the code-reviewer spend extra time: error handling, test coverage, and security. I was not an expert in any of these topics when I started vibe coding. But I've learned a lot along the way. I'll highlight some basics here. And, of course, you can download my code-reviewer skill at the bottom of this article.

### Error Handling

If you aren't familiar with error handling, it's basically how you tell your code to respond when something goes wrong. Let's say your code calls an API. What will your code do if:

- The API is unavailable
- It doesn't have the right credentials to access the API
- It gets an unexpected response from the API

We often write code for the happy path—when everything goes well. Error handling is how we enumerate the problematic paths and what to do when they occur.

You don't need to know how error handling works in code. The agent can handle that. But you should ask, "What could go wrong with this step?" and "How do we want to handle each instance?" You can then talk through these decisions with your coding agent.

I specifically instruct the code-reviewer to look for gaps in error handling. I ask it to highlight missing coverage. If I'm not sure how to fix it, I discuss it with the coding agent. The key is to get an expert to review it for you. That's what you get from the code-reviewer.

### Test Coverage

The code-reviewer also looks for test coverage. Do we have comprehensive unit tests and integration tests? Do the integration tests cover all of the actual usage patterns?

For those of you new to automated testing, unit tests test pieces of code in isolation (e.g. does this function do what it is supposed to do?). Integration tests test how all the pieces work together. You don't need to know how to write either. But if you want your code to work reliably, you do have to know enough to tell Claude to write the right tests.

Claude is great at writing unit tests. It is not great at writing the right unit tests. So the code-reviewer checks its work. Claude almost never remembers to write integration tests. So the code-reviewer explicitly looks for both.

For integration tests, I instruct the code-reviewer to make a list of all of the ways the code might be used and we decide which ones need integration tests based on how we plan to use it.

### Security

Early vibe coding tools were not very good at security. Many, thankfully, have gotten much better. You might even notice that your favorite tool has its own security check. This is a great starting point.

I asked Claude to help me write security review instructions for the code-reviewer. It looks for a wide variety of common security gaps like:

- Dependency vulnerabilities: outdated packages or hallucinated package names
- Secrets in code—no exposed API keys or other credentials
- IAM roles are properly scoped to least-privilege access
- Input validation
- Logging hygiene (no sensitive data gets logged)
- CORS access

You don't need to know what all of these things are. The key is to ask the coding agent to help you make sure your app is secure and to have the code-reviewer verify it.

### Sharing the Reviewer's Feedback with the Coding Agent

The code-reviewer (like the plan-reviewer) doesn't fix the issues that it finds. Instead, it writes a report of its findings. I review it and share it with the coding agent.

I used to let the coding agent call the reviewer and let them iterate. But I found that this can lead to endless cycles of fixing things that don't really need fixing. So I like to stay in the loop.

Just like with planning, the code isn't done until all three parties are happy: me, the coding agent, and the code-reviewer.

I can't tell you how many bugs have been surfaced through code reviews. This seems like a burdensome step, especially if it looks like the code just works. But I promise this will save you time in the long run.

## Vibe Coding Debugging: How to Recover When Things Go Wrong

Even if you follow the plan-review-fix and implement-review-fix cycles diligently, things will still go wrong. Remember, agents make mistakes.

But don't panic. Odds are another agent can help you resolve the issue. When you encounter a bug that the coding agent is struggling to fix, don't let it keep trying. This is where you are likely to introduce even more bugs.

Instead, start a new conversation. Ask a new agent to look at the problem. Tell it specifically, "Just diagnose and report back, don't fix." This is important. You don't want it to just start changing things.

If it's a particularly hard bug, I might spin up two or even three agents with the exact same prompt. I want to see if they converge on a single diagnosis.

Only when I'm confident the agents have found the real issue, do I let them write any code.

It's really easy to think one thing is the problem, when it's not. If you let an agent just start fixing things, they are going to change a lot of things that don't need changing. This opens the door to even more bugs.

Always separate diagnosing from fixing.

## What This Looks Like in Practice

It's one thing to read about this process. It's another to see it in action. That's why I'm going to share with you some of my real conversations with Claude.

We'll look at:

- How I planned my initial TeresaBot with the help of Claude
- What the plan-reviewer flagged and how we acted on it
- What the code-reviewer flagged and how we acted on it

And as an added bonus, I'll share my plan-reviewer and code-reviewer skills with you, so that you can put these ideas into practice today.

## Plan-Review-Fix Cycle for TeresaBot with Claude

The following is a real planning session that I recently did with Claude. It's quite long. I am including all of it, so you can see how much time I spend in planning. I know it's a lot. But I this saves me countless hours when it comes time to implement. After going through all of this planning, Claude is able to build the right thing. I haven't encountered the vibe coding doom loop in many months.

**Teresa:** I want to talk through a new idea. I'd like to create an mcp server or an agent for Product Talk. I have a ton of content on my site and I'd like to create a way for readers to find what they are looking for easier whether they hit my website (through a chat agent) or through an LLM (via MCP).

> *This starts as a vague idea. I'm not quite sure what I want. But you'll see over the course of the conversation, it turns into a solid plan.*

**Claude:** This is a great idea. There are a few different angles here, so let me ask some clarifying questions to understand what you're envisioning.

These could share the same underlying content index but have different interfaces.

Questions to help shape this:

Content scope - What types of content should be searchable? Blog posts, podcast episodes, course descriptions, the book, newsletter archives? All of it?

Goal for readers - Should it primarily point people to the right content (like a smart search/recommendation engine), or should it also synthesize answers from your content (more like a knowledge base chatbot)?

Attribution matters - I'd assume you want answers to always cite/link back to specific articles or episodes. Is that right?

Volume - Roughly how much content are we talking about? Hundreds of blog posts? How many podcast episodes?

Priority - Which use case feels more valuable to start with - the website chat agent or the MCP server? Or are you thinking of them as one project?

Let me know where your head is at and we can start mapping out what this would look like.

**Teresa:** 1. all of it - and I might want to distinguish between a paid one and a free one
2. both - tldr + links
3. yes
4. about 400 blog posts, about 80 podcast episodes
5. both, same project, 2 different interfaces

> *Notice how I added a new requirement: free vs. paid content. This is the type of change that if it happens in code, it requires changes the data layer. If it's not propagated through to the controller and view layers, you'll get bugs.*

**Claude:** Got it. So the core of this is a content knowledge base with two interfaces on top. Let me think through the layers:

**Layer 1: Content Index**

~400 blog posts + ~80 podcast episodes + book content + course descriptions + newsletter

Each piece of content gets chunked, embedded, and stored in a vector database

Metadata tagging: topic, content type, free vs. paid, date, URL

This is the foundation everything else builds on

**Layer 2: Retrieval + Synthesis**

Query comes in, find the most relevant content chunks

Generate a concise answer synthesized from your actual content

Always include source links

Filter by free vs. paid based on which tier the user has access to

**Layer 3: Interfaces**

Website chat widget - embedded on producttalk.org

MCP server - exposes your content as tools LLMs can call

---

*[Article continues for paid subscribers]*
