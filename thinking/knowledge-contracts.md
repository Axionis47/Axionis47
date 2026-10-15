# My thinking: knowledge and contracts

A correct-looking answer can violate the task before its wording is assessed. The revenue case and metadata below are illustrative, not measured outputs or a model run.

## Domain meaning

```text
Request: North Division, Q3 revenue
Unresolved: fiscal Q3 or calendar Q3? Source S-18: fiscal Q2
```

A user asks for “North Division's Q3 revenue.” The company reports fiscal quarters, while the user may mean calendar quarters. Clarifying the period is useful when the distinction changes the answer. Applying a documented fiscal default can be reasonable in a recurring internal workflow if the assumption remains visible. Both choices need an authoritative entity mapping: a subsidiary with a similar name is not interchangeable.

Clarification adds delay; a silent default creates confident wrong-period answers. User corrections, conflicting period references, and source metadata would determine whether the default remains defensible. Once Q3 is fixed, S-18 cannot support it. Frequent ambiguity favors earlier clarification.

## Requirements across boundaries

Consider the following constructed mismatch:

| Field | Requested | Retrieved source |
| --- | --- | --- |
| Entity | North Division | North Holdings |
| Period basis | Fiscal | Calendar |
| Quarter | Q3 | Q2 |

Filtering before retrieval can prevent ineligible sources from entering the candidate set. A downstream acceptance check can independently reject a mismatched citation when metadata is unreliable or retrieval is broader. These controls can be combined. Early filtering can exclude a useful consolidated report; late rejection wastes work and may fail if identity was discarded during [context assembly](context-management.md#assembly-and-dependencies). Candidate identities, assembly manifests, and validation reasons reveal the first broken boundary. High semantic similarity cannot repair the mismatch.

## Structural and semantic contracts

```text
Record fields present: entity, quarter, amount, citation
Citation S-18: table covers a different entity
```

A revenue record might contain all required fields: entity, period, amount, and citation. Strict schema validation is useful for reliable parsing; evidence validation is needed to establish that the cited passage actually supports the amount and period. [JSON Schema's object rules explain required fields and additional properties](https://json-schema.org/understanding-json-schema/reference/object), not whether a financial claim is true.

A structurally valid citation can point to an unrelated table. Exact metadata checks may reject that case; a calibrated semantic review may be needed when supporting notes use different terminology. Valid exceptions, unsupported acceptances, and reviewer disagreement would show where either check is too rigid or too permissive. A single “valid” flag would conceal the distinction.

## Versions and change

```text
Approval PAY-v3: reviewer allowed -> PAY-v4: supervisor required
Schema v2: amount -> schema v3: payable_amount
```

INV-42 was approved under PAY-v3, but PAY-v4 now requires a supervisor. Pinning versions explains the historical approval; revalidating authority protects a new commitment. A schema migration may also rename the amount field. The choice depends on whether the task asks what was authorized then or what may proceed now.

Shape-compatible records can still carry obsolete meaning; aggressive migration can erase historical interpretation. Versioned cases should include both policies and intentional expected changes. Contract checks in CI, affected-case results, and staged-rollout corrections would indicate whether migration is safe. A changed grader must remain visible so a better score cannot disguise a shifted definition of success.
