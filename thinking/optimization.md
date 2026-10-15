# My thinking: optimization

**What we cannot measure, we cannot improve.**

Useful optimization can make previously impractical work feasible. That possibility depends on meeting real constraints, not improving one metric in isolation.

## Feasible trade-offs

Quality, authority, and reliability floors come first. Faster unsafe work does not qualify. Among feasible designs, some improve one objective only by worsening another. This is the practical Pareto intuition: several choices may be defensible. Task urgency, failure costs, review capacity, and resource limits determine which compromise is useful. Feasibility can change as models and tools improve; the dimensions and their acceptable ranges need revisiting when the task changes.

## Latency and critical paths

Latency records separate first useful response from verified completion, with p50, p95, and p99, sample counts, and excluded cells. [Google's SLO guidance](https://sre.google/workbook/implementing-slos/) connects service indicators and targets to user experience. Separate model, retrieval, tool, queue, persistence, validation, and review time. Use the critical path to explain elapsed time; summing overlapping spans overstates duration. Small samples provide weak evidence about tails. Deliberately injected slowdowns belong in recovery evidence, outside normal latency estimates.

## Cost per successful task

The denominator is successful tasks under the declared contract. The numerator includes failed attempts, retries, retrieval, storage, and observability, alongside model and tool charges. Human review stays separately recorded unless explicitly monetized with stated assumptions. Infrastructure code and development time saved need separate accounting alongside setup, runtime, and maintenance. Cache hits can improve system economics without demonstrating cheaper or faster live model behavior. Claims need an accounting boundary, observation period, and missing-data disclosure.

## Controlled measurements

For a controlled comparison, declare one variable and fix other relevant boundaries, inference settings, and budgets. Use the real configured model. Record provider, requested and resolved model, prompt version, and call identity; label `live`, `cached-live`, `replayed-live`, or `not-a-model`. Only live supports model-quality, model-latency, or model-cost conclusions. Preserve conclusive failures; resume only missing or inconclusive cells. Infrastructure failures remain inconclusive. Publish missing, excluded, and inconclusive counts. Isolated call comparisons need controlled load and separate warm and cold samples. Concurrency, queueing, and production-load tests need their own workload definitions. Discuss execution order, host load, cold starts, model residency where relevant, grader error, and instrumentation overhead. Disclose provider-side conditions that cannot be observed. Watchdogs cannot become behavioral failure criteria.

**What would change the choice:** A cheaper design losing its quality floor is no longer feasible. Tail delays, failed attempts, review burden, or uncertain measurements can reverse an apparent advantage. Selection needs representative evidence; revision should distinguish changed conditions from random variation. No measurements were run for these notes.
