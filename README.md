# Siddharth Yalamanchili

**I approach AI engineering by understanding the task, turning application knowledge into system behavior, and testing whether the result deserves trust.**

I start with the outcome, the evidence required to support it, and the consequences of being wrong. Those requirements shape context, model autonomy, tools, state, and evaluation. Architecture follows the problem.

## My first-principles approach

### Understand the problem and define completion

Who is the system helping? What must they accomplish? Which facts are authoritative, what could be missing, and what would make the result unacceptable? I define the success contract and a simpler baseline before choosing a model or framework.

### Turn application knowledge into behavior

Application knowledge includes domain meaning, evidence requirements, permissions, valid state transitions, and completion criteria. I make that knowledge operational through retrieval rules, context contracts, tool validation, runtime gates, and evaluation cases. Unresolved assumptions remain visible.

### Allocate judgment and authority

I use deterministic software for properties that can be specified and verified reliably: identities, calculations, permissions, valid state transitions, and effect execution. Models handle interpretation and investigation within explicit boundaries. People retain authority where consequences, accountability, or unresolved uncertainty require their judgment.

### Assemble context for the decision

Retrieval finds candidate evidence; assembly determines what reaches the model. I ask which sources qualify, what must appear together, how contradictions are represented, and whether the evidence is sufficient. Preloaded context, adaptive retrieval, and graph expansion each have conditions under which they help.

### Make execution observable and recoverable

A model proposal crosses explicit boundaries: validated arguments, permission checks, tool execution, observations, artifacts, and state transitions. Completion requires evidence. Missing information, partial failure, interruption, and ambiguous effects need defined recovery or escalation paths.

### Evaluate outcomes and the path taken

I define checks at the relevant granularity: functions, model outputs, nodes, tools, transitions, trajectories, and end-to-end outcomes. Deterministic checks cover exact contracts; semantic assessment needs explicit rubrics and calibration. Traces help locate the first observable broken contract. Controlled interventions test causal explanations.

### Treat latency, cost, and reliability as design constraints

I distinguish time to a useful response from time to verified completion. Model calls, context work, tools, persistence, retries, and review each contribute overhead. I prefer maintained tools where they remove infrastructure work, and assess their setup, runtime, and maintenance costs alongside quality.

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

This is the connection I care about: **what the application knows should determine what it retrieves, allows, verifies, rejects, or asks about.**

## How I test design choices

I compare credible alternatives, make failures visible, and preserve negative results. For controlled studies, I isolate one variable and report limitations. I keep implemented behavior, measured results, and proposed improvements distinct. A useful conclusion explains when a design is appropriate and what evidence would change that choice.

Implementation and investigation: [Causal Desk](https://github.com/Axionis47/causal-inference-agent) · [FinRAG](https://github.com/Axionis47/finsolve-abac-rag) · [AI Engineering First Principles](https://github.com/Axionis47/basis-agent-engineering).

I am currently open to machine-learning and AI-engineering roles.

[Portfolio](https://axionis47.github.io/portfolio/) · [LinkedIn](https://www.linkedin.com/in/siddharth-yalamanchili/) · [Email](mailto:sidsy04@gmail.com)
