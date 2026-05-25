# How Large Language Models Work: From Zero to ChatGPT

**Author:** Andreas Stöffelbauer
**Publication:** Medium - Data Science + AI at Microsoft
**Date:** Oct 24, 2023
**Read Time:** 25 min read

---

## Introduction

Thanks to Large Language Models (or LLMs for short), Artificial Intelligence has now caught the attention of pretty much everyone. ChatGPT, possibly the most famous LLM, has immediately skyrocketed in popularity due to the fact that natural language is such a, well, natural interface that has made the recent breakthroughs in Artificial Intelligence accessible to everyone.

This article is meant to take you from zero all the way through to how LLMs are trained and why they work so impressively well.

---

## The Field of Artificial Intelligence in Layers

The field of AI is often visualized in layers:

- **Artificial Intelligence (AI)** is a very broad term, but generally it deals with intelligent machines.
- **Machine Learning (ML)** is a subfield of AI that specifically focuses on pattern recognition in data.
- **Deep Learning** is the field within ML that is focused on unstructured data, which includes text and images.
- **Large Language Models (LLMs)** deal with text specifically.

---

## Machine Learning: Discovering Patterns

The goal of Machine Learning is to discover patterns in data, or more specifically, a pattern that describes the relationship between an input and an outcome.

### Example: Classifying Music Genres

Suppose we want to distinguish between reggaeton and R&B. Reggaeton is a Latin urban genre known for its lively beats and danceable rhythms, while R&B is a genre rooted in African-American musical traditions, characterized by soulful vocals.

If we have songs labeled with their tempo and energy metrics, we can train a classifier to learn the boundary between these two genres. Once trained, we can predict the genre of new songs based only on their metrics.

In Machine Learning terms, this is a **classification problem**, because the outcome can only take one of a fixed set of classes. This contrasts with a **regression problem**, where the outcome is continuous.

### Complexity in Real-World Problems

In reality, relationships are often much more complex. There may be thousands of input variables and many classes, with non-linear relationships between them.

**Key insight:** The more complex the relationship between input and output, the more complex and powerful the Machine Learning model we need.

---

## Image Classification Example

Consider classifying images as tiger, cat, or fox. A computer can only process numeric inputs, but fortunately images are just pixels—numeric values with height, width, and RGB channels.

However, even a small 224x224 image has over 150,000 pixels. The relationship between raw pixels and the image label is incredibly complex. Our brains distinguish these animals easily, but a Machine Learning model must learn this mapping from scratch.

---

## Sentiment Classification

Analyzing whether a sentence is positive or negative sentiment is another complex task. Words must be converted to numeric inputs called **word embeddings**, which represent semantic and syntactic meaning.

Word embeddings typically contain tens to thousands of variables per word. With long texts, this quickly becomes very high-dimensional. The relationship between language and sentiment is highly complex—consider how "That was a great fall" can be interpreted multiple ways.

What we need is an extremely powerful Machine Learning model and lots of data—this is where Deep Learning comes in.

---

## Deep Learning: Neural Networks

Neural networks are powerful Machine Learning models that allow arbitrarily complex relationships to be modeled. They consist of layers of connected "neurons" that an input passes through to predict outputs.

Think of them as multiple layers of linear regression stacked together, with non-linearities between them. This allows neural networks to model highly non-linear relationships.

Neural networks are often many layers deep (hence "Deep Learning"). They can be extremely large—ChatGPT, for example, has 176 billion neurons, more than the 100 billion neurons in a human brain.

---

## Large Language Models: Learning to Predict the Next Word

A Large Language Model is a neural network with billions of neurons. But what makes it "large" and a "language" model?

**Language modeling** means learning to predict the next word in a sequence. Given a sentence, predict the following word. This is a classification task with approximately 50,000 classes (one for each word).

We can create training data easily from internet text without manual labeling—this is **self-supervised learning**. Each sentence can generate multiple training examples by using progressively longer prefixes.

With a large enough network and enough data, the LLM becomes very good at predicting appropriate next words that are syntactically and semantically correct.

