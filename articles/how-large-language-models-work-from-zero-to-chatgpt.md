# How Large Language Models Work

## From Zero to ChatGPT

**Author:** Andreas Stöffelbauer  
**Publication:** Data Science + AI at Microsoft (Medium)  
**Date:** October 24, 2023

---

## Introduction

Thanks to Large Language Models (or LLMs for short), Artificial Intelligence has now caught the attention of pretty much everyone. ChatGPT, possibly the most famous LLM, has immediately skyrocketed in popularity due to the fact that natural language is such a, well, natural interface that has made the recent breakthroughs in Artificial Intelligence accessible to everyone. Nevertheless, how LLMs work is still less commonly understood, unless you are a Data Scientist or in another AI-related role.

This article aims to strike a balance between overly technical content and trivial explanations. It's meant to take you from zero all the way through to how LLMs are trained and why they work so impressively well, by picking up just all the relevant pieces along the way.

This is not a deep dive into all the nitty-gritty details—we'll rely on intuition rather than math, and on visuals as much as possible. The main mechanisms underlying LLMs are very intuitive, and that alone will get us very far.

This article should help you get more out of using LLMs like ChatGPT. As Andrei Karpathy, a well-known AI researcher and engineer, recently and pointedly said: **"English is the hottest new programming language."**

## Where do LLMs Fit in AI?

The field of AI is often visualized in layers:

- **Artificial Intelligence (AI)** is a very broad term, but generally it deals with intelligent machines.
- **Machine Learning (ML)** is a subfield of AI that specifically focuses on pattern recognition in data. Once you recognize a pattern, you can apply that pattern to new observations.
- **Deep Learning** is the field within ML that is focused on unstructured data, which includes text and images. It relies on artificial neural networks, a method that is (loosely) inspired by the human brain.
- **Large Language Models (LLMs)** deal with text specifically, and that is the focus of this article.

## Machine Learning Basics

The goal of Machine Learning is to discover patterns in data—or more specifically, a pattern that describes the relationship between an input and an outcome.

### Example: Music Genre Classification

Let's distinguish between two music genres: reggaeton and R&B. Reggaeton is a Latin urban genre known for its lively beats and danceable rhythms, while R&B (Rhythm and Blues) is a genre rooted in African-American musical traditions, characterized by soulful vocals and a mix of upbeat and slower-paced songs.

Suppose we have 20 songs. We know each song's tempo and energy, and we've labeled them with a genre. When we visualize the data, we can see that high energy, high tempo songs are primarily reggaeton while lower tempo, lower energy songs are mostly R&B.

However, we want to avoid having to label the genre by hand all the time because it's time consuming and not scalable. Instead, we can learn the relationship between the song metrics and genre and then make predictions using only the readily available metrics.

In Machine Learning terms, this is a **classification problem**, because the outcome variable can only take on one of a fixed set of classes/labels. We "train" a Machine Learning model using our labeled dataset, i.e., a set of songs for which we do know the genre. Visually speaking, what the training does is find the boundary that best separates the two classes.

Once we know this boundary, for any new song we can make a prediction about whether it's a reggaeton or an R&B song, depending on which side of the boundary the song falls on. Additionally, the further away from the boundary, the more certain we can be about being correct.

### Complexity in Real-World Problems

In reality, things are often much more complex. The best boundary to separate classes may not be linear—the relationship between inputs and output can be more complex, curved, or many times more complex than that. Reality is typically more complex because:

- Rather than only two inputs, we often have tens, hundreds, or even thousands of input variables
- We often have more than two classes
- All classes can depend on all inputs through an incredibly complex, non-linear relationship

What we should take away is: **The more complex the relationship between input and output, the more complex and powerful the Machine Learning model we need to learn that relationship.**

### Image Classification Example

Let's consider image classification. We want to classify images as either tiger, cat, or fox. Images are numeric inputs consisting of pixels with height, width, and three channels (red, green, blue). Even a small 224×224 image consists of more than 150,000 pixels (224×224×3).

This presents two problems:
1. We have far more input variables than before (150,000+)
2. The relationship between raw pixels and class label is incredibly complex

Our human brains can distinguish among tigers, foxes, and cats easily, but if you saw the 150,000 pixels one by one, you'd have no idea what the image contains. A Machine Learning model must learn this mapping from scratch.

### Text and Sentiment Classification

Let's consider the relationship between a sentence and its sentiment (positive or negative). This is also a classification task.

Just like with images, it's not obvious how words can be turned into numeric inputs. Every word can be turned into a **word embedding**, which represents the word's semantic and syntactic meaning, often within a specific context. Word embeddings typically consist of between tens and thousands of variables per word.

With a long sentence or paragraph, we can quickly reach a very large number of inputs. The relationship between language and sentiment is also very complex—just think of a sentence like "That was a great fall" and all the ways it can be interpreted.

