# Records for a council effort

Keep these files in an uncommitted `records/` folder. Exclude it through `.git/info/exclude` so the project's `.gitignore` stays untouched.

| File or folder | Holds | Id prefix |
|---|---|---|
| `requirements.md` | The user's request, verbatim and itemized | `R-` |
| `questions.md` | Open and answered questions for the user | `Q-` |
| `decisions.md` | Decisions taken, by whom, why and when | `D-` |
| `concerns.md` | Contradictions, risks and anything that needs a ruling | `C-` |
| `evidence.md` | Facts established from code, docs or sources, with where | `E-` |
| `chunks.md` | The work plan split into chunks, and each chunk's status | `K-` |
| `log.md` | A dated journal of what happened | dated |
| `agents/<lineage>/` | One work folder per model lineage. Only that lineage reads it. | |
| `shared/` | Material the coordinator cleared for both lineages | |
| `synthesis/` | The coordinator's merge per chunk | |
| `council/` | Council reviews per chunk and lineage | |

## Rules

- Every entry has a stable id so other documents can cite it.
- Nothing is a decision until the user confirms it, unless the user delegated it.
- A statement without evidence is marked `unverified`.
- Append answers and decisions. Strike through superseded entries and point to their replacement. Never delete one.
- Planning documents mark every statement as done (with evidence), planned (citing a decision) or proposed. Give no dates or durations as facts. Sizes are relative estimates.

## Example entries

```markdown
- **D-016** Council cadence: review at the end of a feature, after a scope document, between pieces of work, and on the final documents. (user, 2026-10-31)
- ~~**D-009** 1.0 matches the reference's app compatibility.~~ Replaced by D-018. (user, 2026-10-31)
- **E-012** Both delegate models are available: `gpt-6.1-sol`, `claude-opus-5-5` (host catalog, 2026-10-31).
```
