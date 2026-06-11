# Transformer Architecture

Transformer architecture is the core design behind modern large language models such as GPT, Llama, and Gemini.

Its main job is to take input text and predict the most likely next token. The key idea that makes transformers powerful is **self-attention**, which lets every token look at other relevant tokens in the sequence.

Reference: [Transformer Explainer](https://poloclub.github.io/transformer-explainer/)

## High-Level Flow

```text
Input Text
   ↓
Tokenization
   ↓
Embedding + Positional Encoding
   ↓
Transformer Blocks
   ↓
Output Probabilities
   ↓
Next Token
```

## 1. Tokenization

The input sentence is split into smaller pieces called **tokens**.

A token can be:

- A word
- Part of a word
- Punctuation
- A special symbol

Example:

```text
Data visualization empowers users to
```

can become:

```text
Data | visualization | empower | s | users | to
```

## 2. Embedding

Computers cannot directly understand words, so each token is converted into a vector.

A vector is a list of numbers that represents the meaning of the token.

Tokens with similar meanings or usage patterns usually have similar vector representations.

## 3. Positional Encoding

Transformers process tokens in parallel, so they need a way to understand word order.

Example:

```text
Dog bites man
Man bites dog
```

Both sentences contain the same words, but the meaning changes because the word order changes.

**Positional encoding** adds position information to each token embedding.

## 4. Transformer Block

The transformer block is the main processing unit of a transformer model.

Large models stack many transformer blocks one after another.

Each transformer block mainly contains:

- Self-attention
- MLP (Multi Layer Perceptron) / feed forward network
- Layer normalization
- Residual connections

## 5. Self-Attention

Self-attention helps each token decide which other tokens are important.

For every token, the model creates three vectors:

| Vector | Meaning |
| --- | --- |
| Query | What this token is looking for |
| Key | What this token offers for matching |
| Value | The actual information this token provides |

Simple analogy:

| Transformer Term | Search Engine Analogy |
| --- | --- |
| Query | Search text |
| Key | Page title or searchable match |
| Value | Page content |

The model compares queries with keys to calculate attention scores.

These scores decide how much each token should pay attention to other tokens.

## 6. Multi-Head Attention

Instead of doing attention once, transformers use multiple attention heads.

Each head can learn a different kind of relationship.

| Head Type | Possible Focus |
| --- | --- |
| Head 1 | Nearby grammar |
| Head 2 | Subject-verb relationship |
| Head 3 | Long-range meaning |
| Head 4 | Repeated concepts |

The outputs from all heads are combined.

## 7. Masked Self-Attention

In text generation models, the model should not see future tokens while predicting the next token.

Example:

```text
The capital of India is
```

The model should predict the next token without already seeing the answer.

This is called **masked self-attention**.

## 8. MLP / Feed Forward Layer

MLP stands for **Multi Layer Perceptron**.

After attention mixes information between tokens, the MLP processes each token individually.

It refines the token representation and helps the model learn more complex patterns.

## 9. Residual Connections and Layer Normalization

Residual connections and layer normalization help deep transformer models train better.

| Component | Purpose |
| --- | --- |
| Residual connections | Preserve earlier information and help gradients flow |
| Layer normalization | Stabilizes training |
| Dropout | Reduces overfitting during training |

## 10. Output Probabilities

After all transformer blocks process the input, the model produces scores for every possible next token in its vocabulary.

These scores are converted into probabilities using softmax.

Example:

| Next Token | Probability |
| --- | --- |
| New | 0.65 |
| Delhi | 0.20 |
| Mumbai | 0.05 |
| city | 0.03 |

The model then selects or samples the next token.

## Summary

```text
Transformer = Embeddings + Positional Encoding + Self-Attention + MLP + Output Prediction
```

The most important concept:

```text
Self-attention lets each token understand its context by looking at other relevant tokens.
```