---

## Generating Text with LLMs

Once we can predict one word, we can feed the extended sequence back and predict another word, then repeat. This allows us to **generate text** one word at a time. This is **Generative AI**.

We don't always pick the most likely word—we can sample from the top candidates. This adds creativity. You can often adjust how deterministic or creative the output is. This is why ChatGPT gives different responses when you regenerate.

---

## What Does GPT Stand For?

**GPT = Generative Pre-trained Transformer**

- **G**enerative: Trained on language generation
- **P**re-trained: Trained in phases (we'll discuss this)
- **T**ransformer: The neural network architecture used

Transformers work well because they can focus attention on the most relevant parts of the input sequence at any time—similar to human attention.

---

## LLM Training Phases

### Phase 1: Pre-Training

The first stage trains the model to predict the next word using massive amounts of internet text, books, and research papers. The model learns grammar, syntax, and world knowledge.

However, pre-trained LLMs have a problem: they're optimized for completing text, not responding to questions or following instructions. If you ask "What is your first name?" a pre-trained model might just respond "What is your last name?" because that's what it sees in training data like empty forms.

We say the model is not **aligned with human intentions**. It doesn't behave as an assistant.

### Phase 2: Instruction Fine-Tuning

We now train the model using only high-quality instruction-response pairs. This is more expensive than pre-training since humans must create these examples.

The model learns to become an assistant that follows instructions and responds aligned with user intent.

### Phase 3: Reinforcement Learning from Human Feedback (RLHF)

Some LLMs like ChatGPT go through RLHF, which further improves alignment and ensures outputs reflect human values and preferences.

---

## How LLMs Can Summarize and Answer Questions

### Summarization

LLMs perform well at summarization because summarization is common in training data (research papers, articles, etc.). The model learned to attend to main points and compress them.

### Knowledge Questions

LLMs answer questions because instruction fine-tuning teaches assistant behavior, but the knowledge itself comes from pre-training on massive amounts of text.

---

## LLM Hallucinations

LLMs sometimes make up facts. Why? The model learns to generate text, not necessarily truthful text. Training data includes unreliable sources. Additionally, confident-sounding text in training data teaches the model to sound confident even when wrong.

### Solution: Grounding with Context

The answer is providing relevant context. If asked "Who is the current president of Colombia?" the model might hallucinate. But if we provide a recent Wikipedia article about Colombian politics, the model can extract the answer from the context.

This is how Bing Chat works: it retrieves relevant context from web searches and passes it to the LLM along with the question.

---

## The AI Magic: Emerging Abilities

### Zero-Shot Learning

LLMs can perform entirely new tasks they haven't been trained on, just from instructions. For example, you can ask an LLM to translate German to English using only words starting with 'f'. It translates "Die Katze schläft gerne in der Box" to "Feline friend finds fluffy fortress."

### Few-Shot Learning

For complex tasks, providing a few examples (demonstrations) helps. Like humans asking for examples before attempting a new task, LLMs benefit from examples. Providing examples often improves performance and reliability.

### Chain-of-Thought Reasoning

For complex multi-step problems, telling an LLM to "think step by step" substantially improves performance. This gives the model a working memory to solve sub-problems before the final answer.

For example, answering "Who won the World Cup the year before Messi was born?" requires: (1) finding Messi's birth year, (2) identifying the prior year, (3) finding that year's World Cup winner. Chain-of-thought lets the model work through these steps.

---

## Conclusion

LLMs work by predicting the next word repeatedly. Yet this simple mechanism, scaled to billions of parameters and trained on massive datasets, produces remarkably capable systems.

Whether LLMs have true understanding or simply learn patterns remains debated. But they demonstrate impressive knowledge and reasoning. The question of how much further language modeling can advance AI remains open.

This article helps you understand LLMs so you can form your own opinions about AI's potential and risks.

---

**Source Article URL:** https://medium.com/data-science-at-microsoft/how-large-language-models-work-91c362f5b78f