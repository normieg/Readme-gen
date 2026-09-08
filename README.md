# readme-gen

A standalone Agent Skill for creating, redesigning, auditing and updating GitHub READMEs from repository evidence. Designed for Claude Code, Codex, and other agents that support the [Agent Skills format](https://agentskills.io/home).

Repository truth takes priority over technical clarity, visual polish and marketing. The skill supports applications, libraries, CLIs, APIs, monorepos, frameworks and smaller projects. It includes technology badges, Mermaid architecture, setup, testing and deployment guidance without assuming those capabilities exist in every repository.

## Installation

### Quick install (recommended)

With Node.js/npm and Git available, run this from the project you want to document:

```bash
npx skills add normieg/Readme-gen --skill readme-gen
```

Choose your agent in the installer. It downloads the skill and sets up the appropriate agent directory; no manual clone or copy is needed. The [Skills CLI](https://github.com/vercel-labs/skills#install-a-skill) supports Claude Code, Codex and other agents.

To install for both Claude Code and Codex across all your projects:

```bash
npx skills add normieg/Readme-gen --skill readme-gen --agent claude-code codex --global
```

Omit `--global` for a project-only installation. To preview the available skill without installing it:

```bash
npx skills add normieg/Readme-gen --skill readme-gen --list
```

After installation, use `/readme-gen` in Claude Code or `$readme-gen` in Codex with your request. See [Use and verify](#use-and-verify) for a first audit prompt.

### Manual installation (alternative)

Install the same `readme-gen/` folder in your agent's skills directory. The package contains Markdown instructions and supporting files, with no dependency on a particular model, paid API, MCP server or larger skill collection. Skill discovery and invocation depend on the agent application; a model or chat interface without skill support cannot automatically install it.

### Download the skill

With Git installed, run this in a terminal:

```bash
git clone https://github.com/normieg/Readme-gen.git && cd Readme-gen
```

Alternatively, use GitHub's **Code → Download ZIP**, extract the archive, and locate the inner `readme-gen` folder containing `SKILL.md`. Copy that entire inner folder, including `references`, `templates` and `examples`; copying only `SKILL.md` is insufficient.

### Choose your agent

| Agent | Personal installation: all your projects | Project installation: one target repository | Invoke in the agent chat |
| --- | --- | --- | --- |
| Claude Code | `~/.claude/skills/readme-gen/` | `.claude/skills/readme-gen/` | `/readme-gen Create a README for this project.` |
| Codex | `~/.agents/skills/readme-gen/` | `.agents/skills/readme-gen/` | `$readme-gen Create a README for this project.` |
| Other Agent Skills-compatible agents | Use the agent's documented skills directory | Use its documented project skills directory | Select the skill or use its documented invocation syntax |

`~` means your user home directory. Project paths are relative to the repository you want to document. These Claude Code and Codex locations follow their official [Claude Code skills documentation](https://code.claude.com/docs/en/skills#where-skills-live) and [Codex local skills documentation](https://learn.chatgpt.com/docs/build-skills#where-codex-loads-local-skills).

### Copy into the skills directory

On macOS, Linux or a compatible Bash shell, choose **one** destination below. Run it from the downloaded `Readme-gen` repository root.

For Claude Code:

```bash
skill_parent="$HOME/.claude/skills"
```

For Codex:

```bash
skill_parent="$HOME/.agents/skills"
```

Then run this shared copy step in the same terminal:

```bash
(
  set -eu
  : "${skill_parent:?Choose a skills directory first}"
  test -f ./readme-gen/SKILL.md
  mkdir -p "$skill_parent"
  if [ -e "$skill_parent/readme-gen" ] || [ -L "$skill_parent/readme-gen" ]; then
    printf '%s\n' "readme-gen already exists; compare or back it up before replacing it."
    exit 1
  fi
  cp -R ./readme-gen "$skill_parent/readme-gen"
  test -f "$skill_parent/readme-gen/SKILL.md"
  printf 'Installed readme-gen in %s\n' "$skill_parent/readme-gen"
)
```

For a project-only install, set `skill_parent` to the absolute path of the target repository's `.claude/skills` or `.agents/skills` directory before running the shared step. On Windows without Bash, use File Explorer to copy the inner `readme-gen` folder into the corresponding directory under your user profile or target project; create the parent folders if needed.

Codex users can also ask its built-in installer directly, instead of manually copying files:

```text
Use $skill-installer to install the readme-gen skill from
https://github.com/normieg/Readme-gen/tree/main/readme-gen
```

The built-in installer supports skills from other repositories. See [Codex skill installation](https://learn.chatgpt.com/docs/build-skills#install-curated-skills-for-local-use).

### Use and verify

Open the repository you want to document in your agent and invoke `readme-gen` using the table above. For a first check that makes no edits, ask:

```text
Use readme-gen to audit this repository's README. Report findings without editing files.
```

If the skill does not appear, confirm that `SKILL.md` is directly inside the installed `readme-gen` directory, that the supporting folders were copied, and that you chose the directory for your agent. Reload or restart the agent if needed. Avoid duplicate installations of the same skill across personal and project scopes.

For an agent without native skills, give it the complete skill folder and explicitly ask it to read `SKILL.md` and follow the linked references against your repository. This is manual instruction loading, not automatic skill installation; the agent still needs access to the relevant repository files.

### Update an existing installation

For Skills CLI installations, run `npx skills update readme-gen` to update this skill. Preserve any local customizations first. See the [CLI update reference](https://github.com/vercel-labs/skills#skills-update).

For manual installations, run `git pull --ff-only` in your downloaded `Readme-gen` checkout. Compare or back up any edits to your installed copy, move the previous installation outside the agent's scanned skills directories, then repeat the copy step. The copy instructions intentionally refuse to overwrite an existing installation.

## Package contents

```text
readme-gen/
├── SKILL.md                              # Entry point, mode selection and reference routing
├── references/
│   ├── README-PATTERNS.md                # Audiences, section order and archetype tradeoffs
│   ├── BADGES.md                         # Badge evidence, encoding, logos and dynamic metadata
│   ├── MERMAID.md                        # Architecture discovery, diagram patterns and checks
│   ├── ADVANCED-MARKDOWN.md              # Assets, themes, grids, details, alerts and links
│   ├── REPOSITORY-INSPECTION.md           # Evidence sources, stack detection and operational truth
│   └── QUALITY-CHECKLIST.md               # Accuracy, scope, presentation and audit gates
├── templates/
│   ├── application.md                    # User-facing products and full-stack applications
│   ├── library.md                        # Consumer installation, public API and compatibility
│   ├── cli.md                            # Commands, options, examples and configuration
│   ├── api.md                            # Authentication, service setup and request examples
│   ├── monorepo.md                       # Workspaces, shared setup and separate deployments
│   ├── framework.md                      # Adoption, core concepts and extension boundaries
│   └── minimal.md                        # Short documentation for focused projects
└── examples/
    ├── example-readme.md                 # Explicitly fictional Fieldboard application README
    └── assets/
        └── board-preview.svg            # Bundled, labeled interface mockup used by the example
```

Start with [SKILL.md](readme-gen/SKILL.md) or view the [fictional example](readme-gen/examples/example-readme.md). Templates are authoring scaffolds: the skill replaces their comments/placeholders and removes unsupported sections before writing a project's README.

[VALIDATION.md](VALIDATION.md) records package checks and their limits. The original builder specification is not part of the distributed package or required at runtime.

## Activation and usage

After installation, select the skill using your agent's invocation syntax, or ask:

```text
Use readme-gen to create README.md for this repository. Inspect the code and
configuration first, document the actual setup, and omit unsupported claims.
```

Other supported requests:

| Request | Expected result |
| --- | --- |
| “Create a README for this project.” | Complete README based on inspection and a suitable archetype |
| “Make my GitHub README professional.” | Redesign preserving accurate identity, credits and caveats |
| “Audit my README against the codebase.” | Prioritized evidence-backed findings; no edits |
| “Only add technology logos and badges.” | Verified badge images; unrelated sections preserved |
| “Only add Mermaid architecture.” | Source-backed diagram and concise explanation |
| “Fix outdated installation instructions.” | Correct manager, prerequisites, directories and actual commands |
| “Update the README after the backend migration.” | Update affected stack, architecture, configuration and operations |
| “Make this README shorter.” | Reduce duplication while retaining necessary setup and warnings |

For a specific file, include its path: `Use readme-gen to audit packages/client/README.md without editing it.` Natural-language activation depends on the host selecting the skill; use `/readme-gen` in Claude Code or `$readme-gen` in Codex to invoke it explicitly.

## Assumptions and boundaries

- The deliverable is a portable source package in this repository. Installation instructions are provided; personal installation is a separate step.
- The skill normally has access to the target repository. With no access, it requests relevant files and identifies which claims remain unverified.
- README generation may use network access for public metadata or badge checks, but network access is not required. Missing evidence causes omission or a stated limitation.
- The example's application, commands, tree and license are fictional, as requested. Its image is an original illustrative SVG mockup, not evidence of a working application.
- No license was supplied for this skill package, so none is invented. The example's fictional MIT assumption does not license the skill.

The badge and diagram references link the official documentation used to verify their syntax. Package structure and checks do not establish how reliably every model will apply the skill; see the validation record for the checks actually performed.
