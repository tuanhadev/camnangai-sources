# What is Generative AI?

By Cole Stryker, Mark Scapicchio

## What is Generative AI?

Generative AI, sometimes called gen AI, is artificial intelligence (AI) that can create original content such as text, images, video, audio or software code in response to a user's prompt or request.

Generative AI relies on sophisticated machine learning models called deep learning models algorithms that simulate the learning and decision-making processes of the human brain. These models work by identifying and encoding the patterns and relationships in huge amounts of data, and then using that information to understand users' natural language requests or questions and respond with relevant new content.

AI has been a hot technology topic for the past decade, but generative AI, and specifically the arrival of ChatGPT in 2022, has thrust AI into worldwide headlines and launched an unprecedented surge of AI innovation and adoption. Generative AI offers enormous productivity benefits for individuals and organizations, and while it also presents very real challenges and risks, businesses are forging ahead, exploring how the technology can improve their internal workflows and enrich their products and services. According to research by the management consulting firm McKinsey, one third of organizations are already using generative AI regularly in at least one business function. Industry analyst Gartner projects more than 80% of organizations will have deployed generative AI applications or used generative AI application programming interfaces (APIs) by 2026.

## How Generative AI Works

For the most part, generative AI operates in three phases:

- **Training**, to create a foundation model that can serve as the basis of multiple gen AI applications.
- **Tuning**, to tailor the foundation model to a specific gen AI application.
- **Generation, evaluation and retuning**, to assess the gen AI application's output and continually improve its quality and accuracy.

### Training

Generative AI begins with a foundation model, a deep learning model that serves as the basis for multiple different types of generative AI applications. The most common foundation models today are large language models (LLMs), created for text generation applications, but there are also foundation models for image generation, video generation, and sound and music generation as well as multimodal foundation models that can support several kinds of content generation.

To create a foundation model, practitioners train a deep learning algorithm on huge volumes of raw, unstructured, unlabeled data e.g., terabytes of data called from the internet or some other huge data source. During training, the algorithm performs and evaluates millions of 'fill in the blank' exercises, trying to predict the next element in a sequence e.g., the next word in a sentence, the next element in an image, the next command in a line of code and continually adjusting itself to minimize the difference between its predictions and the actual data (or 'correct' result).

The result of this training is a neural network of parameters, encoded representations of the entities, patterns and relationships in the data, that can generate content autonomously in response to inputs, or prompts.

This training process is compute-intensive, time-consuming and expensive: it requires thousands of clustered graphics processing units (GPUs) and weeks of processing, all of which costs millions of dollars. Open-source foundation model projects, such as Meta's Llama-2, enable gen AI developers to avoid this step and its costs.

### Tuning

Metaphorically speaking, a foundation model is a generalist: It knows a lot about a lot of types of content, but often can't generate specific types of output with desired accuracy or fidelity. For that, the model must be tuned to a specific content generation task. This can be done in a variety of ways.

#### Fine Tuning

Fine tuning involves feeding the model labeled data specific to the content generation application questions or prompts the application is likely to receive, and corresponding correct answers in the desired format. For example, if a development team is trying to create a customer service chatbot, it would create hundreds or thousands of documents containing labeled customers service questions and correct answers, and then feed those documents to the model.

Fine-tuning is labor-intensive. Developers often outsource the task to companies with large data-labeling workforces.

#### Reinforcement Learning with Human Feedback (RLHF)

In RLHF, human users respond to generated content with evaluations the model can use to update the model for greater accuracy or relevance. Often, RLHF involves people 'scoring' different outputs in response to the same prompt. But it can be as simple as having people type or talk back to a chatbot or virtual assistant, correcting its output.

### Generation, Evaluation, More Tuning

Developers and users continually assess the outputs of their generative AI apps, and further tune the model even as often as once a week for greater accuracy or relevance. (In contrast, the foundation model itself is updated much less frequently, perhaps every year or 18 months.)

Another option for improving a gen AI app's performance is retrieval augmented generation (RAG). RAG is a framework for extending the foundation model to use relevant sources outside of the training data, to supplement and refine the parameters or representations in the original model. RAG can ensure a generative AI app always has access to the most current information. As a bonus, the additional sources accessed via RAG are transparent to users in a way that the knowledge in the original foundation model is not.

## Generative AI Model Architectures and How They Have Evolved

Truly generative AI models deep learning models that can autonomously create content on demand have evolved over the last dozen years or so. The milestone model architectures during that period include

- **Variational Autoencoders (VAEs)**, which drove breakthroughs in image recognition, natural language processing and anomaly detection.
- **Generative Adversarial Networks (GANs) and diffusion models**, which improved the accuracy of previous applications and enabled some of the first AI solutions for photo-realistic image generation.
- **Transformers**, the deep learning model architecture behind the foremost foundation models and generative AI solutions today.

### Variational Autoencoders (VAEs)

An autoencoder is a deep learning model comprising two connected neural networks: One that encodes (or compresses) a huge amount of unstructured, unlabeled training data into parameters, and another that decodes those parameters to reconstruct the content. Technically, autoencoders can generate new content, but they're more useful for compressing data for storage or transfer, and decompressing it for use, than they are for high-quality content generation.

Introduced in 2013, variational autoencoders (VAEs) can encode data like an autoencoder, but decode multiple new variations of the content. By training a VAE to generate variations toward a particular goal, it can 'zero in' on more accurate, higher-fidelity content over time. Early VAE applications included anomaly detection (e.g., medical image analysis) and natural language generation.

### Generative Adversarial Networks (GANs)

GANs, introduced in 2014, also comprise two neural networks: A generator, which generates new content, and a discriminator, which evaluates the accuracy and quality the generated data. These adversarial algorithms encourages the model to generate increasingly high-quality outputs.

GANs are commonly used for image and video generation, but can generate high-quality, realistic content across various domains. They've proven particularly successful at tasks as style transfer (altering the style of an image from, say, a photo to a pencil sketch) and data augmentation (creating new, synthetic data to increase the size and diversity of a training data set).

### Diffusion Models

Also introduced in 2014, diffusion models work by first adding noise to the training data until it's random and unrecognizable, and then training the algorithm to iteratively diffuse the noise to reveal a desired output.

Diffusion models take more time to train than VAEs or GANs, but ultimately offer finer-grained control over output, particularly for high-quality image generation tool. DALL-E, Open AI's image-generation tool, is driven by a diffusion model.

### Transformers

First documented in a 2017 paper published by Ashish Vaswani and others, transformers evolve the encoder-decoder paradigm to enable a big step forward in the way foundation models are trained, and in the quality and range of content they can produce. These models are at the core of most of today's headline-making generative AI tools, including ChatGPT and GPT-4, Copilot, BERT, Bard, and Midjourney to name a few.

Transformers use a concept called attention, determining and focusing on what's most important about data within a sequence to;

- process entire sequences of data e.g., sentences instead of individual words simultaneously;
- capture the context of the data within the sequence;
- encode the training data into embeddings (also called hyperparameters) that represent the data and its context.

In addition to enabling faster training, transformers excel at natural language processing (NLP) and natural language understanding (NLU), and can generate longer sequences of data e.g., not just answers to questions, but poems, articles or papers with greater accuracy and higher quality than other deep generative AI models. Transformer models can also be trained or tuned to use tools e.g., a spreadsheet application, HTML, a drawing program to output content in a particular format.