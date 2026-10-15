# My thinking: context management

My central design concern is the evidence available at the moment of judgment. More context helps only when the decision can use it appropriately.

## Evidence selection

Evidence selection starts with the task, access scope, authoritative sources, and required coverage. Retrieval scores identify candidates; they do not establish sufficiency. Fixed bundles, selective hydration, adaptive retrieval, and graph expansion fit different dependency patterns and can be combined. [Anthropic's context engineering discussion](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents) describes finite context and just-in-time approaches. A predictable evidence need may favor preloading; uncertain investigation may favor progressive retrieval. Either can omit decisive evidence or introduce distraction.

## Assembly and dependencies

A context manifest can record source identity, version, selection reason, size, and the decision it supports. Definitions, exceptions, tables, and their notes may need to appear together. Ordering can affect what receives attention. Conflicting evidence should retain provenance and disagreement. The [reporting-period contract](knowledge-contracts.md#requirements-across-boundaries) shows why isolated relevant passages can remain insufficient: entity, period, and source relationships make those passages interpretable. Assembly needs to preserve those relationships without burying the decision in unrelated detail.

## Freshness and compression

Context policy needs to distinguish canonical [state and artifacts](state-recovery.md#truth-and-representations) from a temporary decision view. Rehydration restores detail but adds retrieval cost and may encounter changed sources. Compaction saves space while risking lost exceptions, obligations, or provenance. Summaries need versions and references to recoverable evidence. When testing assembly, the underlying information boundary should remain fixed; otherwise changed source access could be mistaken for improvement from presentation. Freshness requirements depend on the consequences of stale evidence.

## Access and injection

The context boundary needs tenant, owner, purpose, and freshness restrictions before evidence reaches the model. Retrieved documents and tool observations can contain instructions that conflict with the task. Their content remains data, with tool authority enforced independently in [execution contracts](agency-tools.md#authority-and-effects). Privacy extends to logs, memory, and reused summaries. Permission revocation should affect later hydration and reuse. Smaller context can reduce exposure, but completeness and access remain separate obligations.

**What would change the choice:** Missed exceptions favor preserving larger evidence neighborhoods. Distraction, stale reuse, or leakage favor tighter selection and revalidation. Comparable cases and context manifests should establish which change caused the difference before a broader design conclusion follows.
