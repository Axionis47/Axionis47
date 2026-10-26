# Siddharth Yalamanchili

**My starting belief: high-quality AI solutions begin with a deep understanding of the problem.**

My projects are a way to test and refine that belief. The starting questions concern the people doing the work, the outcome they need, the evidence available, and the consequences of being wrong. Where does the workflow break? Which assumptions remain untested? What would establish improvement?

That belief motivated [Causal Desk: asking how a course was assigned before estimating its effect](https://github.com/Axionis47/causal-inference-agent#see-it). The platform starts with a causal question, gathers missing study information, and connects the selected analysis to its evidence and assumptions.

One useful lens for AI engineering is constrained optimization: finding workable combinations of quality, reliability, latency, cost, and human effort within the authority granted. Better combinations may make previously impractical work feasible. **Context management is a particular focus:** how do the right evidence, relationships, obligations, and uncertainty reach each decision?

## Tech stack

Tools used in [Causal Desk](https://github.com/Axionis47/causal-inference-agent) and [FinRAG](https://github.com/Axionis47/finsolve-abac-rag).

**Languages and applications**

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![React](https://img.shields.io/badge/React-20232A?style=flat-square&logo=react&logoColor=61DAFB)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)

**AI and data**

![LangGraph](https://img.shields.io/badge/LangGraph-1C3C3C?style=flat-square&logo=langgraph&logoColor=white)
![LangChain / LangSmith](https://img.shields.io/badge/LangChain_%2F_LangSmith-1C3C3C?style=flat-square&logo=langchain&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat-square&logo=numpy&logoColor=white)
![pandas](https://img.shields.io/badge/pandas-150458?style=flat-square&logo=pandas&logoColor=white)
![Pydantic](https://img.shields.io/badge/Pydantic-E92063?style=flat-square&logo=pydantic&logoColor=white)
![Neo4j](https://img.shields.io/badge/Neo4j-4581C3?style=flat-square&logo=neo4j&logoColor=white)

**Infrastructure and development tools**

![Google Cloud](https://img.shields.io/badge/Google_Cloud-4285F4?style=flat-square&logo=googlecloud&logoColor=white)
![SQLite](https://img.shields.io/badge/SQLite-003B57?style=flat-square&logo=sqlite&logoColor=white)
![pytest](https://img.shields.io/badge/pytest-0A9EDC?style=flat-square&logo=pytest&logoColor=white)
![Ruff](https://img.shields.io/badge/Ruff-261230?style=flat-square&logo=ruff&logoColor=D7FF64)
![Vite](https://img.shields.io/badge/Vite-646CFF?style=flat-square&logo=vite&logoColor=white)

## Questions shaping my work

These notes capture my current understanding through concrete cases, competing approaches, and questions that remain open. Different tasks may call for different choices, and better evidence may change these views. The constructed cases are illustrative; linked project examples are identified separately.

### Which part of the problem needs a model?

An invoice review queue takes three days. Is the bottleneck interpretation, missing purchase orders, or an approval handoff? Those explanations suggest different interventions: model judgment, better intake, or a workflow change. The question is whether faster generation would address the actual delay.

[Find why the reviewer waits three days](thinking/problem-understanding.md#people-and-workflow) · [Check whether course assignment changes the explanation](thinking/problem-understanding.md#causes-and-assumptions) · [Define when a disputed invoice is resolved](thinking/problem-understanding.md#completion-and-failure-costs) · [Compare model judgment with better intake](thinking/problem-understanding.md#baselines-and-feasibility)

### How should domain knowledge affect acceptance?

A revenue figure has a valid citation, but the source covers Q2 and the user asked for Q3. Where could that mismatch be caught: source eligibility, context assembly, or acceptance? This case explores how a domain requirement might become checks across those boundaries.

[Reject a Q2 source for a Q3 request](thinking/knowledge-contracts.md#domain-meaning) · [Carry quarter identity from search to acceptance](thinking/knowledge-contracts.md#requirements-across-boundaries) · [Reject an unsupported claim despite valid JSON](thinking/knowledge-contracts.md#structural-and-semantic-contracts) · [Recheck approval when the policy changes](thinking/knowledge-contracts.md#versions-and-change)

### What context does this decision actually need?

A policy says approval is required above a threshold. Its footnote exempts a particular contract type. Retrieving the main rule without the exception changes the decision. Preloading a complete bundle, retrieving adaptively, and expanding relationships each help under different conditions and introduce different failure modes.

[Check whether the policy is current and applicable](thinking/context-management.md#evidence-selection) · [Keep the footnote exception beside the rule](thinking/context-management.md#assembly-and-dependencies) · [Preserve a pending confirmation during compression](thinking/context-management.md#freshness-and-compression) · [Stop revoked evidence leaking through a summary](thinking/context-management.md#access-and-injection)

Project-reported counterexample: [FinRAG's temporal graph displaced the correct Q3 source](https://github.com/Axionis47/finsolve-abac-rag#what-the-tests-showed). More connected evidence did not automatically produce a better selection.

### Where should the tool boundary sit?

Resolving a disputed invoice could involve several small calls, one evidence-gathering operation, or a whole-workflow tool. Each boundary offers different flexibility, model effort, visibility, and recovery options. Which consequential choices or partial failures become harder to inspect as more work moves inside the tool?

[Separate invoice interpretation from payment authority](thinking/agency-tools.md#decision-allocation) · [Compare invoice primitives with an evidence-bundle tool](thinking/agency-tools.md#tool-abstraction) · [Reject changed arguments after approval](thinking/agency-tools.md#authority-and-effects) · [Count setup, debugging, and code a tool saves](thinking/agency-tools.md#engineering-effort)

### What can be trusted after an interrupted write?

An update succeeds, but the process stops before saving its receipt. Retrying might duplicate the action; assuming success might lose unfinished work. The recovery choice depends on what the external system can prove and what authority remains valid.

[Store invoice facts separately from working context](thinking/state-recovery.md#truth-and-representations) · [Choose which investigation work must survive a crash](thinking/state-recovery.md#checkpoint-boundaries) · [Retry, reconcile, or escalate an uncertain write](thinking/state-recovery.md#effects-and-recovery) · [Handle two workers updating the same invoice](thinking/state-recovery.md#concurrency-and-evolution)

### What would explain a plausible but wrong answer?

A polished Q3 answer can hide a retrieval error, an assembly omission, or a missing acceptance check. Outcome scores may flag a problem; node and tool evidence may help locate the first observable break. The example asks which observations would distinguish those explanations before choosing a fix.

[Trace a wrong-quarter answer to its first failure](thinking/evaluation-observability.md#evaluation-units) · [Check invoice-image totals and attributed speech](thinking/evaluation-observability.md#rubrics-and-multimodal-evidence) · [Separate LangGraph node time from tool time](thinking/evaluation-observability.md#tracing-and-causality) · [Catch a tenant leak behind a passing average](thinking/evaluation-observability.md#regression-and-rollout)

### What does improvement mean for the whole task?

**What we cannot measure, we cannot improve.**

A cheaper model call may require more retries or reviewer corrections. A fast first response may still leave the task waiting for verification. The accounting example asks whether an apparent saving survives once unsuccessful attempts, supporting services, and review effort are visible alongside quality.

[Reject a faster design that misses the task contract](thinking/optimization.md#feasible-trade-offs) · [Follow overlapping work to verified completion](thinking/optimization.md#latency-and-critical-paths) · [Calculate whether cheaper calls reduce task cost](thinking/optimization.md#cost-per-successful-task) · [Separate model evidence from infrastructure failure](thinking/optimization.md#controlled-measurements)

The [case index and evidence policy](thinking/README.md) connect these working notes. Feedback, counterexamples, and better ways to frame the problems are welcome.

Open to machine-learning and AI-engineering roles.

[Portfolio](https://axionis47.github.io/portfolio/) · [LinkedIn](https://www.linkedin.com/in/siddharth-yalamanchili/) · [Email](mailto:sidsy04@gmail.com)
