# Natural Language Processing - What's the big deal?

**Author:** Skanda Vivek  
**Date:** October 25, 2022

With recent AI advances where algorithms have been called sentient and can explain jokes - this article is a 30,000 foot view on the most important breakthroughs in NLP and their impacts.

---

## Grammar and Machines

In 1957, a struggling linguistics graduate wrote a revolutionary book with a revolutionary premise: by understanding the rules behind grammar, it is possible to predict all grammatical sentences of any language. The author was Noam Chomsky, and the book - Syntactic Structures. The seeds were planted in linguistics and other fields - that machines could learn language; because after all - what are machines good for, if not following complex rules?

Chomsky proposed a hierarchy of grammars where sentences could be represented as trees. In the example below, the sentence "John hit the ball" consists of a noun phrase ("the ball") which in turn is contained by a verb phrase ("hit the ball").

A generative parse tree: the sentence is divided into a noun phrase (subject), and a verb phrase which includes the object. This is in contrast to structural and functional grammar which consider the subject and object as equal constituents.

As the intersection between language and machines started shifting towards computer science, in 1966 a breakthrough was made. Dr. Joseph Weizenbaum at MIT made a computer program that could act as a psychotherapist that could have conversations. If you notice, the responses look like a repetition of the sentence by the patient. This is because ELIZA was based on a set of certain rules given by its creator. This can be viewed as taking the idea of rules governing grammar and language, applied to a conversation. For example, if the patient used a word that conveys similarity such as "like/alike" then ELIZA would respond with some variation of - "In what way?"

## Neural Networks in Language

While many people were convinced ELIZA was intelligent and "understood" them, it was essentially a rule-based system making simple decisions based on inputs. In the early 2010's there were a series of breakthroughs involving Neural Networks and modern computational capabilities that unlocked the potential for machines to learn languages by training them on huge amounts of text data.

But first of all: what are neural networks? It would be quite naïve to summarize a complex concept in just a paragraph - but turns out that the essence of neural networks are quite straightforward and lies in high school algebra. The idea is that if you have a bunch of inputs (x1, x2, x3,…) - through a series of matrix multiplications these can be transformed to an intermediate state (a1, a2, a3, a4,…). After a non-linear transformation (maybe a step function or logistic function) followed by more matrix operations - this can ultimately yield a single number (y) which is either 0 or 1.

Why is this important? Well the 0 or 1 could be mapped to various useful metrics - one example is sentiment analysis: where 0 could represent an unhappy sentiment (e.g. a negative review) or positive sentiment (positive review). And yes - these concepts can be extended to a larger number of outputs - 0, 1, 2, etc.. which could represent a range of sentiments, or something else.

But you might ask - what do the x's represent? You could think that each x represents an individual word and thus by knowing a word's relative position you could map a sentence of say 10 words to a vector of x with length 10. And each x has a unique number. But there are 2 problems here:

1. **For vectors, distance is important.** What I mean is that let's say you assign numbers to words based on their position in the dictionary. "Aardvark" is assigned a value of 1, and apple soon after, etc… The problem with this is that distance here is a meaningless concept and could highly confuse neural networks. This could bias neural networks to associate reviews containing more words starting with the letter A as positive or vice versa.

2. **Computationally expensive** to have a dimensionality the same as the size of the English vocabulary. With hundreds of thousands of words in the English language, it is extremely expensive to assign a dimensionality the same as vocabulary.

Another innovation in neural networks in 2013 called Word2vec solves the above problem by using a neural network to embed the dimensionality into 100-1000. Thus each word now has a dimensionality of hundreds rather than hundreds of thousands - making the use of neural networks for NLP tasks much more accessible.

### Important NLP Tasks

- Sentiment analysis
- Text generation
- Question answering
- Entity extraction
- Language Translation

These are only a few representative tasks - and over the years as NLP is starting to burst new bubbles, we shall see how the list of tasks is also exploding.

