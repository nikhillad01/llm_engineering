# Week 1 – LLM Foundations (Interview-Ready Notes)

> **Goal of this document**  
If you read only this document before an interview, you should be able to **clearly explain how LLMs work, how we interact with them, and how they are used in real systems**.

---

## 1. System Prompt

### What it is
A **system prompt** defines the **role, behavior, and response style** of the LLM. It has the **highest priority**.

### Why we need it
- To control tone (teacher, expert, assistant)
- To enforce rules (concise answers, depth, formatting)
- To make responses consistent

### Example
You are an expert software engineer who explains concepts clearly, step by step, with real-world examples.

### Interview one-liner
*A system prompt defines how the LLM should behave and has higher priority than user instructions.*

---

## 2. User Prompt

### What it is
A **user prompt** is the actual question or task given to the model.

### Why it matters
- Prompt clarity directly affects output quality
- Ambiguous prompts lead to ambiguous answers

### Example
Explain transformers in simple terms.

### Interview one-liner
*User prompts are task-specific instructions provided to the LLM within the constraints of the system prompt.*

---

## 3. Frontier Models

### What they are
**Frontier models** are the most advanced, large-scale LLMs available at a given time.

### Examples
- GPT-4 / GPT-4o
- Claude 3
- LLaMA 3 (70B)
- Gemini 1.5

### Why they matter
- Strong reasoning
- Better generalization
- Larger context windows

### Interview one-liner
*Frontier models represent the state-of-the-art in LLM capability and scale.*

---

## 4. Parameters in LLMs

### What they are
**Parameters are learned weights and biases** inside the neural network.

### Key points
- Architecture defines parameter count
- Training assigns parameter values
- Parameters store patterns, not raw data

### Example
7B model → 7 billion learned numbers

### Interview one-liner
*Parameters encode the learned knowledge of an LLM and are fixed during inference.*

---

## 5. Tokens

### What they are
**Tokens are the basic units of text** processed by LLMs.

### Important facts
- LLMs do not understand raw text
- Tokens can be words, sub-words, punctuation, or spaces
- Same tokenizer always produces the same tokens

### Example
"unhappiness" → ["un", "happi", "ness"]

### Interview one-liner
*LLMs operate on tokens, not characters or full words.*

---

## 6. Transformers

### What it is
A **Transformer** is the neural network architecture used by modern LLMs.

### Core components
- Token embeddings
- Self-attention
- Feed-forward layers
- Positional encoding

### Why transformers are powerful
- Parallel processing
- Long-range dependency handling
- Scales efficiently

### Interview one-liner
*Transformers use self-attention to model relationships between all tokens in a sequence.*

---

### 6.2 Self-Attention

**Self-attention** is the core mechanism used in Transformers that allows a model to understand **relationships between tokens within the same input sequence**.

> Each token decides how much attention to pay to other tokens in order to build its meaning.

---

#### Why Self-Attention is Needed

- Language meaning depends on context
- Words can refer to other words far away in a sentence
- Traditional models struggle with long-range dependencies

Self-attention solves this by letting **every token interact with every other token**.

---

#### Simple Intuition

Example sentence: The animal didn’t cross the street because it was tired.

The word **“it”** uses self-attention to focus more on **“animal”** than **“street”**, resolving ambiguity.

---

#### How Self-Attention Works (High Level)

For each token, the model creates three vectors using learned parameters:

- **Query (Q):** what this token is looking for
- **Key (K):** what this token offers
- **Value (V):** the information this token carries

---

#### Core Steps

1. Compare the **Query** of a token with **Keys** of all tokens
2. Compute similarity scores (dot product)
3. Apply **softmax** to get attention weights
4. Generate a weighted sum of **Values**

This produces a **context-aware representation** for each token.

---

#### Example Attention Weights

For the token **“it”**:

| Token   | Attention Weight |
|--------|------------------|
| animal | 0.65 |
| street | 0.05 |
| tired | 0.30 |

---

#### Why It’s Called *Self*-Attention

- Attention is applied **within the same sequence**
- Contrast:
  - **Cross-attention** → between different sequences (e.g., encoder–decoder)

---

#### Multi-Head Self-Attention

- Transformers use multiple attention heads in parallel
- Each head captures different relationships:
  - Grammar
  - Semantic meaning
  - Coreference

---

#### Interview-Ready Definition

> **Self-attention is a mechanism where each token computes weighted influence from all other tokens in the same sequence to form a context-aware representation.**

---

#### Key Takeaway

> **Self-attention allows LLMs to understand meaning by letting tokens attend to each other.**


## 7. Stateless Calls in LLMs

### What it means
LLMs are **stateless by default** and do not remember previous requests.

### Implication
- Every request must include required context
- Conversation history must be resent

### Example
messages = [system, history, user]

### Interview one-liner
*LLMs are stateless; all required context must be provided with each request.*

---

## 8. Context Window

### What it is
The **context window** is the maximum number of tokens an LLM can process at one time.

### Includes
- System prompt
- User prompt
- Conversation history
- Generated output

### Example
Context window: 8k tokens

### Interview one-liner
*Context window defines the LLM’s short-term memory limit measured in tokens.*

---

## 9. stream=True

### What it does
Enables **token-by-token streaming** of responses.

### Why it’s used
- Better user experience
- Faster perceived response
- Real-time output

### Interview one-liner
*Streaming allows LLM responses to be delivered incrementally as tokens are generated.*

---

## 10. Chaining of Prompts

### What it is
Breaking a complex task into **multiple sequential prompts**.

### Why it matters
- Improves reasoning
- Reduces hallucinations
- Easier debugging

### Example
1. Extract requirements  
2. Generate solution  
3. Review output  

### Interview one-liner
*Prompt chaining decomposes complex tasks into manageable LLM calls.*

---

## 11. Additional Concepts (Very Important)

### a) Inference
Using a trained model to generate output without updating parameters.

### b) Deterministic vs Non-deterministic Output
- Temperature = 0 → deterministic output
- Higher temperature → more creative output

### c) Tokens vs Parameters vs Context

| Concept | Role |
|-------|------|
| Tokens | Input/output units |
| Parameters | Long-term knowledge |
| Context window | Short-term memory |

---

## Final Interview Summary (Memorize This)

*LLMs are transformer-based models that process tokenized text using learned parameters. They are stateless systems that rely on context windows for temporary memory. System prompts define behavior, user prompts define tasks, and prompt chaining helps solve complex problems. Streaming improves UX by delivering responses token-by-token.*

---
