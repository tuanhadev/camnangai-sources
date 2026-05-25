# Large Language Models: A Short Introduction

**By:** Carolina Bento  
**Date:** Jan 21, 2025  
**Read Time:** 10 min read  
**Source:** [Medium](https://medium.com/data-science/large-language-models-a-short-introduction-bb8366118ad0)

---

## Introduction

There's an acronym you've probably heard non-stop for the past few years: LLM, which stands for Large Language Model.

In this article we're going to take a brief look at what LLMs are, why they're an extremely exciting piece of technology, why they matter to you and me, and why you should care about LLMs.

**Note:** in this article, we'll use Large Language Model, LLM and model interchangeably.

---

## What is an LLM

A Large Language Model, typically referred to as LLM since it is a bit of a tongue twister, is a mathematical model that generates text, like filling in the gap for the next word in a sentence.

For instance, when you feed it the sentence "The quick brown fox jumps over the lazy ____", it doesn't know exactly that the next word is dog. What the model produces instead is a list of possible next words with their corresponding probability of coming next in a sentence that starts with those exact words.

### Training Data Size

The reason why LLMs are so good at predicting the next word in a sentence is because they are trained with an incredibly large amount of text, which typically is scraped from the Internet.

On the other hand, if you're building an LLM that is specific to a particular domain, for example, you're building a chatbot that could converse with you as if they were a character in Shakespeare's plays, you would feed the LLM only Shakespeare context, i.e., all of his plays and sonnets.

### Number of Parameters

Although LLMs are trained with a gigantic amount of data, that's not what the "Large" in Large Language Models stands for. Besides the size of the training data, the other large quantity in these models is the number of parameters they have, each one with the possibility of being adjusted, i.e., tuned.

The simplest statistical models is Simple Linear Regression, with only two parameters, the slope and the intercept.

As a comparison:
- **GPT-3** (released in 2020) had **175B parameters** (yes Billion!)
- **LLaMA** (Meta's open source LLM, released in 2023) had different models ranging from **7B to 65B parameters**

These billions of parameters all start with random values at the beginning of the training process, and it's during the Backpropagation part of the training phase that they continually get tweaked and adjusted.

### Training Process

Similar to any other Machine Learning model, during the training phase, the output of the model is compared with the actual expected value for the output, in order to calculate the error. When there's still room for improvement, Backpropagation ensures the model parameters are adjusted such that the model can predict values with a little bit less error the next time.

But this is just what's called pre-training, where the model becomes proficient at predicting the next word in a sentence.

In order for the model to have really good interactions with a human, the underlying LLM has to go through a step of Reinforcement Learning with Human Feedback (RLHF). This is literally the human in the loop that is often talked about in the context of Machine Learning models.

In this phase, humans tag predictions that are not as good and by taking in that feedback, model parameters are updated and the model is trained again, as many times needed, to reach the level of prediction quality desired.

---

## Technical Architecture

### GPUs and Transformers

It's clear that these models are extremely complex and need to be able to perform millions, if not billions of computations. This high-intensity compute required novel architectures, at the model level with **Transformers** and for compute, with **GPUs**.

**GPU** (Graphics Processing Unit) is a class of graphic processors used in scenarios when you need to perform an incredibly big number of computations in a short period of time. Compared to the traditional CPUs found in your laptop, GPUs have the ability to effortlessly run many parallel computations.

The breakthrough for LLMs was when researchers realized GPUs can also be applied to non-graphical problems. Both Machine Learning and Computer Graphics rely on linear algebra—running operations on matrices—so both benefit from the ability to execute many parallel computations.

### Transformers Architecture

**Transformers** is a new type of architecture developed by Google, which makes it such that each operation done during model training can be parallelized. For instance, while predicting the next word in a sentence, a model that uses a Transformer architecture doesn't need to read the sentence from start to end; it processes the entire text all at the same time, in parallel.

It associates each word processed with a long array of numbers that give meaning to that word. Instead of processing and transforming one data point at a time, the combo of Transformers and GPUs can process tons of points at the same time by leveraging matrices.

### Attention Mechanism

What distinguishes Transformers is a unique operation called **Attention**. In a very simplistic way, Attention makes it possible to look at all the context around a word, even if it occurs multiple times in different sentences.

For example:
- "At the end of the show, the singer took a bow multiple times."
- "Jack wanted to go to the store to buy a new bow for target practice."

If we focus on the word "bow", you can see how the context in which this word shows up in each sentence and its actual meaning are very different.

Attention allows the model to refine the meaning each word encodes based on the context around them. This, plus some additional steps like training a Feedforward Neural Network, all done multiple times, make it such that the model gradually refines its capacity to encode the right information.

---

## Why LLMs Matter

### Capabilities

With the capacity to process enormous amounts of text examples and then predict with high accuracy the next word in a sentence, combined with other powerful Artificial Intelligence frameworks, many natural language and information retrieval tasks became much easier to implement and productize.

In essence, Large Language Models (LLMs) have emerged as cutting edge artificial intelligence systems that can process and generate text with coherent communication and generalize multiple tasks.

### Tasks Enabled by LLMs

Think about tasks like:
- Translating from English to Spanish
- Summarizing a set of documents
- Identifying certain passages in documents
- Having a chatbot answer your questions about a particular topic

These tasks were possible before, but the effort required to build a model was incredibly higher and the rate of improvement was much slower due to technology bottlenecks. LLMs came in and supercharged all of these tasks and applications.

### Real-World Products

There are tons of Artificial Intelligence (AI) products that leverage LLMs:
- **Meta AI** (Facebook's Meta)
- **Google Gemini**
- **ChatGPT** (Open AI)
- **Microsoft Copilot**
- Many others, covering a wide range of tasks to assist you

---

## Practical Applications and Impact

### Personal Use Cases

For example, a few weeks ago, when wondering how many studio albums Incubus had released, instead of Googling it or going to Wikipedia, the approach now is to ask Gemini.

These products are much more than a simple LLM that accurately predicts the next word. They leverage LLMs and other Machine Learning techniques and frameworks to understand what you're asking, search through all the contextual information they've seen so far, and present you with a human-like and coherent answer.

### Travel Planning Example

When traveling to Melbourne, asking LLMs for recommendations provides:
- A variety of pointers on what to do
- Saving time that would normally be spent between Yelp, TripAdvisor reviews, YouTube videos, or blog posts about iconic and recommended places
- Ability to dig further on specific places that seem more interesting

---

## Conclusion

LLMs are, without a doubt, a nascent area of research that has been evolving at a lightning fast pace. We're just in the very early days of productization and application.

### Future Opportunities

**For Researchers:** It's a cutting edge field with a wealth of both theoretical and practical problems to untangle.

**For Genomics:** Genomic Language Models (gLMs), i.e., Large Language Models trained on DNA sequences, are used to accelerate our general understanding of genomes and how DNA works and interacts with other functions. These are big questions for which scientists don't have definitive answers, but LLMs are proving to be a tool that can help them make progress at a much bigger scale.

**For Companies:** There's a monumental shift and opportunity to do more for customers, address more of their problems and pain-points, making it easier for customers to see the value in products.

**For Consumers:** We get to experience products and tools to assist us on day-to-day tasks, helping us perform our jobs a little better, gain faster access to knowledge, or get pointers to where we can search and dig deeper.

### Final Thoughts

The most exciting part is the speed at which these products evolve and outdate themselves. It's nothing short of rational to be apprehensive when we experience big technological step-changes multiple times during our lifetime. Yet, among all the hype and some of the fads that come and go, the core technology underlying Large Language Models is fascinating and has proven to have interesting and plausible applications.

---

## References

1. Large Language Models explained briefly (video)

2. A Comprehensive Overview of Large Language Models. 2024. Humza Naveed and Asad Ullah Khan and Shi Qiu and Muhammad Saqib and Saeed Anwar and Muhammad Usman and Naveed Akhtar and Nick Barnes and Ajmal Mian.

3. Language Models are Few-Shot Learners. 2020. Tom B. Brown and Benjamin Mann and Nick Ryder and Melanie Subbiah and Jared Kaplan and Prafulla Dhariwal and Arvind Neelakantan and Pranav Shyam and Girish Sastry and Amanda Askell and Sandhini Agarwal and Ariel Herbert-Voss and Gretchen Krueger and Tom Henighan and Rewon Child and Aditya Ramesh and Daniel M. Ziegler and Jeffrey Wu and Clemens Winter and Christopher Hesse and Mark Chen and Eric Sigler and Mateusz Litwin and Scott Gray and Benjamin Chess and Jack Clark and Christopher Berner and Sam McCandlish and Alec Radford and Ilya Sutskever and Dario Amodei

4. Genomic Language Models: Opportunities and Challenges. 2024. Gonzalo Benegas and Chengzhong Ye and Carlos Albors and Jianan Canal Li and Yun S. Song.

---

*Extracted on: May 26, 2026*
