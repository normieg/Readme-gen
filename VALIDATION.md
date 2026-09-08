# Validation record

Validated on 2026-09-08. These checks concern the skill package, not a running implementation of the fictional Fieldboard application.

| Check | Result |
| --- | --- |
| Required deliverables | All 15 required files exist: entry point, six references, seven templates, one example. |
| Bundled asset | One additional SVG mockup supports the example's image link; 16 package files total. |
| Skill metadata | Bundled Codex `quick_validate.py` reports `Skill is valid!`. |
| Progressive disclosure | Entry point is 96 lines; detailed guidance and seven distinct templates are routed by task. |
| Local package links | All 20 prose-level relative links/image paths and heading anchors resolve. Syntax examples in code are excluded. |
| Markdown structure | Fences balance across all 15 Markdown files; no trailing whitespace or unintended output placeholders were found outside template scaffolds. |
| SVG | `xmllint --noout` succeeds; macOS Quick Look renders a thumbnail, but its preview crops the right side. Full browser visual verification was unavailable. |
| Example badges | All four public Shields URLs return HTTP 200 SVGs with matching technology titles and no provider-error title. |
| Mermaid | Five diagram blocks reviewed manually for conservative syntax and internally coherent edges. No local Mermaid parser/renderer was available. |
| Scope | Source package and handoff docs created locally; no personal installation, commit, deployment or publication performed. |

The system Python initially could not import PyYAML. The existing offline cache supplied a usable environment; no online dependency download was needed. Metadata validation was run with:

```bash
uv run --offline --with pyyaml python \
  /Users/grey/.codex/skills/.system/skill-creator/scripts/quick_validate.py \
  /Users/grey/orca/projects/ReadMe-Generator/readme-gen
```

The validator's absolute path is specific to the build environment and is not a dependency of the delivered skill. The link/fence checks were ad hoc read-only inspections; no validator script is shipped with the package.

## Review boundaries

The instructions were reviewed for audit-only behavior, narrow-edit preservation, conflicting lockfiles, missing repository access, unverified deployment/publication, absent licenses/assets and secret-bearing documentation. This is a static editorial review, not an independent model behavior benchmark.

No application commands from the fictional example were run. No end-to-end skill execution across real repositories, GitHub-rendered README preview, Mermaid parser validation or cross-agent installation test was performed. The browser's URL policy blocked opening the local SVG; no browser-policy workaround was attempted. Local badge responses and a valid skill manifest do not prove those behaviors.

The original builder specification was the input and is not included in the distributed package. Templates intentionally contain authoring placeholders; the entry point explicitly requires removing them from generated project READMEs unless the user asks for a reusable skeleton.

## Installation documentation follow-up

The README now documents Claude Code, Codex and other compatible agents, using official host documentation for install paths and invocation. All four Bash blocks passed `bash -n`. The shared copy step was run against a temporary destination containing spaces: the installed folder matched the complete source package, and a second run refused to overwrite it. No personal agent installation was changed. This verifies the copy procedure, not live discovery or execution in each agent.
