# My engineering reasoning notes

Concrete cases make the trade-offs easier to inspect. These notes extend [my profile](../README.md) through situations where a plausible design can fail and evidence can change the choice. The alternatives are illustrative and composable, not exhaustive.

| Start with a case | Follow the decision |
| --- | --- |
| [Invoices wait days for a purchase order](problem-understanding.md#people-and-workflow) | Faster decisions, better intake, or evidence gathering? |
| [A convincing revenue citation names the wrong quarter](knowledge-contracts.md#requirements-across-boundaries) | Where should the requirement reject the answer? |
| [A policy footnote reverses the main rule](context-management.md#evidence-selection) | Preload the evidence, retrieve adaptively, or expand relationships? |
| [A disputed invoice needs tools and bounded authority](agency-tools.md#tool-abstraction) | Primitives, an evidence bundle, or a resolution workflow? |
| [A write succeeds before the process crashes](state-recovery.md#effects-and-recovery) | Retry, reconcile, or escalate? |
| [A polished answer hides the first wrong-source decision](evaluation-observability.md#tracing-and-causality) | Which observation actually localizes the failure? |
| [Cheaper calls create more retries and review](optimization.md#cost-per-successful-task) | Which accounting boundary changes the apparent winner? |

<details>
<summary>Sources, examples, and evidence policy</summary>

Checked: **2026-10-15**. Constructed cases, amounts, and event sequences are labelled illustrative, not measured runs. Project reports are attributed separately. Official links explain specific mechanisms, not proof of my results. No experiments or model calls were run for these notes.

Supporting evidence needs task, dataset/case, model, prompt, context, tool, policy, and grader versions. Keep observable decisions and source provenance, not hidden chain-of-thought, secrets, or gold labels in runtime context. Preserve access, privacy, retention, and deletion boundaries across derived copies.

A controlled comparison declares one independent variable, preserves conclusive failures, and reports missing, excluded, and inconclusive cells. Infrastructure failures remain inconclusive. Record model provenance as `live`, `cached-live`, `replayed-live`, or `not-a-model`; only live supports model-quality, model-latency, and model-cost conclusions. Cache benefits are separate system evidence.

Consequential authority needs stronger evidence than reversible assistance. One confirmed access violation can outweigh a favorable average; a small latency difference may need repeated observations. Choices remain revisable as conditions and evidence change.

</details>
