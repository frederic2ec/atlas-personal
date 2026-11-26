# personal-workflow

Always-loaded rules for how agents work with me, in any project. Each rule came from a real correction. The notes below say what went wrong without it.

## Talking with me

| Rule | Why it exists |
|---|---|
| Put decisions and drafts in the conversation, not in files I must open | I asked agents to go over decisions with me directly, so I can answer without switching to another file. |
| End each message with every open question in full, with options and a recommendation | Questions asked mid-conversation, or while a background agent ran, were invisible unless I scrolled back. A pointer such as "still open from earlier" is effectively no question. |
| Read back an interpretation before acting on it | An agent once recorded "1.0 follows the reference project's scope" as literal feature parity. I meant something much smaller. Confirming first is cheaper than undoing a plan. |
| Do not re-ask settled decisions, and do not keep listing deferred items | Settled decisions kept coming back in status reports and "what next" menus. "For now" means raise it again only when its conditions change. |
| Keep an approved decision visible until it is merged and verified | An approved decision was once lost between sessions. |
| Research the reference before asking a scope question | A question that comes with the reference project's answer and citations takes one reply, not three. |
| Validate merged or deleted rules with me | Rule sets were compressed during a handoff, and several decided rules disappeared without anyone noticing. |
| Confirm before deleting anything outside the change | Deleting a file, branch, data or a cloud resource cannot be undone. Removing code that a change replaces is part of the change, so it does not need this confirmation. |

## My setup

- **I work alone.** Governance roles such as approver and reviewer are me. Enterprise process designed for teams adds cost without a reader.
- **My cloud accounts hold several projects.** An agent once described another project's resource as an unused leftover of this one.
- **No AI or co-author attribution, and Git identity stays unchanged.** Some tools add attribution trailers on their own, so the agent checks the final commit message.

## Writing

The writing rules come from the [unslop](https://github.com/cursor/plugins/tree/main/pstack/skills/unslop) skill. That skill is marked for manual use only, so the always-on subset lives here as instructions. Plain, concrete sentences are faster to review, and a number tells me more than an adverb.
