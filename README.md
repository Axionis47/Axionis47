# Siddharth Yalamanchili

**My guiding principle: high-quality AI solutions begin with a deep understanding of the problem.**

My approach starts with the people doing the work, the outcome they need, the evidence available, and the consequences of being wrong. The useful questions are concrete: where does the workflow break, which assumptions remain untested, and what would establish improvement?

That belief motivated [Causal Desk: asking how a course was assigned before estimating its effect](https://github.com/Axionis47/causal-inference-agent#see-it). The platform starts with a causal question, gathers missing study information, and connects the selected analysis to its evidence and assumptions.

AI engineering is a constrained optimization problem: finding useful combinations of quality, reliability, latency, cost, and human effort within the authority granted. Better combinations can make previously impractical work feasible. **Context management is central:** every decision depends on which evidence, relationships, obligations, and uncertainty reach it.

## My thinking patterns, through concrete cases

The cases below are illustrative engineering situations. Linked project examples are identified separately. Each extension shows the competing choices, the catch, and the evidence that could change the decision.

### Understand the problem before choosing the system

An invoice review queue takes three days. Is the bottleneck interpretation, missing purchase orders, or an approval handoff? Those explanations suggest different interventions: model judgment, better intake, or a workflow change. Faster generation helps only if it addresses the actual delay.

[Find why the reviewer waits three days](thinking/problem-understanding.md#people-and-workflow) · [Check whether course assignment changes the explanation](thinking/problem-understanding.md#causes-and-assumptions) · [Define when a disputed invoice is resolved](thinking/problem-understanding.md#completion-and-failure-costs) · [Compare model judgment with better intake](thinking/problem-understanding.md#baselines-and-feasibility)

### Make domain knowledge change behavior

A revenue figure has a valid citation, but the source covers Q2 and the user asked for Q3. The requirement must affect source eligibility, context assembly, and acceptance. A well-formed answer can still fail the task.

[Reject a Q2 source for a Q3 request](thinking/knowledge-contracts.md#domain-meaning) · [Carry quarter identity from search to acceptance](thinking/knowledge-contracts.md#requirements-across-boundaries) · [Reject an unsupported claim despite valid JSON](thinking/knowledge-contracts.md#structural-and-semantic-contracts) · [Recheck approval when the policy changes](thinking/knowledge-contracts.md#versions-and-change)

### Assemble context around the decision

A policy says approval is required above a threshold. Its footnote exempts a particular contract type. Retrieving the main rule without the exception changes the decision. Preloading a complete bundle, retrieving adaptively, and expanding relationships each help under different conditions and introduce different failure modes.

[Check whether the policy is current and applicable](thinking/context-management.md#evidence-selection) · [Keep the footnote exception beside the rule](thinking/context-management.md#assembly-and-dependencies) · [Preserve a pending confirmation during compression](thinking/context-management.md#freshness-and-compression) · [Stop revoked evidence leaking through a summary](thinking/context-management.md#access-and-injection)

Project-reported counterexample: [FinRAG's temporal graph displaced the correct Q3 source](https://github.com/Axionis47/finsolve-abac-rag#what-the-tests-showed). More connected evidence did not automatically produce a better selection.

### Put tool boundaries where the choices belong

Resolving a disputed invoice could require several small calls, one evidence-gathering operation, or a whole-workflow tool. The boundary changes flexibility, model effort, visibility, and recovery. A tool that saves calls still needs to expose consequential choices and partial failure.

[Separate invoice interpretation from payment authority](thinking/agency-tools.md#decision-allocation) · [Compare invoice primitives with an evidence-bundle tool](thinking/agency-tools.md#tool-abstraction) · [Reject changed arguments after approval](thinking/agency-tools.md#authority-and-effects) · [Count setup, debugging, and code a tool saves](thinking/agency-tools.md#engineering-effort)

### Design for the gap between effect and receipt

An update succeeds, but the process stops before saving its receipt. Retrying might duplicate the action; assuming success might lose unfinished work. The recovery choice depends on what the external system can prove and what authority remains valid.

[Store invoice facts separately from working context](thinking/state-recovery.md#truth-and-representations) · [Choose which investigation work must survive a crash](thinking/state-recovery.md#checkpoint-boundaries) · [Retry, reconcile, or escalate an uncertain write](thinking/state-recovery.md#effects-and-recovery) · [Handle two workers updating the same invoice](thinking/state-recovery.md#concurrency-and-evolution)

### Evaluate the path behind a plausible answer

A polished Q3 answer can hide a retrieval error, an assembly omission, or a missing acceptance check. Outcome scores identify a problem; node and tool evidence help locate the first observable break. Different faults call for different fixes.

[Trace a wrong-quarter answer to its first failure](thinking/evaluation-observability.md#evaluation-units) · [Check invoice-image totals and attributed speech](thinking/evaluation-observability.md#rubrics-and-multimodal-evidence) · [Separate LangGraph node time from tool time](thinking/evaluation-observability.md#tracing-and-causality) · [Catch a tenant leak behind a passing average](thinking/evaluation-observability.md#regression-and-rollout)

### Optimize the completed task

**What we cannot measure, we cannot improve.**

A cheaper model call may require more retries or reviewer corrections. A fast first response may still leave the task waiting for verification. Cost and latency need a declared accounting boundary, meaningful completion criteria, and visible quality and reliability constraints.

[Reject a faster design that misses the task contract](thinking/optimization.md#feasible-trade-offs) · [Follow overlapping work to verified completion](thinking/optimization.md#latency-and-critical-paths) · [Calculate whether cheaper calls reduce task cost](thinking/optimization.md#cost-per-successful-task) · [Separate model evidence from infrastructure failure](thinking/optimization.md#controlled-measurements)

My [case index and evidence policy](thinking/README.md) connect these examples. The choices remain conditional, and the design space remains open.

Open to machine-learning and AI-engineering roles.

[Portfolio](https://axionis47.github.io/portfolio/) · [LinkedIn](https://www.linkedin.com/in/siddharth-yalamanchili/) · [Email](mailto:sidsy04@gmail.com)
