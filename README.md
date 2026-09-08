# readme-gen

A standalone Agent Skill for creating, redesigning, auditing and updating GitHub READMEs from repository evidence.

Repository truth takes priority over technical clarity, visual polish and marketing. The skill supports applications, libraries, CLIs, APIs, monorepos, frameworks and smaller projects. It includes technology badges, Mermaid architecture, setup, testing and deployment guidance without assuming those capabilities exist in every repository.

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

## Install for Codex

Copy the entire `readme-gen` folder into your personal Codex skills directory. The local skill-creation guidance for this environment uses `$CODEX_HOME/skills`, falling back to `$HOME/.codex/skills`. Keep the folder name and its internal layout intact.

From this repository root, the following shell commands create a new installation and refuse to overwrite an existing one:

```bash
skill_parent="${CODEX_HOME:-$HOME/.codex}/skills"
mkdir -p "$skill_parent"
if [ -e "$skill_parent/readme-gen" ] || [ -L "$skill_parent/readme-gen" ]; then
  printf '%s\n' "readme-gen already exists; compare it before replacing it."
else
  cp -R ./readme-gen "$skill_parent/readme-gen"
fi
```

Open a new Codex session in the repository you want to document and invoke `$readme-gen`. This delivery creates the source package in this repository; it does not modify your personal installed skills.

For another agent supporting `SKILL.md` with `name` and `description` frontmatter, put the same complete folder in that agent's documented skill location. Other agents' discovery and rendering behavior have not been tested here. No code generator, network service, larger skill kit or executable helper is required by this package.

## Activation and usage

Example explicit invocation:

```text
Use $readme-gen to create README.md for this repository. Inspect the code and
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

For a specific file, include its path: `Use $readme-gen to audit packages/client/README.md without editing it.` Natural-language activation depends on the host selecting the skill; explicit invocation identifies it directly.

## Assumptions and boundaries

- The deliverable is a portable source package in this repository. Installation instructions are provided; personal installation is a separate step.
- The skill normally has access to the target repository. With no access, it requests relevant files and identifies which claims remain unverified.
- README generation may use network access for public metadata or badge checks, but network access is not required. Missing evidence causes omission or a stated limitation.
- The example's application, commands, tree and license are fictional, as requested. Its image is an original illustrative SVG mockup, not evidence of a working application.
- No license was supplied for this skill package, so none is invented. The example's fictional MIT assumption does not license the skill.

The badge and diagram references link the official documentation used to verify their syntax. Package structure and checks do not establish how reliably every model will apply the skill; see the validation record for the checks actually performed.
