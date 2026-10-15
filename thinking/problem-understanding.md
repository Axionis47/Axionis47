# My thinking: problem understanding

My starting question is whether the proposed system addresses the work people actually need to complete. Architecture becomes meaningful only after that understanding is explicit.

## People and workflow

Understanding the workflow starts with who requests work, who supplies evidence, who decides, and who bears the consequences. A workflow includes handoffs, waiting, exceptions, and informal workarounds. One real case can reveal that the bottleneck is missing information or unclear ownership. If people cannot inspect, correct, and continue the work, faster generation may add little value. The useful intervention might be better intake, evidence organization, decision support, or delegated execution, depending on where the work breaks.

## Causes and assumptions

A useful problem statement separates observed symptoms from explanations. Slow review might reflect scattered evidence, conflicting policies, or unnecessary approval. Each explanation suggests different interventions. Assumptions need owners, confidence, and a way to disprove them. Temporal order can guide investigation, but a sequence of events does not establish why an outcome occurred. Competing explanations should remain visible before an architecture hardens around a preferred story.

## Completion and failure costs

A success contract should specify the useful outcome, required evidence, unacceptable actions, and unresolved conditions that require abstention or human judgment. Failure costs include missed issues, false alarms, delay, privacy loss, and recovery effort. Non-goals prevent a narrow assistant from silently becoming an authorized operator. Wording and investigation paths may vary while entity identity, access scope, and support for conclusions remain invariant. Higher consequences can justify stronger checks, slower completion, or narrower authority.

## Baselines and feasibility

The baseline could be the current human workflow, a search interface, deterministic automation, or a bounded model workflow. Simpler options establish what additional agency must earn. [Anthropic's workflow and agent distinction](https://www.anthropic.com/engineering/building-effective-agents) helps compare prescribed paths with model-directed execution. A combination of software, judgment, and review might make a previously impractical task feasible, but that opportunity needs evidence about quality, effort, and consequences under real constraints.

**What would change the choice:** Case evidence showing that improved intake removes the ambiguity would favor workflow changes. Persistent ambiguity with useful, supported model decisions could justify bounded judgment. Comparisons need fixed success criteria and visible failures, not only persuasive examples.
