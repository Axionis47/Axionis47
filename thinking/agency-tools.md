# My thinking: agency and tools

A disputed invoice needs judgment, evidence, and bounded effects. The case below is constructed and illustrative, not a model run or a measured tool comparison.

## Decision allocation

```text
INV-42: supplier claims emergency exception
Order PO-17: exception flag absent; payment authority=reviewer
```

A supplier says the invoice matches an emergency order; the purchase-order system disagrees. A prescribed workflow can gather defined records and route the dispute. Model-directed investigation may help when evidence locations or terminology vary. Human judgment may remain necessary when the exception is contested or payment authority is restricted. [Anthropic's workflow and agent distinction explains these execution choices](https://www.anthropic.com/engineering/building-effective-agents), which can be combined within one task.

Rigid routing can miss a valid exception; open-ended investigation can exceed scope. Source-backed recommendations, missed exceptions, unauthorized attempts, and reviewer corrections would establish where flexibility earns its cost. A correct recommendation does not grant authority to execute it.

## Tool abstraction

For the same dispute, several boundaries are plausible:

| Illustrative interface | Useful when | Catch |
| --- | --- | --- |
| Search, fetch, compare primitives | Investigation needs unusual combinations | Mechanical mistakes and many calls |
| Build invoice-evidence bundle | Joins and checks are predictable | Bundle may omit novel evidence |
| Resolve invoice workflow | Cases and allowed transitions are stable | Hidden decisions or partial progress |

These are examples along several axes, not fixed categories. The bundle can expose evidence while leaving judgment outside; the workflow can offer an escape hatch. Incorrect joins, invalid arguments, excluded exceptions, and visible partial results would show whether the boundary is too narrow or too broad. Transport standardization does not settle that question.

## Authority and effects

```text
Preview: INV-42, 1200 units, payee A, policy P7-v3
Commit request: same invoice, payee B
```

The reviewer previews payment of invoice INV-42 under policy v3. Approval bound to those exact arguments can prevent later substitution of a different amount or payee. Intent-level approval is less burdensome when a trusted executor can constrain all subsequent details. The binding should match the consequence and accountability required.

Changed arguments after approval create an authority breach. Tool observations may also contain injected payment instructions; permissions must survive model compliance failures. Argument fingerprints, actor scope, permission results, and receipts expose the effect actually authorized. A timeout after partial execution needs [reconciliation rather than blind retry](state-recovery.md#effects-and-recovery), even when the preview was correct.

## Engineering effort

```text
Integration ledger: handwritten lines; setup steps; debug hours
Also record: export failures, upgrades, runtime overhead
```

A maintained integration could replace custom authentication, pagination, and export handling. A small direct adapter may fit when the existing integration adds complex setup or hides receipts. Count handwritten code avoided, setup steps, debugging hours, export failures, upgrades, runtime overhead, and ownership over the same observation period. Fewer lines alone do not establish lower total effort; no speedup is assumed here.

Concrete integration records would change the adoption choice. Cloud Gemini through Vertex AI with existing Application Default Credentials is an implementation option for real model calls if access and service requirements fit. Infrastructure choice should support the task's contracts, including observability and recovery, rather than determine the authority granted.
