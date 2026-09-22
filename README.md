# Siddharth Yalamanchili

**I build AI systems that can take initiative without losing evidence, control, or accountability.**

I care about the line between model judgment and deterministic software. Models should have room to reason where judgment helps; permissions, state, calculations, and acceptance should remain explicit and testable.

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

## How I work

- Give models freedom where judgment is useful; put hard guarantees around evidence, permissions, execution, and approval.
- Evaluate the path to an answer—retrieval, tool choices, checks, and failure behavior—not only the final prose.
- Keep negative results. If a more complex method performs worse, that is an engineering result, not an embarrassment.
- Use coding agents heavily, with clear contracts, tests, review, and explicit acceptance criteria.

I am currently open to machine-learning and AI-engineering roles.

[Portfolio](https://axionis47.github.io/portfolio/) · [LinkedIn](https://www.linkedin.com/in/siddharth-yalamanchili/) · [Email](mailto:sidsy04@gmail.com)
