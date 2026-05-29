# A Structured Workflow for "Vibe Coding" Full-Stack Apps

**Tags:** #vibecoding #ai #fullstack #webdev

---

There's a lot of hype surrounding "vibe coding". You've probably seen the AI influencers making claims like how you can build SaaS apps in 15 minutes with just a few tools and prompts.

But, as you might have guessed, these example workflows are pretty flimsy.

Yes, you can copy a landing page, or build a decent CRUD app, but you're not gonna be able to build a complex SaaS or internal tool with them.

But that doesn't mean there aren't workflows out there that can positively augment your development workflow. Anyone who's tinkered around with different AI-assisted techniques can tell you that there is some real magic in these tools.

That's why I spent a couple weeks researching the best techniques and workflow tips and put them to the test by building a full-featured, full-stack app with them.

Below, you'll find my honest review and the workflow that I found that really worked while using Cursor with Google's Gemini 2.5 Pro, and a solid UI template.

---

By the way, I came up with this workflow by testing and building a full-stack personal finance app in my spare time, tweaking and improving the process the entire time. Then, after landing on a good template and workflow, I rebuilt the app again and recorded it entirely, from start to deployments, in a ~3 hour long YouTube video.

This article is a summary of the key approaches to implementing this workflow.

---

## Step 1: Laying the Foundation

There are a lot of moving parts in modern full-stack web apps. Trying to get your LLM to glue it all together for you cohesively just doesn't work.

That's why you should give your AI helper a helping hand by starting with a solid foundation and leveraging the tools we have at our disposal.

In practical terms this means using stuff like:

- **UI Component Libraries**
- **Boilerplate templates**
- **Full-stack frameworks with batteries-included**

Component libraries and templates are great ways to give the LLM a known foundation to build upon. It also takes the guess work out of styling and helps those styles be consistent as the app grows.

Using a full-stack framework with batteries-included, such as Wasp for JavaScript (React, Node.js, Prisma) or Laravel for PHP, takes the complexity out of piecing the different parts of the stack together. Since these frameworks are opinionated, they've chosen a set of tools that work well together, and they have the added benefit of doing a lot of work under-the-hood. In the end, the AI can focus on just the business logic of the app.

Take Wasp's main config file, for example (see below). All you or the LLM has to do is define your backend operations, and the framework takes care of managing the server setup and configuration for you. On top of that, this config file acts as a central "source of truth" the LLM can always reference to see how the app is defined as it builds new features.

```wasp
app vibeCodeWasp {
  wasp: { version: "^0.16.3" },
  title: "Vibe Code Workflow",
  auth: {
    userEntity: User,
    methods: {
      email: {},
      google: {},
      github: {},
    },
  },
  client: {
    rootComponent: import Main from "@src/main",
    setupFn: import QuerySetup from "@src/config/querySetup",
  },
}

route LoginRoute { path: "/login", to: Login }
page Login {
  component: import { Login } from "@src/features/auth/login"
}

route EnvelopesRoute { path: "/envelopes", to: EnvelopesPage }
page EnvelopesPage {
  authRequired: true,
  component: import { EnvelopesPage } from "@src/features/envelopes/EnvelopesPage.tsx"
}

query getEnvelopes {
  fn: import { getEnvelopes } from "@src/features/envelopes/operations.ts",
  entities: [Envelope, BudgetProfile, UserBudgetProfile]
}

action createEnvelope {
  fn: import { createEnvelope } from "@src/features/envelopes/operations.ts",
  entities: [Envelope, BudgetProfile, UserBudgetProfile]
}

//...
```

---

## Step 2: Getting the Most Out of Your AI Assistant

Once you've got a solid foundation to work with, you need to create a comprehensive set of rules for your editor and LLM to follow.

To arrive at a solid set of rules you need to:

1. Start building something
2. Look out for times when the LLM (repeatedly) doesn't meet your expectations and define rules for them
3. Constantly ask the LLM to help you improve your workflow

### Defining Rules

