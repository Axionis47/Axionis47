# My thinking: evaluation and observability

A fluent answer can conceal an early contract failure. The revenue trace and multimodal cases below are constructed illustrations, not model outputs, evaluator scores, or measured runs.

## Evaluation units

```text
Task REV-42: Q3 requested; selected source S-Q2-v1
One node: retrieve + assemble + answer + validate
```

Retrieval eligibility fails first in this fixture; acceptance later fails to catch it. Those are distinct contracts even when one final score says “wrong.” One LangGraph node could own all four operations; separate nodes could expose meaningful contracts at each transition. A single node with internal tool spans can preserve operational detail without turning every function into a workflow boundary. The choice depends on independent retries, ownership, and the failure question.

Node-level success can hide a bad retrieval; excessive splitting can add state and coordination overhead. Versioned datasets and cases need entity, quarter, source eligibility, and critical slices. Fault-localization accuracy, missing observations, retry behavior, and end-to-end acceptance would show whether finer granularity helps. Good local checks cannot establish that the entire path respected permissions.

## Rubrics and multimodal evidence

```text
Image INV-42: total legible; vendor stamp ambiguous
Audio A42: words clear; speaker identity disputed
```

An image invoice has a legible total but an ambiguous vendor stamp. Exact amount matching can check extraction; a human-calibrated rubric can assess whether vendor identity is supported. In audio, correct words do not guarantee correct speaker attribution. A model judge may favor a plausible description while humans mark the identity uncertain.

[Google's evaluation overview describes managed evaluation mechanisms](https://cloud.google.com/vertex-ai/generative-ai/docs/models/evaluation-overview), not validation of a task-specific rubric. Human review and model judging can complement each other, but shared bias or unclear criteria can make both wrong. Source-region references, calibration labels, disagreement by slice, and grader versions would indicate whether to revise the rubric before trusting aggregate scores.

## Tracing and causality

```text
LangGraph node N1: 0 to 6 seconds (inclusive)
Child tools: retrieve 0 to 2; validate 4 to 6
```

Adding child-span durations to N1's inclusive duration double-counts time. Instrumenting those spans is useful for locating work inside the node. Boundary records answer a different question:

| Stage | Observable evidence |
| --- | --- |
| Retrieve | Q3 requested; Q2-only source selected |
| Assemble | Q2 metadata retained |
| Answer | Plausible Q3 claim cites that source |
| Validate | Shape passes; period check absent |

Outcome-only review finds the wrong answer; boundary evidence localizes retrieval eligibility. [LangSmith explains nested runs and trace granularity](https://docs.langchain.com/langsmith/observability-concepts); [OpenTelemetry distinguishes traces, metrics, and logs](https://opentelemetry.io/docs/concepts/signals/). Temporal order does not prove retrieval caused every later error. Controlled source replacement could test that explanation; missing spans would weaken it. The aim is observable rationale, not hidden chain-of-thought.

## Regression and rollout

```text
Release R8: aggregate acceptance rises
Critical slice: tenant A answer cites tenant B source
```

A new release improves most revenue cases but exposes another tenant's source in one answer. An overall acceptance threshold can track broad change; a separate access invariant should block that release regardless of the average. CI can preserve the leaking case and contract check. Staged rollout can reveal workload and operational failures absent from the dataset.

CI success is bounded by coverage; a quiet rollout can reflect limited exposure. Versioned critical-slice results, access-denial evidence, observed workload, rollback readiness, and reported missing or inconclusive cells would change confidence. Trace redaction, access, retention, and deletion also need checks, since diagnostic evidence can itself leak sensitive information.
