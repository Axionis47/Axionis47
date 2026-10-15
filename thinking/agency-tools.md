# My thinking: agency and tools

Tool design asks where semantic choice should meet reliable mechanics. The boundary determines what the model can decide and what software must guarantee.

## Decision allocation

Allocation starts with consequences, ambiguity, and accountability. Interpretation and investigation may benefit from model judgment. Calculations, identities, permissions, and transition rules need enforceable software boundaries. Humans may own disputed assumptions or consequential commitments. Prescribed workflows and model-directed loops can also be combined, as illustrated in [Anthropic's agent guidance](https://www.anthropic.com/engineering/building-effective-agents). Additional autonomy needs evidence of useful flexibility and acceptable failure costs. Good outcomes alone cannot justify authority that was never granted.

## Tool abstraction

Mechanical primitives, semantic operations, and broader workflow tools expose different choices. Primitives offer flexibility but increase planning and calls. Semantic tools can combine predictable joins, validation, or formatting while retaining meaningful decisions. Workflow tools may reduce effort on familiar cases yet conceal partial progress or struggle with exceptions. These are points along several design axes, not exhaustive categories. Each boundary needs explicit inputs, observations, errors, and retry semantics. Transport and discovery do not determine whether the abstraction is appropriate.

## Authority and effects

A tool contract identifies actor, capability scope, allowed resources, preconditions, and effect. Preview and commit can separate inspection from authorization. Approval may bind intent, a plan, exact arguments, or an effect; those are different controls. Tool observations remain untrusted data, especially when they contain injected instructions. Software enforces permissions independently of model compliance. Idempotency, receipts, verification, and [recovery semantics](state-recovery.md#effects-and-recovery) make ambiguous writes inspectable. Sensitive arguments and observations also need privacy controls.

## Engineering effort

Adoption should count infrastructure code avoided, development time saved, and operational support gained. Setup, integration, runtime overhead, debugging, upgrades, and maintenance can offset those savings. A maintained tool can be valuable without improving model quality. Its abstractions still need to preserve evaluation visibility. Cloud Gemini through Vertex AI with existing Application Default Credentials is one implementation option, subject to the task's access and service requirements. Infrastructure selection follows the contract rather than determining it.

**What would change the choice:** Repeated mechanical mistakes favor stronger semantic operations. Valid exceptions hidden by a broad tool favor exposing narrower decisions. Selection needs evidence across representative and consequential cases; a single polished path can justify exploration, not broad delegation.
