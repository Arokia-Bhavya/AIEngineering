# LLM Basics

## Generative AI vs AI Agent vs Agentic AI

| Type | What It Does | How It Works | Example |
| --- | --- | --- | --- |
| Generative AI | Creates new content | Uses a raw LLM to answer based on patterns learned from training data | Answers "New Delhi" when asked, "What is the capital of India?" |
| AI Agent | Takes input, decides what to do, and completes a task | Combines an LLM with tools, memory, and knowledge | Books a flight ticket |
| Agentic AI | Uses multiple agents to complete multi-step goals | Coordinates several tasks or agents toward a larger objective | Checks visa requirements, finds sunny travel dates, books a flight, and suggests hotels |

## Language Models

A language model predicts the next word in a sequence based on the previous words.

### Evolution of Language Models

- **1990s - Statistical models:** N-grams predicted the next word using 2 to 3 prior words.
- **2010s - Recurrent Neural Networks:** RNNs maintain a hidden state that captures information about previous inputs, helping them consider word sequence context.
- **2020s - Large Language Models:** LLMs use billions of parameters and are trained on trillions of tokens.

## Key LLM Parameters

LLM parameters control how much text the model can process and how it chooses the next token while generating a response.

### Context Window

The **context window** is the maximum number of tokens that can be passed to the model at once.

It includes:

- Input prompt
- Conversation history
- Provided documents
- Generated output

| Model | Context Window |
| --- | --- |
| GPT-4o | 128,000 tokens, roughly 96,000 words |
| Llama 3 70B | 8,000 tokens, roughly 6,000 words |
| Gemini 1.5 Pro | 2,000,000 tokens, roughly 1.5 million words |

**Key insight:** A larger context window lets the model remember more of a conversation or read longer documents. However, models can lose attention in the middle of very long contexts. This is called the **lost in the middle** problem.

### Temperature

**Temperature** controls how random or creative the model's output is.

It changes the probability distribution before the model samples the next token.

| Temperature | Effect | Use Case |
| --- | --- | --- |
| 0 | Deterministic; picks the highest-probability token | Code generation, data extraction |
| 0.7 to 1.0 | Balanced creativity | Chatbots, Q&A |
| Above 1.5 | Very random; distribution becomes flatter | Brainstorming, poetry |
| 2 | Near-uniform distribution; output may become gibberish | Avoid in production |

### Top-p and Top-k Sampling

Top-p and top-k limit which tokens the model is allowed to sample from. They reduce incoherence without fully removing randomness.

| Method | Meaning | Best For | Example Tasks |
| --- | --- | --- | --- |
| Top-p, also called nucleus sampling | Samples from the smallest set of top tokens whose cumulative probability is at least `p` | Creative and diverse outputs | Chatbots, storytelling, creative writing |
| Top-k | Samples only from the top `k` highest-probability tokens | Predictable and structured outputs | Code generation, summarization |
| Combined top-k and top-p | Uses both limits together | Balance of quality and diversity | Most production use cases |

Example:

- For `top_p = 0.9`, the model samples from the smallest group of likely tokens whose total probability reaches at least 90%.
- For `top_k = 3`, the model samples only from the 3 most likely tokens.

## Word Embeddings

An embedding represents text as a fixed-length array of numbers, also called a vector.

### Types of Embeddings

- **Static embedding:** Each word gets one fixed vector, regardless of context.
- **Contextual embedding:** Each word gets a vector that changes depending on the surrounding words.

Embeddings can represent:

- Words
- Sentences
- Documents

## Problems in LLM

- Hallucinations
- Security
- Cost
