# council

A skill, not an always-loaded rule. The host loads it only when I ask for a council, or when a project requires one for planning or design work. It is too long, and too expensive to run, for every task.

## What it does

Two investigators from different model families work on the same question in isolation. A coordinator merges their results. Then two reviewers from different families critique the merged result.

- **Isolation is the point.** If the second model reads the first one's answer, you get one opinion twice. Each lineage writes only in its own folder and never opens the other's.
- **Records make decisions auditable.** Requirements, questions, decisions, concerns, evidence and a dated log live in an uncommitted `records/` folder. Every entry has a stable ID. Nothing becomes a decision until I confirm it, and superseded decisions are struck through rather than deleted.
- **The merge keeps disagreement visible.** It lists where the lineages agree, where they differ, questions for me with a recommendation, and defaults to accept as a block.
- **Councils run at set points.** These are the end of a feature, after a scope document is written, between pieces of work, and on final documents.

## Files

| File | Contents |
|---|---|
| [SKILL.md](skills/council/SKILL.md) | The procedure, step by step |
| [references/records.md](skills/council/references/records.md) | The records layout, ID prefixes and example entries |
| [references/briefs.md](skills/council/references/briefs.md) | Brief templates for investigators and council reviewers |

The procedure comes from a planning effort for an operating system project, where two lineages designed the roadmap and two council reviewers checked it between chunks.