For many tasks like language translation; the traditional neural network is inadequate. Researchers came up with a way to take into account the history of preceding words using recurrent neural networks (RNNs). The idea behind RNNs is that each "cell" which is a neural network - takes into account not just the current word; but the output from the previous history of words - giving relevant context for translation (think about how while reading a sentence- just starting from the middle might make no sense and it is best to start from the beginning).

Ex-Tesla AI director Andrej Karapathy has a minimal implementation of an RNN in python using only basic math in approximately 100 lines of code!

## Enter Transformers

In 2017, there was another revolutionary idea in NLP. In the paper "Attention is all you need"- Vaswani et al. detail how training a model to attend to certain parts of a sentence does a much better job than recurrence. The idea is intuitive when considering this analogy: glancing at an entire sentence while translating it seems a better idea than manually going word by word during the translation - in which case you might forget some of the previous parts once you're half-way through the translation. Transformer architectures have taken the NLP world by storm. So far, bigger the model and more the training data - better the performance.

I won't go into the details of transformers in this post - but transformer models are called Large Language Models for a reason - they are trained on large corpuses including Wikipedia articles and books. They are called language models because these models are trained to understand languages; rather than perform specific NLP tasks right at the beginning. For example, the GPT-2 model was trained to predict the next word, given all the previous words in some text. Interestingly, such general language models perform better than the previous state-of-the-art on specific tasks downstream.

## Is something that can hold a meaningful conversation sentient?

Before getting to the recent controversy around whether a google AI chatbot is sentient - let's talk about some relevant transformer results. The GPT-2 model developed by OpenAI was trained to generate long passages by accurately synthesizing the next item in sequences. You can see examples in fictional scenarios such as Edward Snowden becoming president in 2020. As you can see it is remarkably believable and astonishing that the highlighted part was completely generated by an AI model.

Then in June 2022, a Google engineer made a bold claim that a Google chatbot, LaMDA was sentient based on his conversations with it. As you can see it is remarkably convincing.

While there is much controversy around whether or not LaMDA is sentient - it is definitely agreed that the Turing test (a test of intelligence based on whether a machine is indistinguishable from a human) might not be enough to make a judgement on intelligence as it relates to consciousness.

## Closing Thoughts

This was a whirlwind tour of NLP achievements over the years. I didn't even get the chance to talk about recent transformer models that can explain jokes. Along with classic NLP tasks, recent NLP achievements have transformed the way we think about AI and NLP.

Apart from (currently) esoteric discussions on consciousness - there is a booming practical aspect of NLP. We are impacted by this everyday while searching for items on Google - summaries of answers returned are the outputs of such transformer models. The company Hugging Face is on a mission to make state of the art transformer NLP models public. Many organizations are leveraging Hugging Face implementations to transform businesses.

And as for the question of consciousness and intelligence - being the dad of 3 year old twins has shown me just how incredibly different humans and machines are. My kids struggle with basic counting and grammatical rules - but excel in talking our heads off and observing life's details. I'm fascinated by how they learn. Yet, machines are completely different. They are amazing at following rules - they excel at counting, grammar, and vocabulary. But they struggle at holding a decent conversation (although that is changing now). I'm curious what LaMDA would say about what kind of day it has had. Does it even know its own history? Does it remember how it was trained? There is good reason for humans and machines to be different - we wouldn't want a rule based genius of a kid with zero social skills. And we wouldn't want a gregarious machine.

Hopefully we won't need to be concerned with machines like this. Unless of course, someone shows that generalizable AI which can perform multiple language, vision, mechanical, and other sensorial tasks without being plugged to an outlet - trained by roaming freely amongst us - does better than the current state-of-the-art in AI.

If you enjoyed this post, please share on social media or even just one person you think might enjoy holistic perspectives on the interconnections between technology and modern societies. Feel free to also post any comments in the post discussions on the cyber-physical substack page. This is a small, but growing effort and I hope that I can share in my journey in understanding and building resilient societies.

---

**Source:** https://skandavivek.substack.com/p/natural-language-processing-whats