Different IDEs and coding tools have different naming conventions for the rules you define, but they all function more or less the same way (I used Cursor for this project so I'll be referring to Cursor's conventions here).

Cursor deprecated their `.cursorrules` config file in favor of a `.cursor/rules/` directory with multiple files. In this set of rules, you can pack in general rules that align with your coding style, and project-specific rules (e.g. conventions, operations, auth).

The key here is to provide structured context for the LLM so that it doesn't have to rely on broader knowledge.

What does that mean exactly? It means telling the LLM about the current project and template you'll be building on, what conventions it should use, and how it should deal with common issues.

You can also add general strategies to rules files that you can manually reference in chat windows. For example, I often like telling the LLM to "think about 3 different strategies/approaches, pick the best one, and give your rationale for why you chose it." So I created a rule for it, `7-possible-solutions-thinking.mdc`, and I pass it in whenever I want to use it, saving myself from typing the same thing over and over.

### Using AI to Critique and Improve Your Workflow

Aside from this, I view the set of rules as a fluid object. As I worked on my apps, I started with a set of rules and iterated on them to get the kind of output I was looking for. This meant adding new rules to deal with common errors the LLM would introduce, or to overcome project-specific issues that didn't meet the general expectations of the LLM.

As I amended these rules, I would also take time to use the LLM as a source of feedback, asking it to critique my current workflow and find ways I could improve it.

This meant passing in my rules files into context, along with other documents like Plans and READMEs, and asking it to look for areas where we could improve them, using the past chat sessions as context as well.

A lot of the time this just means asking the LLM something like:

> Can you review for breadth and clarity and think of a few ways it could be improved, if necessary. Remember, these documents are to be used as context for AI-assisted coding workflows.

---

## Step 3: Defining the "What" and the "How" (PRD & Plan)

An extremely important step in all this is the initial prompts you use to guide the generation of the Product Requirement Doc (PRD) and the step-by-step actionable plan you create from it.

The PRD is basically just a detailed guideline for how the app should look and behave, and some guidelines for how it should be implemented.

After generating the PRD, we ask the LLM to generate a step-by-step actionable plan that will implement the app in phases using a modified vertical slice method suitable for LLM-assisted development.

The vertical slice implementation is important because it instructs the LLM to develop the app in full-stack "slices" — from DB to UI — in increasing complexity. That might look like developing a super simple version of a full-stack feature in an early phase, and then adding more complexity to that feature in the later phases.

This approach highlights a common recurring theme in this workflow: **build a simple, solid foundation and incrementally add complexity in focused chunks.**

After the initial generation of each of these docs, I will often ask the LLM to review its own work and look for possible ways to improve the documents based on the project structure and the fact that it will be used for assisted coding. Sometimes it finds interesting improvements, or at the very least it finds redundant information it can remove.

Here is an example prompt for generating the step-by-step plan:

> From this PRD, create an actionable, step-by-step plan using a modified vertical slice implementation approach that's suitable for LLM-assisted coding. Before you create the plan, think about a few different plan styles that would be suitable for this project and the implementation style before selecting the best one. Give your reasoning for why you think we should use this plan style. Remember that we will constantly refer to this plan to guide our coding implementation so it should be well structured, concise, and actionable, while still providing enough information to guide the LLM.

---

## Step 4: Building End-to-End — Vertical Slices in Action

As mentioned above, the vertical slice approach lends itself well to building with full-stack frameworks because of the heavy-lifting they can do for you and the LLM.

Rather than trying to define all your database models from the start, this approach tackles the simplest form of a full-stack feature individually, and then builds upon them in later phases. This means, in an early phase, we might only define the database models needed for Authentication, then its related server-side functions, and the UI for it like Login forms and pages.

In my Wasp project, the flow for implementing a phase/feature looked a lot like:

1. Define necessary DB entities in `schema.prisma` for that feature only
2. Define operations in the `main.wasp` file
3. Write the server operations logic
4. Define pages/routes in the `main.wasp` file
5. Build `src/features` or `src/components` UI
6. Connect things via Wasp hooks and other library hooks and modules (`react-router-dom`, `recharts`, `tanstack-table`)

