# A Practical Guide to Getting Stuff Done with Vibe Coding

**By Rakesh Gupta**

*Aug 14, 2025*

We recently announced our $156mm series C after tripling our revenue two years in a row. Growth like this strains every business process — how do we maintain this trajectory? How do we deliver the same quality of service when we're 10x larger than two years ago?

Great problems to have, except our product management team was drowning in customer data and requests from sales to help technically qualify new opportunities for our rapidly-expanding product. So I spent a few afternoons vibe coding with Claude Code to automate both problems away.

But what I learned about vibe coding with AI turned out to be much more valuable than the time saved.

## The setup

I built two things:

- An automation that regularly scans Salesforce for new qualified opportunities, analyzes their Gong transcripts, and writes technical fit assessments for each to Notion.
- A system that generates weekly customer health reports & activity snapshots from the previous week's Gong conversations and JIRA support tickets.

Both work great, saving us many hours weekly and connecting previously siloed data (kind of like what our product does for observability…). One of our company values is "run towards the smoke," and these automations help us spot both smoke and opportunity.

But building them taught me that successfully coding with AI requires way more software engineering fundamentals than people admit.

(Why not use off-the-shelf solutions? Nothing we tried, including the AI features in these products, gave us the flexibility to tailor solutions to our specific needs.)

## Lesson 1: You can't skip engineering design (even with AI)

My first attempt was true "vibe coding" — just prompting Claude Code to build stuff. It worked until it didn't. On more than one occasion, it rewrote the entire codebase with a different architecture, which introduced a bunch of regressions that slowed me down considerably.

I realized engineering teams solved this decades ago: design first, code second. I asked ChatGPT to write an engineering design doc considering multiple approaches (Python scripts? Web app? Zapier?). Only after choosing an architecture did we start coding.

Feeding that design doc to Claude Code had a big impact. With a clear design, it stopped making radical changes when hitting problems. Those radical changes were the cause of cascading bugs.

## Lesson 2: AI needs management 101

A design doc wasn't enough to keep Claude Code on track. Its assumptions about what I wanted for each individual task were consistently wrong. So I tried basic management techniques:

**Before starting each task:**

- Asked it to repeat my goals until I was certain it understood
- Had it create a verifiable task list
- Explicitly told it not to write code until we agreed on the approach of each step

**During each task:**

- Asked "What do you need from me before starting?"
- Kept a post-it on my desk of things it was doing that looked weird, so I could have a follow up conversation with it.

**After each task:**

- Had it test end-to-end after every change

The reality is that AI needs management like a human employee: clear goals, expectations, and accountability. Vibe coding is managing the world's most capable intern who has zero context and makes wild assumptions without explicit instructions.

## Lesson 3: You still need code reviews, even solo

AI couldn't fix every bug. When it spun its wheels, I had to read and understand the code myself. This disrupts the vibe coding flow but sometimes it's the only way forward, even on smaller projects like my few-thousand-line codebase.

Once I spent 30 minutes trying to prompt my way out of a bug. When I finally looked at the code myself, I found 500+ lines of unused methods and dead logging statements. The bug was obvious once I could actually see the real code.

This taught me to request code walkthroughs after building each component. Kind of like a code review, but mainly so I could help myself later when I inevitably needed to dive in.

You can't just be a "prompt engineer," you need to understand what it's building.

## Lesson 4: Every prompt is groundhog day

After a few hours of vibe coding, I started to feel exhausted. And not from the typing, but rather from maintaining the mental model of what I was building while managing an assistant that has no persistent memory or context. This was even true when I used the memory features, which were not 100% reliable.

When humans work together, they build shared context and trust over time, making collaboration easier. Not so with AI tools, even those claiming to have "memory." Human colleagues learn each other's preferences, remember past decisions, and build on previous conversations. We develop shorthand with each other. I know when you say "make it cleaner" what you specifically mean. You can reference "that bug from last week" and I'll know exactly what you're talking about. Over time, you need fewer words to communicate precisely.

With AI, you're starting from zero every single time. It's like working with someone who has perfect skills but complete amnesia. No learning curve, no building trust, no shared understanding. You're the only one who remembers anything, which means you're doing all the mental work of maintaining context while also trying to solve the actual problem.

I started keeping a document of prompt templates that I'd use over and over again as I worked with AI:

- "Don't make any changes, just provide hypotheses for what might be causing the bug"
- "Before you start coding, list all assumptions you're making"
- "Test this end-to-end and show me the output before moving on"

## Lesson 5: It's still 10x faster (when you do it right)

Despite all of this, I'm way more productive with AI coding tools. Building these automations would have taken weeks solo. With Claude Code, each took about 8 hours.

But, and this is crucial, only once I took ownership of:

- Designing the system architecture
- Reading and debugging the code when needed
- Managing the AI like a very junior developer
- Maintaining the mental model of what we were building

## What actually matters

Our PM team now spends zero time on manual opportunity analysis and much less time scrambling for customer data. We're spending much more time talking to customers and building conviction in our product plans for how to solve their problems. That is a huge win.

But the meta-win is understanding how to effectively use AI. We're an AI-native observability company, and that means we're also using AI to observe and optimize our own operations, not just our product workflows.

## A parting thought

"Vibe coding" is a terrible name for this. Vibes alone won't make code work reliably, even for small projects. You're not vibing, you're doing rigorous software engineering with an incredibly powerful but context-free assistant.

Next time someone tells you AI makes engineering skills obsolete, ask them to debug 500 lines of AI-written code. The future isn't "AI replaces engineers." It's "engineers with AI outperform everyone else by 10x."
