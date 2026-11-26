# atlas-personal

My personal agent guidance, published as a [Mivern Atlas](https://github.com/MivernLabs/mivern-atlas) catalog. It is a working example of a personal profile: rules that follow one person into every project and every coding agent, kept separate from the rules a project commits for all its contributors.

## Personal rules and project rules

Agent instructions mix two kinds of rules.

- **Project rules** belong to a repository. Examples are its architecture, its commands, its review requirements and its security boundaries. Every contributor and every CI agent must receive them, so they are committed with the code.
- **Personal rules** belong to a person. Examples are how they want agents to talk to them, how they write, which models they pay for, and procedures they use across projects. Committing these into each repository forces them on other contributors, and copying them by hand means they drift.

Atlas installs a personal catalog at user scope. It writes a managed section into each agent host's global instruction file, such as `~/.codex/AGENTS.md` and `~/.claude/CLAUDE.md`, and installs personal skills into each host's user skill folder. A project's own rules still win where the two differ, and personal rules never grant authority a project did not grant.

## Packs

| Pack | Kind | What it covers |
|---|---|---|
| [personal-workflow](packs/personal-workflow/) | Rules | How agents talk to me, my working setup, Git attribution and identity, and writing style |
| [model-routing](packs/model-routing/) | Rules | Which model tier does which work, and how children and reviewers are run |
| [council](packs/council/) | Skill | A procedure for multi-model investigations and reviews, loaded only when asked for |

Each pack folder has a README that explains why its rules exist.

## Layout

```text
packs/
  <pack>/
    1.0.0.json        descriptor: the pack's name, version and resources
    1.0.0.md          always-loaded rules
    skills/<skill>/   optional skills, loaded by the host when a task matches
    README.md         explanation for humans; Atlas does not install it
```

A descriptor lists `instructions` resources (Markdown rendered into the instruction file) and `skill` resources (folders with a `SKILL.md`). Versions are immutable. Atlas locks each one by checksum, so a change ships as a new version file.

## Install

```sh
atlas init --scope user
atlas source add personal https://github.com/frederic2ec/atlas-personal --ref <commit> --path packs --scope user
atlas add personal/personal-workflow --scope user
atlas add personal/model-routing --scope user
atlas skill add personal/council --scope user
atlas sync --scope user
```

`atlas hosts --scope user` lists the agent hosts Atlas detected and the file it writes for each.
## Using this as a template

Fork it, then rewrite the rules as your own. Keep the following in mind.

- **Rules that should bind every contributor belong in the project.** Put them in the project's `.atlas/rules/` or in a shared pack, not here.
- **Every rule section ends with a Do and an Avoid example.** Agents apply a rule more reliably when they see the difference.
- **Keep the always-loaded text short.** Some hosts stop reading instruction files at 24 to 32 KB. Move long procedures into skills, which load only when a task matches.
