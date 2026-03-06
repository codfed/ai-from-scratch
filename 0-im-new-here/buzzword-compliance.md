# Buzzword Compliance Q1 2026

# LLM

Large Language model. Essentially... research labs took the entire internet and all recorded text that seemed useful and converted it into mathematical vectors (embedded). Words with similar meanings share a similar vector space. Then they trained the model on this data.

When you ask a question or assign a task, the LLM builds its response by mathematically calculating which word is most likely to be next.

# Vector DB

Since we're working with vectors, we need to store them.

These are simple... you take any existing DB technology (PostgreSQL, NoSQL) and add two things

- Datatype (PGVector)
- Mathematical operations to find similar vectors

---

# Problem

LLMs only know the training data. But for every use case we want it to know specific domain knowledge and current events.

# Solutions

- RAG
- Tool Calling

# Problem

I want it to do more than just chat

# Solution

Agents

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

### Replit

### v0 (Vercel)

### Lovable / Bolt

## Household Names (Products & Tools)

### Cursor

### Perplexity

### Midjourney

### Replit

### NotebookLM (Google)

---

## The Technical Buzzword Arc

These concepts roughly track the evolution of what developers were building — each wave building on the last.

### 1. LLMs / Foundation Models (2020–present)

**Large Language Models** are neural networks trained on massive text datasets to predict the next token. "Foundation model" means a model general enough to be fine-tuned or prompted for many tasks. GPT, Claude, Gemini, Llama are all LLMs.

Key sub-terms:

- **Parameters**: The "knobs" in the network. More parameters ≠ always better, but it's a size proxy.
- **Context window**: How much text the model can "see" at once. Grew from ~4K tokens in GPT-3 to 200K+ in Claude 3.
- **Tokens**: The chunks text is split into — roughly ¾ of a word. Models think in tokens, not words.
- **Hallucination**: When a model confidently states something false. The core reliability problem.

### 2. Prompt Engineering (2022–2023)

The art of writing inputs that get better outputs. "Zero-shot" (just ask), "few-shot" (give examples), "chain-of-thought" (ask the model to reason step by step). Briefly a hot job title before models got good enough to require less hand-holding.

### 3. Fine-tuning & RLHF (2022–2023)

**Fine-tuning** = taking a base model and training it further on your specific data/task. **RLHF** (Reinforcement Learning from Human Feedback) is how OpenAI turned GPT-3 into the helpful ChatGPT you know — humans rated outputs, the model learned to produce highly-rated ones. The technique behind why these models are pleasant to talk to rather than just predicting text.

### 4. Embeddings & Vector Databases (2023)

**Embeddings** convert text into numbers (vectors) that capture semantic meaning. Similar meaning = similar numbers = close together in vector space. This unlocks semantic search: "find me documents about contract disputes" works even if none of them contain those exact words.

**Vector databases** (Pinecone, Chroma, Weaviate, pgvector) store and search these embeddings efficiently. They became critical infrastructure when RAG took off.

### 5. RAG — Retrieval Augmented Generation (2023)

The dominant pattern for giving an LLM access to your data without fine-tuning it. The flow:

1. User asks a question
2. Search your documents for relevant chunks (using embeddings)
3. Stuff those chunks into the prompt as context
4. LLM answers using that context

This repo has three RAG notebooks — it's the thing worth learning deeply. RAG is why you can ask Claude about a 79-page NTSB report and get accurate answers: the relevant pages are retrieved and handed to the model.

### 6. Function Calling / Tools (2023)

Models can now emit structured outputs that trigger real actions. The model doesn't execute code directly — it outputs something like `{"function": "search_web", "query": "current weather in Chicago"}` and your code runs the actual function. This is what makes AI "do things" rather than just "say things."

### 6. Function Calling / Tools (2023)

### 7. Agents (2024)

### 8. MCP — Model Context Protocol (late 2024)

### 9. Skills (2025–present)

An **agent** is a model in a loop: it takes an action, observes the result, decides the next action, repeats. Instead of one prompt → one answer, you get a model that can browse the web, write code, run it, fix errors, and iterate — autonomously.

LangChain and LlamaIndex were the first popular frameworks for building these. The term got overloaded fast — everything became an "AI agent" whether it deserved the label or not.

**Multi-agent systems**: multiple specialized agents working together. One agent plans, one searches, one writes code, one reviews it. Research area that's moving fast.

### 8. MCP — Model Context Protocol (late 2024)

Invented by Anthropic. MCP is a standard protocol for connecting AI models to external tools and data sources. Think of it like USB — instead of every AI app writing custom integrations with every tool, you build one MCP server and any MCP-compatible model can use it.

Before MCP: custom integration work for every tool + every model combination.
After MCP: write it once, works everywhere that speaks the protocol.

Adoption exploded through 2025. If you see "MCP server" in a repo, someone has wrapped a tool (filesystem, database, web browser, API) in the protocol so agents can use it.

### 8. MCP — Model Context Protocol (late 2024)

### 9. Skills (2025–present)

Packaged, reusable capabilities for agents. Where function calling is low-level ("call this function"), skills are higher-level ("know how to handle git operations" or "know how to review a PR"). The abstraction above tools — composed behaviors that agents can invoke. You're in a repo that has Claude Code skills right now.

### 10. Vibe Coding (2025)

Term coined by Andrej Karpathy (ex-OpenAI, ex-Tesla). Describes programming by describing intent in natural language and letting an AI write the code — the developer "vibes" the direction without writing syntax. Cursor is the primary tool. The philosophical shift: programming becomes closer to product management than to typing code.

---

## The Reasoning Model Turn (2024–2025)

OpenAI's **o1** (late 2024) introduced a new pattern: instead of responding immediately, the model "thinks" — running an internal chain-of-thought before answering. Slower, more expensive, dramatically better at hard math/logic/coding problems.

**o3** followed, then DeepSeek R1 proved you could do this open-source. Anthropic shipped **Claude 3.7 Sonnet with extended thinking**. Reasoning models became the default choice for hard tasks.

The buzzword: **inference-time compute** — spending more compute at answer time (rather than just at training time) to get better results.

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
