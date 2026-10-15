# My thinking: evaluation and observability

Dependable evaluation needs evidence about outcomes, unsafe paths, and the first observable broken contract. Visibility supports diagnosis; controlled tests support attribution.

## Evaluation units

Checks should match meaningful responsibilities: functions, model outputs, tools, transitions, artifacts, trajectories, and complete tasks. A LangGraph node can represent one operation or several; node granularity changes what a failure label can localize. Splitting nodes improves attribution only when their contracts are meaningful. Dataset and case versions preserve provenance, slices, invariants, and expected evidence. Good component scores cannot substitute for end-to-end success or permission checks along the path. Aggregation should retain critical slices and uncertainty.

## Rubrics and multimodal evidence

Deterministic checks cover exact properties. Semantic assessment needs explicit rubrics, human calibration examples, disagreement review, and checks for judge drift or shared bias. Text, image, audio, and mixed-media tasks require modality-specific evidence: transcription accuracy differs from speaker attribution, and image grounding differs from prose plausibility. [Google's evaluation overview](https://cloud.google.com/vertex-ai/generative-ai/docs/models/evaluation-overview) describes managed evaluation mechanisms. Available metrics still need validation against the task and human judgments. A judge's confidence does not establish rubric validity.

## Tracing and causality

An observable record connects selected context, decisions, tools, artifacts, transitions, and versions. [LangSmith's observability concepts](https://docs.langchain.com/langsmith/observability-concepts) describe nested runs and traces; [OpenTelemetry's signals](https://opentelemetry.io/docs/concepts/signals/) distinguish traces, metrics, and logs. These show temporal order and dependencies. They do not alone prove that an earlier event caused a later failure. Controlled interventions or justified causal assumptions are needed to distinguish a plausible explanation from an established one. Missing spans should remain an evidence gap.

## Regression and rollout

Regression sets preserve consequential failures, including access violations, missing evidence, and recovery errors. CI can gate exact contracts and versioned evaluation thresholds while reporting inconclusive infrastructure cells separately. Staged rollout tests operational assumptions with explicit stop and recovery criteria. Sampling, redaction, retention, and access control protect trace evidence. A passing aggregate should never conceal a failing high-consequence slice or changed grader. Evidence thresholds depend on failure costs and the exposure created by rollout.

**What would change the choice:** Repeated missed faults favor finer observation or stronger evaluation units. Poor human agreement favors revising the rubric before trusting judge scores. Better diagnosis must justify instrumentation, privacy, and review costs, with fault locations established independently of the evaluator under assessment.
