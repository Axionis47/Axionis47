# Siddharth Yalamanchili

**My guiding principle: high-quality AI solutions begin with a deep understanding of the problem.**

My approach starts with the people doing the work, their actual needs, the domain, the existing workflow, and the consequences of getting it wrong. Understanding the problem means questioning assumptions, separating symptoms from causes, identifying constraints, and defining what a useful outcome would look like.

That understanding guides what needs a model, what belongs in software, what requires human judgment, and how completion can be verified. Context assembly, tools, and architecture follow those decisions. Early experiments test the assumptions and deepen the understanding as the system develops.

## My first-principles approach

### Understand the problem deeply and define completion

Who is the system helping? Where does the current workflow fail, and why? What must improve? Which facts are authoritative, what could be missing, and what would make the result unacceptable? A clear success contract, explicit non-goals, and a simpler baseline give later design choices something to answer to.

### Turn application knowledge into behavior

Domain meaning, evidence requirements, permissions, valid state transitions, and completion criteria should change what the system does. Retrieval rules, context contracts, tool validation, runtime checks, and evaluation cases make that knowledge operational. Unresolved assumptions remain visible.

### Allocate judgment and authority

Identities, calculations, permissions, and valid state transitions belong behind enforceable software contracts. Models can handle interpretation and investigation within explicit boundaries. Human authority depends on consequences, accountability, reversibility, and unresolved uncertainty.

### Assemble context for the decision

Retrieval finds candidate evidence; assembly determines what reaches a particular decision. The task determines which sources qualify, what must appear together, how contradictions are represented, and when evidence is sufficient. Preloaded context, selective hydration, adaptive retrieval, graph expansion, and combinations of these are alternatives to investigate. Their value depends on the task and evidence.

### Make execution observable and recoverable

A model proposal crosses explicit boundaries: validated arguments, permission checks, tool execution, observations, artifacts, and state transitions. Completion requires evidence. Missing information, partial failure, interruption, and ambiguous effects need defined recovery or escalation paths.

### Evaluate outcomes and the path taken

Checks need the right granularity: functions, model outputs, nodes, tools, transitions, trajectories, and end-to-end outcomes. Deterministic checks cover exact contracts; semantic assessment needs explicit rubrics and calibration. Traces help locate the first observable broken contract. Controlled interventions test causal explanations.

### Treat latency, cost, and reliability as design constraints

Time to a useful response differs from time to verified completion. Model calls, context work, tools, persistence, retries, and review each contribute overhead. Maintained tools deserve evaluation for the infrastructure code and effort they save, alongside their setup, runtime, and maintenance costs.

## My learning questions

These are open areas of investigation. Each needs credible alternatives, visible failures, and evidence about when the choice should change.

| Area | Questions guiding the learning |
| --- | --- |
| Problem understanding and approach | Is the stated problem the underlying problem? How does the work happen today? Is a model needed? What can a simpler workflow achieve, and what evidence would establish improvement? |
| Context assembly | When is a fixed evidence bundle sufficient? When should retrieval adapt? How should ordering, compression, dependencies, conflicting sources, freshness, and access affect assembly? |
| Agency and tools | Which decisions benefit from autonomy? When do small primitives, semantic tools, or workflow tools reduce effort without hiding essential choices? |
| State and recovery | What is canonical truth, model context, memory, or an artifact? Where do checkpoints help, and how should interrupted or duplicated work resume safely? |
| Evaluation and visibility | What belongs at node, tool, trajectory, and outcome level? How can text, image, audio, and mixed-media tasks be assessed? Where do exact checks, calibrated judges, and human review fit? |
| Operational trade-offs | How do quality, latency, cost, reviewer effort, and recovery change across designs? Which tools save enough code and maintenance to justify their overhead? |

## Following one requirement through the system

Suppose a task requires the correct reporting period. That requirement should change the application at several boundaries:

| Boundary | Resulting behavior |
| --- | --- |
| Intent | Clarify fiscal versus calendar periods when necessary |
| Retrieval | Select eligible sources for the requested entity, period, and version |
| Context | Preserve period metadata and expose conflicts or missing evidence |
| Acceptance | Check cited source identities and period metadata; require support for the conclusion |
| Evaluation | Test wrong-period, missing-source, and conflicting-source cases |
| Trace | Record which source versions reached the decision and which checks passed |

The principle: **what the application knows should determine what it retrieves, allows, verifies, rejects, or asks about.**

## My learning loop

Frame the task, make assumptions explicit, compare credible alternatives, inject failures, inspect the first broken contract, and explain the trade-off. Controlled studies isolate one variable and report limitations. Implemented behavior, measured results, and proposed improvements stay distinct. A useful conclusion states when a design is appropriate and what evidence would change that choice.

Implementation and investigation: [Causal Desk](https://github.com/Axionis47/causal-inference-agent) · [FinRAG](https://github.com/Axionis47/finsolve-abac-rag) · [AI Engineering First Principles](https://github.com/Axionis47/basis-agent-engineering).

Open to machine-learning and AI-engineering roles.

[Portfolio](https://axionis47.github.io/portfolio/) · [LinkedIn](https://www.linkedin.com/in/siddharth-yalamanchili/) · [Email](mailto:sidsy04@gmail.com)
