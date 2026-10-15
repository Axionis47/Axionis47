# My thinking: optimization

**What we cannot measure, we cannot improve.**

All amounts and schedules below are illustrative accounting assumptions, not measured runs. Metrics remain proxies for useful work.

## Feasible trade-offs

```text
Contract INV-42: verified recommendation; no payment authority
Fast draft: citations unchecked
Verified draft: cited evidence checked against the invoice
```

A fast draft with unchecked citations does not meet this contract, even if its wording is convincing. An exploratory draft could be useful under a different contract, but changing completion criteria would change the comparison. Among verified recommendations, one approach might gather evidence up front while another retrieves missing facts as needed. Quality, authority, and reliability floors determine which designs qualify before cost or speed decides among them.

Within that feasible set, one option may be faster while another needs less review. Pareto intuition means neither improves every relevant dimension; the task determines the compromise. Unsupported acceptances, unauthorized effects, review burden, and recovery outcomes would change feasibility. A pleasant first response cannot substitute for completed work.

## Latency and critical paths

Assume this illustrative schedule, with no queue or review wait:

| Operation | Start to finish |
| --- | --- |
| Retrieve evidence | 0 to 3 seconds |
| Check policy, in parallel | 0 to 2 seconds |
| Draft useful recommendation | 3 to 5 seconds |
| Verify completion | 5 to 6 seconds |

First useful response is at 5 seconds; verified completion is at 6. Summing spans gives 8 seconds and double-counts overlap. Streaming may improve perceived progress; waiting for verification can prevent premature claims. Incorrect early claims or long validation waits would change that choice. [Google's SLO guidance explains user-relevant indicators and latency objectives](https://sre.google/workbook/implementing-slos/). Real reports need p50/p95/p99, sample counts, and exclusions; small samples cannot support credible tail claims.

## Cost per successful task

Assume 12 submitted tasks per design, with 10 accepted under the same contract. Include all attempts on the two unsuccessful tasks:

| Illustrative accounting | A | B |
| --- | --- | --- |
| Calls, including retries | 50 at $0.10 | 12 at $0.40 |
| Retrieval, storage, tools, observability | $3.00 | $1.20 |
| All-attempt cost / accepted tasks | $8/10 = $0.80 | $6/10 = $0.60 |
| Human review across all attempts, separate | 50 minutes | 10 minutes |

Cheaper calls do not guarantee cheaper accepted work. A may still fit a different quality or review constraint; B's apparent benefit disappears if acceptance hides unsupported claims. The accounting must include failed attempts and retries, with human effort separately visible unless explicitly monetized. Receipts, acceptance evidence, and missing charges could reverse the choice. Code saved, setup, debugging, and maintenance require separate effort accounting.

## Controlled measurements

```text
Variable: context grouping only
Workloads: isolated calls vs defined concurrent arrivals
```

To compare context grouping, vary only grouping while fixing cases, information, model, tools, authority, policy, state, effects, graders, settings, and budgets. Isolated serial measurements after preflight and warm-up address one question; defined concurrency/load tests address queueing and contention. Mixing them obscures attribution.

Use the real configured model. Record provider, requested/resolved model, prompt version, and call identity. Label `live`, `cached-live`, `replayed-live`, or `not-a-model`; only live supports model-quality, model-latency, or model-cost conclusions. Cache savings are separate system evidence. Preserve conclusive failures; resume missing/inconclusive cells. Infrastructure failures and watchdog stops are inconclusive. Publish missing, excluded, and inconclusive counts. Execution order, host load, cold starts, residency, grader error, instrumentation, and unobserved provider conditions can revise confidence. Injected slowdowns belong outside normal latency estimates.
