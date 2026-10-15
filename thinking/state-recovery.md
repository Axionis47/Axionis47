# My thinking: state and recovery

Long-running work raises a practical question: what remains true when execution stops, sources change, or a new process resumes the task?

## Truth and representations

Canonical state records durable workflow position, facts, obligations, and versions. Model context is a temporary selection for one decision. Memory is retained knowledge with explicit read, write, provenance, and deletion policies. Artifacts hold independently versioned work and evidence, with identity, checksum, owner, lineage, and validation status. Events record what happened. Caches and search indexes are derived views unless deliberately assigned stronger semantics. These distinctions prevent a convenient summary from silently becoming authoritative truth, while allowing several representations of the same evidence.

## Checkpoint boundaries

Checkpoint placement follows the cost and consequences of losing progress. Validated expensive work, entry to human review, and protected effects are candidate boundaries. A checkpoint needs position, obligations, artifact references, approval and retry status, and relevant versions. [LangGraph persistence documentation](https://docs.langchain.com/oss/python/langgraph/persistence) describes thread-scoped checkpoints as one available mechanism. The application still needs an explanation of what can safely resume and what must be revalidated. More frequent checkpoints reduce some recomputation while increasing coordination and storage work.

## Effects and recovery

An external effect may succeed before its completion record commits. Blind retry can duplicate the effect; blindly accepting success can lose unfinished work. An intent record, stable idempotency identity, external receipt, and reconciliation can resolve uncertainty where the external system supports them. Compensation may help when reversal is possible. Some effects need human review because neither retry nor compensation establishes a safe outcome. Recovery must expose uncertainty and retain the pending obligation instead of manufacturing success.

## Concurrency and evolution

Ownership defines who may mutate each field and how stale writers are detected. Duplicate delivery, cancellation, revoked permissions, expired artifacts, and schema changes challenge resume semantics. Version checks or leases protect different boundaries with different coordination costs. Replaying decisions under changed sources or prompts is a new computation unless original inputs and execution semantics are preserved. [Context hydration](context-management.md#freshness-and-compression) must respect that distinction. Retention and deletion policies also need to reach derived representations and recovery copies.

**What would change the choice:** Costly recomputation favors additional checkpoints. Coordination failures favor simpler ownership or fewer shared writes. A crash at an effect boundary can require revising the effect protocol before checkpoint frequency is meaningfully comparable. Recovery evidence should cover both sides of each consequential boundary.
