# Siddharth Yalamanchili

**I build AI systems and study the engineering decisions that make them useful, understandable, and dependable.**

I'm especially interested in the boundary between model judgment and deterministic software: what an agent should decide, what the system must guarantee, and what evidence lets us understand the result.

## Selected work

### [Causal Desk](https://github.com/Axionis47/causal-inference-agent)

A causal-analysis agent for unfamiliar tabular data. It asks one question at a time, builds source-aware memory, freezes context before execution, and routes the analysis through dedicated adjustment, difference-in-differences, or regression-discontinuity lanes.

The model interprets ambiguity. Code owns the facts, validation, statistical execution, and decision to stop. Users can inspect the evidence and assumptions behind a design, correct them, and compare the revised result.

`Python` · `LangGraph` · `DoWhy` · `PyFixest` · `RDrobust` · `FastAPI` · `React`

[Architecture](https://github.com/Axionis47/causal-inference-agent/blob/main/docs/architecture.md) · [Design decisions](https://github.com/Axionis47/causal-inference-agent/tree/main/docs/adr) · [CI](https://github.com/Axionis47/causal-inference-agent/actions/workflows/ci.yml)

### [FinRAG](https://github.com/Axionis47/finsolve-abac-rag)

A role-aware RAG system built to test when additional retrieval machinery and agent autonomy improve results—and when they only add cost or new failure modes.

It compares three query strategies, seven retrievers, and two rerankers on a 50-question gold set. Access control is enforced before ranking, graph traversal, reranking, and generation. The saved security sweep covered 42 pipelines across six roles and returned 117,798 hits with zero policy violations.

`Python` · `BM25` · `Vector Search` · `GraphRAG` · `Neo4j` · `Vertex AI` · `FastAPI`

[Architecture](https://github.com/Axionis47/finsolve-abac-rag/blob/main/docs/architecture.md) · [Experiments](https://github.com/Axionis47/finsolve-abac-rag/blob/main/docs/experiments.md) · [Security](https://github.com/Axionis47/finsolve-abac-rag/blob/main/docs/security.md)

## What I'm investigating

These projects led me to a broader set of questions about AI engineering:

- How do we give nondeterministic systems useful autonomy without losing control?
- How should agents preserve state, evidence, and obligations across long-running work?
- Which decisions belong to the model, and which belong to deterministic software or a person?
- How do we identify the first broken step in a long trajectory instead of judging only the final answer?
- When does additional agent, retrieval, or tool complexity genuinely improve the system?

I explore these questions through controlled comparisons, failure injection, and explicit evidence in [AI Engineering First Principles](https://github.com/Axionis47/basis-agent-engineering). I'm not looking for one universal architecture; I'm trying to understand the conditions and trade-offs behind each choice.

## How I work

- Start with the outcome, uncertainty, and invariants before choosing a framework.
- Give models room for judgment while keeping permissions, state transitions, calculations, and effects explicit.
- Evaluate the path to an answer, preserve negative results, and change conclusions when the evidence disagrees.

I am currently open to machine-learning and AI-engineering roles.

[Portfolio](https://axionis47.github.io/portfolio/) · [LinkedIn](https://www.linkedin.com/in/siddharth-yalamanchili/) · [Email](mailto:sidsy04@gmail.com)
