# Buzzword Compliance Q1 2026

# LLM

Large Language model. Essentially... research labs took the entire internet and all recorded text that seemed useful and converted it into mathematical vectors. Words with similar meanings share a similar vector space. Then they trained the model on this data.

When you ask a question or assign a task, the LLM builds its response by mathematically calculating which word is most likely to be next.

# Vector DB

Since we're working with vectors, we need to store them.

These are simple... you take any existing DB technology (PostgreSQL, NoSQL) and add two things

- Datatype (PGVector)
- Mathematical operations to find similar vectors

---

# Problem

LLMs only know the training data. But for every use case we want it to know specific domain knowledge and current events.

# Solution: RAG

---

LLMs only know the data they were

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
