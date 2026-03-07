# Buzzword Compliance Q1 2026

# LLM

Large Language model. Essentially... research labs took the entire internet and all recorded text that seemed useful and converted it into mathematical vectors. Words with similar meanings share a similar vector space. Then they trained the model on this data.

When you ask a question or assign a task, the LLM builds its response by mathematically calculating which word is most likely to be next.

### LLM keywords

- **Parameters**: The "knobs" in the network. More parameters ≠ always better, but it's a size proxy.
- **Tokens**: The chunks text is split into — roughly ¾ of a word. Models think in tokens, not words.
- **Context Window**: There is a finite amount of data the LLM can handle at a given time. This fills up quickly and needs to be managed carefully.

# Embeddings & Vector DBs

Since we're working with vectors, we need to store them.

These are simple... you take any existing DB technology (PostgreSQL, NoSQL) and add two things

- Datatype (PGVector)
- Mathematical operations to find similar vectors

---

# Problem

LLMs only know the training data. But for every use case we want it to know specific domain knowledge and current events.

# Solutions

- Fine Tuning
- RAG
- Tool Calling

---

# Problem

I want it to give me more concise, useful, full answers

# Solution

Prompt Engineeringf

---

# Problem

I want it to do things for me

# Solution

- Agents
- MCP
- Skills

---

# Labs

## Closed Weight

- OpenAI
- Anthropic
- Google Deepmind
- xAI

## Open Weight

- Mistral AI
- Deepseek

---

# Tools

## Rapid development/deployment

- Replit
- v0 (Vercel)
- Lovable / Bolt
- Antigravity

# Very Impressive Products

- NotebookLM (Google)
- Wispr Flow

# Viral

- Open Claw

---

## What's Real vs. Marketing

| Sounds like               | Actually means                                    |
| ------------------------- | ------------------------------------------------- |
| "AI-powered"              | Uses an LLM API somewhere                         |
| "Agentic"                 | Model runs in a loop with tools                   |
| "Autonomous"              | Still needs human review for anything important   |
| "Fine-tuned on your data" | Could just be RAG, check carefully                |
| "100B parameter model"    | Big, but parameters alone don't determine quality |
| "Reasoning model"         | Chain-of-thought at inference time                |
| "Multimodal"              | Can handle images/audio/video, not just text      |

---

## The Rough Timeline

| Date     | Event                                                 |
| -------- | ----------------------------------------------------- |
| Nov 2022 | ChatGPT public release                                |
| Feb 2023 | Microsoft Bing + GPT-4 integration                    |
| Mar 2023 | GPT-4, Claude 1, Llama 1, Google Bard                 |
| Mid 2023 | RAG becomes dominant pattern; LangChain explodes      |
| Jul 2023 | Llama 2 (Meta open weights)                           |
| Nov 2023 | OpenAI DevDay: GPT store, function calling mainstream |
| Mar 2024 | Claude 3 family (Haiku/Sonnet/Opus) — major leap      |
| Mid 2024 | Cursor becomes a household name                       |
| Jun 2024 | Claude 3.5 Sonnet crushes coding benchmarks           |
| Sep 2024 | o1 — reasoning models go mainstream                   |
| Nov 2024 | MCP announced by Anthropic                            |
| Jan 2025 | DeepSeek R1 shocks the industry                       |
| Feb 2025 | Claude 3.7 Sonnet with extended thinking              |
| 2025     | "Vibe coding" enters the vocabulary                   |
| 2025     | MCP adoption becomes widespread                       |
| 2026     | Agentic AI is the default paradigm                    |

---

## What to Actually Learn

The buzzwords are noise. The signal:

1. **How LLMs actually work** — tokens, attention, why context windows matter
2. **RAG** — the pattern everything else builds on (start with the notebooks in `2-rag/`)
3. **Tool use / function calling** — how agents take actions
4. **Agents** — loops, planning, the new programming model
5. **Prompt craft** — still matters even as models get smarter

The rest is branding.