This gave me and the LLM a huge advantage in being able to build the app incrementally without getting too bogged down by the amount of complexity.

Once the basis for these features was working smoothly, we could improve the complexity of them, and add on other sub-features, with little to no issues!

The other advantage this had was that, if I realised there was a feature set I wanted to add on later that didn't already exist in the plan, I could ask the LLM to review the plan and find the best time/phase within it to implement it. Sometimes that time was then at the moment, and other times it gave great recommendations for deferring the new feature idea until later. If so, we'd update the plan accordingly.

---

## Step 5: Closing the Loop — AI-Assisted Documentation

Documentation often gets pushed to the back burner. But in an AI-assisted workflow, keeping track of why things were built a certain way and how the current implementation works becomes even more crucial.

The AI doesn't inherently "remember" the context from three phases ago unless you provide it. So we get the LLM to provide it for itself.

After completing a significant phase or feature slice defined in our Plan, I made it a habit to task the AI with documenting what we just built. I even created a rule file for this task to make it easier.

The process looked something like this:

1. Gather the key files related to the implemented feature (e.g., relevant sections of `main.wasp`, `schema.prisma`, the `operations.ts` file, UI component files).
2. Provide the relevant sections of the PRD and the Plan that described the feature.
3. Reference the rule file with the Doc creation task.
4. Have it review the Doc for breadth and clarity.

What's important is to have it focus on the core logic, how the different parts connect (DB → Server → Client), and any key decisions made, referencing the specific files where the implementation details can be found.

The AI would then generate a markdown file (or update an existing one) in the `ai/docs/` directory, and this is nice for two reasons:

- **For Humans:** It created a clear, human-readable record of the feature for onboarding or future development.
- **For the AI:** It built up a knowledge base within the project that could be fed back into the AI's context in later stages. This helped maintain consistency and reduced the chances of the AI forgetting previous decisions or implementations.

This "closing the loop" step turns documentation from a chore into a clean way of maintaining the workflow's effectiveness.

---

## Conclusion: Believe the Hype… Just Not All of It

So, can you "vibe code" a complex SaaS app in just a few hours? Well, kinda, but it will probably be a boring one.

But what you can do is leverage AI to significantly augment your development process, build faster, handle complexity more effectively, and maintain better structure in your full-stack projects.

The "Vibe Coding" workflow I landed on after weeks of testing boils down to these core principles:

1. **Start Strong:** Use solid foundations like full-stack frameworks (Wasp) and UI libraries (Shadcn-admin) to reduce boilerplate and constrain the problem space for the AI.
2. **Teach Your AI:** Create explicit, detailed rules (`.cursor/rules/`) to guide the AI on project conventions, specific technologies, and common pitfalls. Don't rely on its general knowledge alone.
3. **Structure the Dialogue:** Use shared artifacts like a PRD and a step-by-step Plan (developed collaboratively with the AI) to align intent and break down work.
4. **Slice Vertically:** Implement features end-to-end in manageable, incremental slices, adding complexity gradually.
5. **Document Continuously:** Use the AI to help document features as you build them, maintaining project knowledge for both human and AI collaborators.
6. **Iterate and Refine:** Treat the rules, plan, and workflow itself as living documents, using the AI to help critique and improve the process.

Following this structured approach delivered really good results and I was able to implement features in record time. With this workflow I could really build complex apps 20–50x faster than I could before.

The fact that you also have a companion that has a huge knowledge set that helps you refine ideas and test assumptions is amazing as well.

Although you can do a lot without ever touching code yourself, it still requires you, the developer, to guide, review, and understand the code. But it is a realistic, effective way to collaborate with AI assistants like Gemini 2.5 Pro in Cursor, moving beyond simple prompts to build full-featured apps efficiently.

If you want to see this workflow in action from start to finish, check out the full ~3 hour YouTube walkthrough and template repo. And if you have any other tips I missed, please let me know in the comments!
