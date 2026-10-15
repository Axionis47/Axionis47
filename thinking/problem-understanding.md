# My thinking: problem understanding

A request to automate can hide several different problems. The invoice case below is constructed and illustrative, not a measured run; the causal example is separately attributed.

## People and workflow

```text
INV-42: queue age=3 days; purchase order=missing; review=not started
```

An invoice reviewer waits days because a purchase order is missing. Faster classification helps only after the evidence arrives. Better intake could require the order reference before submission; an evidence-gathering assistant could search authorized records when suppliers cannot provide it. Automating the decision fits a different bottleneck: complete cases waiting for judgment.

| Observed situation | Candidate intervention |
| --- | --- |
| Missing order reference | Improve intake or gather evidence |
| Complete evidence, unresolved dispute | Support review or bounded judgment |

Mandatory intake can block legitimate exceptions; autonomous search can find the wrong entity's order. Handoff timestamps, missing-field reasons, and corrected matches would show which explanation survives. A queue-time average alone cannot choose the intervention.

## Causes and assumptions

```text
Question: course attendance -> math score?
Observed: attendees score higher; assignment process=unknown
```

Suppose students who attended a preparation course have higher math scores. Stronger students may self-select, making prior ability a competing explanation. Comparing averages describes an association; adjustment may help estimate an effect only when the assignment process and confounders are understood. Random assignment, if feasible, supports a different identification strategy. Neither an attractive chart nor a more capable agent supplies missing causal assumptions.

[Causal Desk's documented course example](https://github.com/Axionis47/causal-inference-agent#see-it) asks who assigned attendance, records sourced claims, waits for confirmation, then performs DoWhy adjustment and produces artifacts. That is a project-described workflow, not evidence here that adjustment identifies the effect. Assignment records, covariate provenance, and sensitivity to plausible confounding would change the justified conclusion.

## Completion and failure costs

```text
INV-42 deliverable: supported recommendation
Payment permission: absent
```

For the invoice, “resolve the case” could mean a supported recommendation or an authorized payment. A recommendation can preserve human commitment when evidence is disputed. Automated payment may suit low-risk, well-specified cases with enforceable authority and independent verification. Those are different success contracts, not merely different interface wording.

A recommendation can still mislead if uncertainty disappears; a correct amount can still be an unauthorized effect. Accepted recommendations, reviewer corrections, payment permissions, and external receipts expose different obligations. A confirmed authority breach can require narrowing scope even when completion rates look favorable. Human review also needs enough source evidence to be meaningful.

## Baselines and feasibility

```text
12 illustrative invoice cases: 8 lack order references
Candidate change: require reference at intake
```

If missing order references dominate, improved intake is a credible baseline. If reviewers instead spend most effort locating documents, search and a checklist may solve enough of the problem. If exceptions require unpredictable investigation, a bounded model-directed workflow may earn its additional complexity. [Anthropic's distinction between prescribed workflows and agents](https://www.anthropic.com/engineering/building-effective-agents) provides vocabulary for those choices, which can also be combined.

Sustained evidence gathering might make previously impractical reviews feasible. It could equally create a larger backlog of recommendations that nobody can verify. Comparable cases, accepted outcomes, review effort, failure costs, and recovery evidence would establish whether the opportunity is real. A successful demonstration supports further consideration; broader authority needs evidence across representative and consequential exceptions.
