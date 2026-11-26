---
name: council
description: Run the council procedure when the user requests it or the project requires it. Two independent model families work in isolation, the coordinator merges the work, and reviewers check the result.
---

# Council

A council gets independent, evidence-backed opinions from two model families and merges them without letting either one anchor the other. The value is independence. Every step protects it.

## 1. Set up records before investigating

Create an uncommitted `records/` folder in the project. Keep it out of Git with `.git/info/exclude`, not `.gitignore`. Follow [records.md](references/records.md): requirements, questions, decisions, concerns, evidence, chunks and a dated log, plus `agents/<lineage>/`, `synthesis/`, `council/` and `shared/`.

- Copy the user's request verbatim into `requirements.md`, itemized.
- Nothing becomes a decision until the user confirms it, unless they delegated it. Read back any interpretation first.
- Append answers and decisions. Strike through superseded entries and point to their replacement. Never delete one.

## 2. Ask before launching

Log concerns and contradictions, and ask the blocking questions. Split the work into chunks and get the plan approved. Launch no agent until the user answers the blocking questions. Independent chunks may run in parallel. The user reviews each merge before the next dependent chunk starts.

## 3. Brief two lineages

- Two lineages per chunk, from different model families, both at high effort. Check that both models are available first, and verify which models actually ran.
- Prepend the common rules in [briefs.md](references/briefs.md) to every chunk brief. Each brief gives the background, the decisions to respect (later decisions supersede earlier ones), the deliverables and a read-first list.
- Each lineage writes only in `records/agents/<lineage>/<chunk>/`. It never opens the other lineage's folder, `synthesis/` or `council/`. Isolation depends on instructions, so state it plainly in every brief.
- Investigators do not write code, change the repository or run git commands that change state. They ask nothing mid-task. Questions go into their `questions.md`.

## 4. Merge

Write `synthesis/<chunk>.md` in this order:
1. Inputs, and what you read in full versus did not re-verify.
2. Where both lineages agree.
3. Where they differ.
4. Questions for the user, with recommendations in bold.
5. Technical defaults to accept as a block.
6. Deferred items.
7. Items for the coordinator, not the user.

Clear material into `shared/` before a later chunk may use it.

## 5. Present

Re-ask every open question in full with its options and a recommendation. Record answers as decisions with who decided and why.

## 6. Council review

- **Cadence.** Review at the end of a feature, after a scope document is written, between pieces of work, and on the final documents.
- **Brief.** Use the reviewer brief in [briefs.md](references/briefs.md). Show it to the user before launching.
- **Reviewers.** Two, from different families, at high effort. Each writes only in `council/<chunk>/<lineage>/`, never opens the other's folder, and may read everything else.
- **Findings.** Each review gives a summary of 10 to 20 lines, then findings. Each finding has an id, a severity (`blocker`, `major`, `minor` or `suggestion`), its evidence and a concrete recommendation. Findings that need the user's judgment are marked. Reviewers do not reopen a decision only to restate the alternative.
- **Council merge.** Write a verdict and a table of the findings that need the user: topic, reviewer A, reviewer B, your recommendation. Add the refinements accepted without reversing a decision. The user accepts them by recording a decision.

## 7. Finalize

Update the documents, run the council, apply the findings and run the council again. Commit only with authorization. Ask the user about changes that need their judgment before applying them.

## Rate limits and stand-ins

Do not relaunch a rate-limited run that the host resumes on its own. A stand-in model for a lineage needs the user's choice, labels every file it writes, and triggers a cross-check later.

## Single merge agent

When the user has chosen between drafts, one merge agent may read both lineages. It takes a base draft plus a second source, changes no decision, and lists every choice it made, preferring the option that needs less rework.
