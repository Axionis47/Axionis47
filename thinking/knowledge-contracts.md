# My thinking: knowledge and contracts

My aim is to turn application knowledge into observable behavior. A requirement matters when it changes what the system selects, permits, checks, or asks about.

## Domain meaning

Domain understanding needs entities, relationships, authoritative sources, terminology, and known uncertainty. A document can be authentic yet irrelevant to the requested entity or period. Evidence eligibility needs business meaning as well as search relevance. Assumptions need visible provenance and owners. Missing evidence differs from evidence of absence: an incomplete search should not quietly become a confident conclusion. Domain rules may be stable enough for code, contested enough for review, or dependent on facts that must be refreshed.

## Requirements across boundaries

A reporting-period requirement starts with clarifying fiscal versus calendar periods. Retrieval selects eligible entity, period, and source versions. [Context assembly](context-management.md#assembly-and-dependencies) preserves those identities and exposes conflicts. Acceptance checks verify citations and support for the conclusion. Evaluation includes wrong-period, missing-source, and conflicting-source cases. The trace records the source versions supplied and checks applied. One requirement becomes connected behaviors whose first failure can be located. A gap at any boundary can invalidate an otherwise fluent answer.

## Structural and semantic contracts

Structural checks can reject missing fields, invalid types, or unexpected properties where the interface requires them. [JSON Schema's object reference](https://json-schema.org/understanding-json-schema/reference/object) explains these mechanisms. A valid object still needs semantic checks: whether a source supports its claim, an actor has authority, and a transition is appropriate. Exact rules, evidence review, and calibrated rubrics cover different obligations. Their disagreements should remain observable. Rigid rejection can protect invariants but may need an uncertainty path for valid exceptions.

## Versions and change

Contracts need compatible schema, source, policy, prompt, tool, and grader versions. A policy change can invalidate an answer even when the text and model remain unchanged. Dataset versions preserve case provenance, expected invariants, and intentional changes. Regression cases expose whether an update creates new failures. CI and rollout evidence should connect a change to affected boundaries, with criteria to stop or restore prior behavior. Compatibility depends on meaning as well as shape.

**What would change the choice:** Unsupported acceptances favor stronger evidence checks. Frequent rejection of valid exceptions favors a more explicit review path. Versioned cases should reveal which boundary changed and whether the improvement holds across critical slices.
