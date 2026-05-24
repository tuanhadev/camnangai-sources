# What is Vibe Coding?

Why you wouldn't want to do it and why you would...

By Cassie Kozyrkov | Mar 31, 2025

---

## Short answer

Vibe coding is prompting an AI system to generate code based on natural language descriptions, saving you from writing it all from scratch.

## Longer answer

Vibe coding, a term coined by Andrej Karpathy in February 2025, describes an increasingly popular approach to writing software: express the code you want in a few sentences to an AI system like ChatGPT or Claude, then polish and (hopefully!) test the generated result.

Why wouldn't you want to do this? Why would you? Let's take a look with an example! (Or scroll down to the case for vibe coding and the case against it, each analyzed for beginners and for experts.)

---

Imagine that you're setting up an online shop to sell eight-legged onesies for adults. In three grave errors of judgment (1) you're expecting massive sales and (2) you've chosen (oh no!) to build your shipping form from scratch. Let's accept your fate and take it from there.

In your questionable quest to automate things, you've decided to check whether the user's submitted country is valid. You're not yet sure how you'll deal with users' near-demonic creativity when it comes to spelling city names but, in the spirit of starting somewhere, the country thing seems doable since there are fewer than 200 of them. How would you build a country validator?

To automatically check that the user input points to a valid shipping country, you have 3 options:

1. Write the validation code from scratch. (Or hire someone to do it.)
2. Connect an AI to validate inputs in real-time.
3. Use an AI to help you write the validation code.

### Option #1 — Code from scratch

Old school but effective. It's very easy to write code that does this: record a list of countries, then compare the user's input string against your list. If we're willing to play fast and loose with philosophy, we could say that your machine now "knows" that Canada is a country.

This traditional approach delivers reliability but requires some knowhow. If your shipping system absolutely must validate countries correctly every time, this approach works best—but only if you know how to code or can afford to hire someone who does.

What if you're broke, friendless, and have no idea how to write this code?

### Option #2 — Connect an AI

While using a large language model (LLM)* through a service like ChatGPT is as easy as sending a text message, engineering a solution with it is a bit harder. Connecting an LLM to your business's online form will take you longer than writing the code for a simple lookup table or IF statement.

That's just one reason you'd want to avoid the knee-jerk reaction of using AI for everything. Let me give you two more reasons:

- It's far more expensive to use an LLM for this task than to use a list or lookup table.
- Unlike the code-from-scratch approach, an LLM doesn't guarantee consistent or 100% reliable results. If you want to input "Canada" and be sure that the output is exactly and only "Country" every time… well, let's see what happens.

The "generative" in GenAI means the output is randomly sampled from a distribution of likely responses based on your prompt. That's why you can get endless answers to the same question—some helpful, others way off the mark. Sure, commercial LLMs have some error-checking under the hood, but it's not bulletproof, especially at scale. So if your proverbial 2 + 2 absolutely has to equal 4 (and only 4***) every time, you're better off not relying on an LLM to do the math.

When you need perfect control, you'll want to write code that cannot surprise you (especially at scale, once your eight-legged onesies really take off). That's Option 1. But wouldn't it be handy if you got that lookup code without having to know how to write it in the first place? Welcome to Option 3.

### Option #3 — Vibe coding

If you don't know how to write the code you need, you could prompt a chatbot like Claude or ChatGPT to help you with a draft.

This way of writing code is exactly what is meant by vibe coding. It's so much better than starting from a blank page… or is it?

---

## The case AGAINST vibe coding

Any programmer worth their salt can whip up a country validation function faster than they can craft the perfect prompt, wait for the output, and then scrutinize the output. Vibe coding doesn't eliminate work—it just shifts it from writing to explaining and reviewing, which isn't always a win.

### For Beginners

If you're a novice, you'll find it tricky to review what you've never taken the time to deeply understand. Generated code can contain subtle bugs or security vulnerabilities that require expertise to identify. It might fail in edge cases you didn't even consider. How will you know what you're looking at?

Vibe coding is like playing archeologist in someone else's mistakes. At least when you write buggy code yourself, you understand the flawed thinking that created it. Though you're perfectly literate in English, are you 100% sure you've never skipped a paragraph without noticing? It's harder to stay focused when reading than when writing, so a bug can slip past you in that little moment that your eyes are glazing over.

The smart move? Guard against overconfidence. If you never took the time to learn proper coding fundamentals, don't assume you understand what you're looking at. Remember that AI makes mistakes (always be testing) and use it selectively to accelerate your work—not replace true expertise. The long way around is sometimes the fastest route to actually knowing what you're doing.

### For Experts

For seasoned developers, especially the type who've memorized 297 Vim shortcuts because using a mouse is for mere mortals, vibe coding is like asking for directions when you already know the way. If clicking is already too slow for you, prompting-waiting-checking would surely feel like a mental traffic jam. In a very literal sense, AI might feel like a waste of time.

What makes matters worse is that code is less ambiguous than your mother tongue, so explaining your wishes in natural language precisely can be more arduous than simply saying it with code if you're already fluent. Before precise algebraic symbols, some of the greatest mathematical minds in history were stumped by equations we moderns breeze through in high school.

If you know exactly what you want to say, conveying it to the machine might take fewer lines in code than in your mother tongue.

Many coders find it less fulfilling and more draining to read code than to write it, so vibe coding threatens to wring out some of the most joyful elements of the work. Reading other people's code all day and ensuring that yours plays nicely with theirs is the difference between the amateur automator and the true professional, but this doesn't mean it's the part that developers spring out of bed for.

---

## The case FOR vibe coding

### For Beginners

While vibe coding isn't a perfect shortcut to understanding, having a patient 24/7 on-demand tutor giving you custom working code examples to adapt to your needs unquestionably lowers the barrier to entry for automation. Grumpy warnings aside, it's a win for beginners. If you've been putting off learning to code, there's no better time to start.

### For Experts

Even programming speed demons can find reasons to love vibe coding. Here are just a few things it lets you save time on if you use it judiciously:

- Quickly compare multiple approaches to solving the same problem.
- Easily explore and translate between unfamiliar programming languages.
- Brainstorm optimizations, best practices, and debugging ideas.
- Generate comments, documentation, and tedious boilerplate.
- Make your formatting more consistent and readable.
- Implement API integrations. (API documentation makes for riveting reading.)
- Create working examples of library usage and unit tests.

---

## Verdict

Plenty of hardened professionals have been incorporating vibe coding into their workflow since before we had this cute name for it—hence the explosive growth of tools like Cursor and Copilot.

Vibe coding is here to stay, but it's best viewed as an enhancement to—not replacement for—programming expertise. True experts are selective about when and how they use it.

Even if you, like many professional software engineers, remain unconvinced that vibe coding can improve the speed or quality of your work, it's still a skill worth practicing. I predict a future in which a developer who never uses AI to assist coding is as rare as one who never uses email.

---

## Footnotes

*A quick guide to the LLM word salad:

- LLMs are a class of AI technology. LLM = large language model.
- GPT-4o and Claude 3.7 Sonnet are specific LLMs.
- ChatGPT and Claude are direct interfaces to those specific LLMs.
- OpenAI and Anthropic are the companies that brought you these specific LLMs.

---

**Source:** https://decision.substack.com/p/what-is-vibe-coding
