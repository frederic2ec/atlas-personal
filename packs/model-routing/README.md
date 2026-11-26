# model-routing

Always-loaded rules for choosing models when an agent delegates work or asks for a review. These are personal because they depend on the subscriptions I pay for. A project can require reviews, independence or more than one model family, but it does not choose my models.

## Order of precedence

1. A model chosen explicitly for the task.
2. This pack.
3. The project's model defaults.

If my models cannot meet a project's review requirement, the agent reports which part went unmet instead of pretending it happened.

## Tiers instead of versions

Rules name tiers (premium, flagship, workhorse, fast) and families, not model IDs. The agent reads the host's live catalog at the start of a task and picks the newest available model in each family. When a new Opus or Sol ships, the rules stay correct without an edit. A model I pin for a task is never upgraded automatically.

## Why the table looks like this

- **Opus is strong, but costly with tight limits.** It finishes and reviews work. Long feature work goes to Sol, the cost-efficient workhorse, when the host can reach both providers.
- **Two final reviews come from different families.** The point is independence: a reviewer from the family that wrote the code is more likely to share its assumptions.
- **Haiku never does technical work, even through a host's built-in helper agents.** Some hosts route helpers to Haiku by default, so the rule names that route explicitly.
- **Premium models only on request.** They cost much more than the workhorse for most tasks.

## Running children

- The agent checks which provider, model and options each child actually ran with. Some host helpers ignore model settings silently.
- A rate limit never blocks progress. Work continues on an allowed model, and the deferred review is reported rather than skipped silently.
- The T3 Code notes cover host behavior that caused duplicate runs. A rate-limited run resumes on its own, so relaunching it creates a second run.
