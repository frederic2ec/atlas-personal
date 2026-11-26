# atlas-personal

My personal agent setup for [Mivern Atlas](https://github.com/MivernLabs/mivern-atlas). This repository is my `~/.atlas` folder. Cloning it on a new machine and running one command gives every coding agent there my personal rules and skills.

It is also a working example of a personal profile: rules that follow one person into every project and every agent, kept separate from the rules a project commits for all its contributors.

## Set up a new machine

```sh
git clone https://github.com/frederic2ec/atlas-personal ~/.atlas
atlas sync --scope user
```

`sync` detects the agent hosts installed on this machine, such as Codex, Claude Code, OpenCode, Zed or Junie. For each one it does two things:

- writes my rules into a managed section of the host's global instruction file, for example `~/.codex/AGENTS.md` or `~/.claude/CLAUDE.md`;
- installs every skill below into the host's user skill folder, pinned to the exact commit in the lock.

`atlas hosts --scope user` shows what was detected and where each file goes. `atlas doctor --scope user` checks that everything matches the lock.

Nothing in this repository is specific to one machine. Paths are stored relative to the home folder, and the hosts are detected again on each machine. Running `sync` on another computer does not change any committed file. Caches and machine-local records stay out of Git through `.gitignore`.

## Personal rules and project rules

Agent instructions mix two kinds of rules.

- **Project rules** belong to a repository. Examples are its architecture, its commands, its review requirements and its security boundaries. Every contributor and every CI agent must receive them, so they are committed with the code.
- **Personal rules** belong to a person. Examples are how they want agents to talk to them, how they write, which models they pay for, and procedures they use across projects. Committing these into each repository forces them on other contributors, and copying them by hand means they drift.

A project's own rules win where the two differ. Personal rules never grant authority that a project or task did not grant.

## What is in this folder

| Path | Purpose | Edit by hand? |
|---|---|---|
| `atlas.json` | Selected rule packs and their sources | Through `atlas add` and `atlas source add` |
| `atlas.lock.json` | Exact version and checksum of each selected pack | No. Atlas writes it. |
| `atlas.skills.json` | Selected skills: repository, path and commit | Through `atlas skill add` |
| `atlas.skills.lock.json` | Checksum of each pinned skill | No. Atlas writes it. |
| `rules/*.md` | Short personal rules that are not worth a pack | Yes |
| `packs/` | My own rule packs, published so others can use them | Yes, as new version files |
| `.gitignore` | Keeps caches, write locks and install records local | Atlas maintains it |

## Rule packs

| Pack | What it covers |
|---|---|
| [personal-workflow](packs/personal-workflow/) | How agents talk to me, my working setup, Git attribution and identity, and writing style |
| [model-routing](packs/model-routing/) | Which model tier does which work, and how child agents and reviewers are run |

Each pack folder has a README that explains why its rules exist.

## Skills

Skills load only when a task matches their description, so they cost nothing until they are used.

| Skill | Source | What it is for |
|---|---|---|
| [council](packs/council/) | this repository | Multi-model investigations and reviews, when I ask for one |
| unslop | [cursor/plugins](https://github.com/cursor/plugins/tree/main/pstack/skills/unslop) | Removing AI writing patterns. `personal-workflow` applies its core rules at all times. |
| nodejs-cli-best-practices | [lirantal/nodejs-cli-apps-best-practices](https://github.com/lirantal/nodejs-cli-apps-best-practices) | Building and auditing Node.js command-line tools |
| frontend-design | [anthropics/skills](https://github.com/anthropics/skills/tree/main/skills/frontend-design) | Visual direction for new interfaces |
| composition-patterns | [vercel-labs/agent-skills](https://github.com/vercel-labs/agent-skills) | React component composition and API design |
| react-best-practices | vercel-labs/agent-skills | React and Next.js performance |
| react-native-skills | vercel-labs/agent-skills | React Native and Expo |
| react-view-transitions | vercel-labs/agent-skills | React View Transition API animations |
| web-design-guidelines | vercel-labs/agent-skills | Reviewing UI against web interface guidelines |
| writing-guidelines | vercel-labs/agent-skills | Reviewing documentation prose |
| deploy-to-vercel | vercel-labs/agent-skills | Deploying to Vercel |
| vercel-cli-with-tokens | vercel-labs/agent-skills | Vercel CLI with access tokens |
| vercel-optimize | vercel-labs/agent-skills | Vercel cost and performance analysis |
| ui-ux-pro-max | [nextlevelbuilder/ui-ux-pro-max-skill](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill) | Searchable UI and UX design reference |
| design | nextlevelbuilder/ui-ux-pro-max-skill | Brand, logo, icon and social asset design |
| design-system | nextlevelbuilder/ui-ux-pro-max-skill | Design tokens and component specifications |
| ui-styling | nextlevelbuilder/ui-ux-pro-max-skill | shadcn/ui, Tailwind and canvas styling |
| brand | nextlevelbuilder/ui-ux-pro-max-skill | Brand voice and identity |
| banner-design | nextlevelbuilder/ui-ux-pro-max-skill | Banners for social, ads and print |
| slides | nextlevelbuilder/ui-ux-pro-max-skill | HTML presentations |

A skill from a library or framework does not decide a project's stack. When a skill's example uses a library the project did not select, the project's choice wins.

## Add or update a skill

```sh
# Add a skill from GitHub, pinned to a commit
atlas skill add https://github.com/<owner>/<repo> --ref <commit> --path <path/to/skill> --scope user

# Update it later: run the same command with the new commit
atlas skill add https://github.com/<owner>/<repo> --ref <new-commit> --path <path/to/skill> --scope user
```

Commit the changed `atlas.skills.json` and `atlas.skills.lock.json`. Other machines pick the change up on their next `git pull` and `atlas sync --scope user`.

## Use only the packs

Anyone can select these rule packs without adopting the rest of this profile:

```sh
atlas source add personal https://github.com/frederic2ec/atlas-personal --ref <commit> --path packs --scope user
atlas add personal/personal-workflow --scope user
atlas skill add personal/council --scope user
```

Pack versions are immutable. Atlas locks each one by checksum, so a change ships as a new version file such as `1.1.0.md`.

## Using this as a template

Fork it, rewrite the rules as your own, and pin your own skills. Keep the following in mind.

- **Rules that should bind every contributor belong in the project.** Put them in the project's `.atlas/rules/` or in a shared pack, not here.
- **Every rule section ends with a Do and an Avoid example.** Agents apply a rule more reliably when they see the difference.
- **Keep the always-loaded text short.** Some hosts stop reading instruction files at 24 to 32 KB. Move long procedures into skills, which load only when a task matches.

## License

[MIT](LICENSE) for this repository's own content. The pinned third-party skills keep their own licenses.