What we need is an extremely powerful Machine Learning model and lots of data. **That's where Deep Learning comes in.**

## Deep Learning

We need more flexible, powerful models when:
- The relationship between input and output is very complex
- The number of input or output variables is large

### Neural Networks

**Neural networks** are powerful Machine Learning models that allow arbitrarily complex relationships to be modeled. They are loosely inspired by the brain, although the actual similarities are debatable.

Their basic architecture is relatively simple: they consist of a sequence of layers of connected "neurons" that an input signal passes through to predict the outcome variable. Think of them as multiple layers of linear regression stacked together, with non-linearities in between, which allows the neural network to model highly non-linear relationships.

Neural networks are often many layers deep (hence the name **Deep Learning**), which means they can be extremely large. ChatGPT, for example, is based on a neural network consisting of 176 billion neurons—more than the approximate 100 billion neurons in a human brain.

## Large Language Models

Finally, we can talk about Large Language Models (LLMs).

### What Does "Large" Mean?

"Large" simply refers to the number of neurons, also called **parameters**, in the neural network. There's no clear number for what constitutes a Large Language Model, but generally, everything above 1 billion neurons is considered large.

### What's a "Language Model"?

A language model learns to predict the next word in a given sequence of words. In other words, given a sentence or paragraph, what's the next word?

This is a Machine Learning problem, similar to sentiment classification but with a crucial difference: instead of only two or a few classes, we now have as many classes as there are words—approximately 50,000. This is orders of magnitude more complex than binary sentiment classification.

### Training Data

We need data to train the neural network. For the "next word prediction" task, it's easy to create massive datasets from the internet, books, research papers, and more.

Moreover, we don't even need to label the data manually. The next word itself is the label—this is called **self-supervised learning**. A single sequence can be turned into multiple training sequences.

We train the neural network to predict the next word for many short and long sequences (some up to thousands of words), so that in every context, it learns what the next word should be.

### Generating Text

Once we can predict one word, we can feed the extended sequence back into the LLM and predict another word, and so on. Using our trained LLM, we can generate text, not just a single word.

**Sampling:** We don't always have to predict the most likely word. We can instead sample from, say, the five most likely words at a given time. This provides more creativity. Some LLMs allow you to choose how deterministic or creative you want the output. This is why ChatGPT typically doesn't give the same answer when you regenerate a response.

## GPT: Generative Pre-trained Transformer

So what does the GPT in ChatGPT stand for?

- **G** = **Generative**: Trained on language generation
- **P** = **Pre-trained**: The model is trained in phases (discussed next)
- **T** = **Transformer**: The type of neural network architecture being used

The transformer architecture works so well because it can focus its attention on the parts of the input sequence that are most relevant at any time. You could argue that this is similar to how humans focus attention on what's most relevant and ignore the rest.

### Phases of LLM Training

Large Language Models like ChatGPT are trained in phases:

#### 1. Pre-Training

The first stage is pre-training, which we've gone through above. This stage requires massive amounts of data to learn to predict the next word. In this phase, the model learns:
- Grammar and syntax of language
- A great deal of knowledge about the world
- Emerging abilities we'll discuss later

**The Problem:** The pre-trained LLM has learned mainly to ramble on about a topic. It doesn't respond well to the kind of inputs you'd generally want to give an AI, such as questions or instructions. The model hasn't learned to behave as an assistant.

For example, if you ask a pre-trained LLM "What is your first name?", it may respond with "What is your last name?" simply because this is the kind of data it has seen during pre-training (in forms, for example).

At this stage, we say that the LLM is not **aligned** with human intentions. Alignment is an important topic for LLMs.

#### 2. Instruction Fine-Tuning

Here we take the pre-trained LLM and train it using only high-quality instruction and response pairs. The model unlearns to be a text completer and learns to become a helpful assistant that follows instructions and responds in a way aligned with the user's intention.

The instruction dataset is typically much smaller than the pre-training set because high-quality instruction-response pairs are expensive to create—they're typically sourced from humans rather than automatically labeled. This stage is called **supervised instruction fine-tuning**.

#### 3. Reinforcement Learning from Human Feedback (RLHF)

Some LLMs like ChatGPT go through a third stage: **Reinforcement Learning from Human Feedback (RLHF)**. The purpose is similar to instruction fine-tuning—it helps alignment and ensures that the LLM's output reflects human values and preferences.

## Common Use Cases Explained

### Why Can LLMs Summarize Text?

People often make summarizations—on the internet, in research papers, books, and more. As a result, an LLM trained on that data learns how to do that too. It learns to attend to main points and compress them into short text.

When a summary is generated, the full text is part of the input sequence. This skill is probably learned during pre-training, although instruction fine-tuning helps improve it further.

### Why Can LLMs Answer Knowledge Questions?

The ability to act as an assistant and respond appropriately is due to instruction fine-tuning and RLHF. But most (or all) of the knowledge to answer questions was already acquired during pre-training.

