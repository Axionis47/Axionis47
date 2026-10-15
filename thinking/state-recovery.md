# My thinking: state and recovery

A checkpoint can preserve workflow position while leaving an external effect uncertain. The invoice sequence below is constructed and illustrative, not an executed recovery test.

## Truth and representations

```text
run R42: status=awaiting approval; pending=pay INV-42
artifact E42-v1: evidence bundle; context C42: selected excerpts
```

An invoice workflow has a recommendation, a pending payment, and supplier evidence. Canonical state can own status, approval identity, and pending obligations. An artifact can hold the evidence bundle with checksum, owner, version, and lineage. Model context can select relevant excerpts; memory may retain permitted cross-run knowledge under a separate policy.

Embedding everything in one durable record simplifies retrieval for small work. Referencing versioned artifacts supports larger evidence and independent lifecycle controls. Neither approach makes a prompt summary authoritative. Missing artifacts, state growth, conflicting versions, and inability to explain a status change would favor a different representation. Search indexes and caches remain derived unless deliberately given stronger semantics.

## Checkpoint boundaries

```text
R42: evidence E42-v1 validated -> approval wait
Checkpoint candidate: proposal, artifact ref, policy P7-v3
```

Suppose evidence assembly is expensive and human approval takes hours. Checkpointing after validated assembly avoids repeating work; checkpointing every mechanical step may save little while increasing write and migration overhead. Checkpointing at approval entry preserves the pending obligation and the exact proposal under review.

[LangGraph documents thread-scoped checkpoints and resume mechanisms](https://docs.langchain.com/oss/python/langgraph/persistence). Those mechanisms do not make an external payment atomic with the checkpoint. Lost work, artifact integrity, approval reconstruction, and persistence overhead would inform placement. If resumed work silently uses a newer policy, an intact checkpoint can still produce the wrong continuation. Resume contracts need versions and revalidation rules, not only a saved position.

## Effects and recovery

Consider this illustrative event sequence:

| Event | Observable record |
| --- | --- |
| Save intent | key `pay-INV42-v1`, status `pending` |
| External write succeeds | receipt `R-731` under that key |
| Process crashes | saved receipt still absent |

Retrying with the same key can be safe when the provider guarantees its idempotency semantics. Reconciling by key or receipt is useful when status can be queried. Escalation is necessary when neither proves what happened. Blind retry can duplicate payment; assuming success can lose unfinished work. A checkpoint alone guarantees neither atomic effect commit nor exactly-once execution. Provider records, duplicate counts, and resolved pending obligations would determine whether recovery is trustworthy.

## Concurrency and evolution

```text
R42 state version=8; workers W1/W2 both read 8
Cancel arrives; policy P7-v3 -> P7-v4
```

Two workers resume INV-42 while cancellation arrives and policy v4 replaces v3. Optimistic version checks can reject stale commits; a lease can reduce simultaneous execution when its expiry and ownership semantics fit. Cancellation before commitment can block the effect; cancellation after commitment may require compensation or human handling.

A lease expiring during execution can allow overlap. A version conflict detected after payment cannot undo it. State versions, cancellation timestamps, external receipts, and permission decisions reveal the boundary actually protected. Refreshing [decision context](context-management.md#freshness-and-compression) may be needed under changed policy, while retaining historical evidence for the original decision. Frequent conflicts or unclear compensation would favor narrower ownership or stronger effect coordination.
