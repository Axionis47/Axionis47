# My engineering reasoning notes

My approach begins with the problem and follows its requirements through context, decisions, execution, and evidence. These notes extend the [thinking patterns in my profile](../README.md). They describe public design rationale and open questions. The examples are illustrative and composable, with no claim to know every alternative or to have measured these choices.

| Reasoning area | Question shaping the design |
| --- | --- |
| [Problem understanding](problem-understanding.md) | What outcome matters, and what would establish improvement? |
| [Knowledge and contracts](knowledge-contracts.md) | How does application knowledge change behavior? |
| [Context management](context-management.md) | What should each decision know, and under whose authority? |
| [Agency and tools](agency-tools.md) | Where should judgment and reliable mechanics meet? |
| [State and recovery](state-recovery.md) | What remains true after interruption or change? |
| [Evaluation and observability](evaluation-observability.md) | What failed first, and how strong is the evidence? |
| [Optimization](optimization.md) | Which feasible design makes useful trade-offs for this task? |

## Documentation and source policy

Checked: **2026-10-15**. First-principles synthesis expresses my working understanding; linked primary documentation supports specific mechanisms. Sources are further reading, not evidence of my own results. Examples illustrate choices that may be combined or replaced. Each choice remains revisable by contrary evidence. These are lightweight notes, not product implementations. No experiments or model calls were run for these documents.

Any supporting result should version the task, cases and dataset, model, prompt, context, tools, policy, and grader. Record observable decisions, evidence, permissions, effects, and checks. Keep hidden chain-of-thought, secrets, and gold labels out of runtime context. Separate trusted instructions from untrusted source content, and preserve access boundaries when retrieving, persisting, or displaying evidence.

Model outputs must identify `live`, `cached-live`, `replayed-live`, or `not-a-model`, plus provider, requested model, resolved version when available, prompt version, and call identity. Only live calls support model-quality, model-latency, or model-cost conclusions. Cache benefits require separate system measurements. Software-mechanics tests cannot stand in for model evidence.

Comparisons should declare one independent variable, preserve conclusive failures, mark infrastructure failures inconclusive, and show missing, excluded, and inconclusive counts. The [optimization note](optimization.md#controlled-measurements) expands these evidence boundaries.

Choosing a bounded, reversible design may need less evidence than granting consequential authority. Revision also depends on the signal: one confirmed access violation can outweigh a favorable average, while a small latency difference may need repeated observations. Confidence, exposure, failure costs, and recovery options shape the threshold; no single score settles every choice.