However, this raises a critical issue: **What if the LLM doesn't know the answer?**

Unfortunately, it may just make one up. To understand why, consider the training objective. The LLM learns only to generate text, not factually true text. Nothing in its training gives the model any indicator of truth or reliability. Moreover, text on the internet and in books sounds confident, so the LLM learns to sound confident too, even if wrong.

### Hallucinations

**Hallucination** refers to the phenomenon of LLMs making up facts when they shouldn't. This is an active area of research, and we can expect LLMs to be less prone to hallucinations over time.

**Partial Solution:** We can mitigate hallucinations by providing additional context. Everything in the LLM's input sequence is readily available for it to process, while any implicit knowledge acquired during pre-training is more difficult to retrieve.

For example, if you ask the LLM "Who is the current president of Colombia?" it may respond incorrectly for two reasons:
1. The LLM may hallucinate and respond with a wrong or fake name
2. LLMs are trained only on data up to a certain cut-off date, so the LLM cannot know current information

**Solution:** Provide relevant context. Include the Wikipedia article on Colombia's political history as context for the LLM. It would then be more likely to answer correctly because it can simply extract the name from the context.

This process is called **grounding the LLM** in the context or in the real world. This is exactly how Bing Chat and other search-based LLMs work: they first extract relevant context from the web and then pass all that information to the LLM alongside the user's question.

## The Magic Behind LLMs

You might think "this is not that magical" because all that's happening is predicting words one at a time—pure statistics. Or is it?

The magical part is how **remarkably well it works**. Everyone, even researchers at OpenAI, were surprised at how far language modeling can go. One of the key drivers in recent years has simply been massive scaling up of neural networks and datasets.

For example, GPT-4, reportedly a model with more than one trillion parameters, can pass the bar exam or AP Biology with a score in the top 10 percent of test takers.

Surprisingly, large LLMs show **emerging abilities**—abilities to solve tasks they were not explicitly trained to do.

### Emerging Ability 1: Zero-Shot Learning

LLMs can perform entirely new tasks that they haven't encountered in training, called **zero-shot**. All it takes is some instructions on how to solve the task.

For example, you can ask an LLM to translate a sentence from German to English while responding only with words that start with "f". When asked to translate "Die Katze schläft gerne in der Box" (which means "The cat likes to sleep in the box"), an LLM translated it to "Feline friend finds fluffy fortress"—quite impressive!

### Emerging Ability 2: Few-Shot Learning

For more complex tasks, zero-shot prompting often requires very detailed instructions and may not achieve perfect performance. Just like humans, LLMs can benefit from examples or demonstrations.

If you want a model to translate currency amounts into a common format, you could describe what you want in detail or just give a brief instruction and some example demonstrations. The model learns the pattern and applies it to new examples.

**General tip:** Provide some examples if the LLM is struggling with a task in zero-shot manner. This typically helps the model understand the task better, making performance more reliable.

### Emerging Ability 3: Chain-of-Thought

Another interesting ability of LLMs is reminiscent of human intelligence. It's especially useful for complex tasks requiring multiple steps of reasoning.

If you're asked "Who won the World Cup in the year before Lionel Messi was born?", you'd solve it step by step by writing down intermediate solutions. LLMs can do the same.

Simply telling an LLM to **"think step by step"** can increase its performance substantially on many tasks.

**Why does this work?** Unusual composite knowledge might not be directly in the LLM's internal memory, but all the individual facts might be (like Messi's birthday and World Cup winners). Allowing the LLM to build up to the final answer gives it time to think out loud—a working memory—and solve simpler sub-problems first.

By the time the model generates the final answer, the relevant facts are already in the LLM's working memory, making it easier to answer correctly.

## Conclusion

Before wrapping up, let's revisit the question: Is the LLM really just predicting the next word, or is there more to it?

Some researchers argue that to become so good at next-word-prediction in any context, the LLM must have acquired a compressed understanding of the world internally. Others argue that the model has simply learned to memorize and copy patterns seen during training, with no actual understanding.

There's probably no clear right or wrong between those two sides. It may just be a different way of looking at the same thing. Clearly these LLMs are proving to be very useful and show impressive knowledge and reasoning capabilities, and maybe even some sparks of general intelligence. But whether or to what extent that resembles human intelligence is still to be determined, as is how much further language modeling can improve the state of the art.

It's not only up to AI researchers and data scientists to decide how AI is used to benefit the world; everyone should be able to have a say. Hopefully, this article helps you understand LLMs and form your own opinion about AI's potentials and risks.

If you've made it through this article, you pretty much understand how some of the state-of-the-art LLMs work (as of Autumn 2023), at least at a high level.

---

**Original Article by Andreas Stöffelbauer**  
**Published on Medium - Data Science + AI at Microsoft**  
**Date: October 24, 2023**