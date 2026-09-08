# README quality gates

Run all applicable gates for a full README or audit. For a narrow edit, run the affected gates plus a preservation diff. “Not applicable” is a useful result; do not create a section just to satisfy this list. Fix supported errors before delivery and distinguish unresolved facts from successful validation.

## Truth and identity

- [ ] Project name, purpose, audience and normal workflow match current evidence.
- [ ] Features are reachable capabilities, not assumptions from dependencies.
- [ ] Major stack roles are correct; direct, transitive, declared and resolved dependencies are distinguished.
- [ ] Version, compatibility, platform, release, roadmap, contributor, metric and production claims have sources.
- [ ] Conflicts are resolved or surfaced; no unsupported claims, fake values or unrequested placeholders remain.

## Visual technology and architecture

- [ ] Badges actually embed images, have alt text, consistent styling and correct encoding.
- [ ] Technologies/versions are evidenced; dynamic workflow, registry, branch, release, coverage and license identifiers exist.
- [ ] Icon slugs are verified or omitted; returned badge errors are not mistaken for success.
- [ ] A substantial stack has a readable role table; badge counts fit the project.
- [ ] Mermaid nodes and edges trace to real boundaries and calls; no fictitious auth, cache, queue, storage or provider exists.
- [ ] Runtime, dependency and deployment relationships are clear, with a brief prose explanation.
- [ ] Fences, quoted labels, brackets, arrows and subgraphs are valid; the diagram is small enough to read.
- [ ] Available parser/render checks were used, or manual-review limitations are recorded honestly.

## Assets, links and structure

- [ ] Logos/screenshots exist, are suitable and have meaningful alt text; mockups are labeled.
- [ ] Paths resolve relative to the actual README location with exact filename casing.
- [ ] Check Markdown links/images, reference-style definitions, HTML `href`/`src`/`srcset`, and internal anchors. Ignore illustrative code samples only when clearly marked as such.
- [ ] Decode URL paths before checking files; check each `srcset` candidate. Do not treat external URLs as filesystem paths or claim network verification from local existence checks.
- [ ] Repository tree entries exist and responsibility comments are accurate; generated/vendor noise is omitted.
- [ ] Existing useful docs, API references, security/contribution guides, roadmap and license are linked when relevant.

## Setup and usage

- [ ] Package manager is supported by scoped lockfiles and active workflow; competing lockfiles were investigated.
- [ ] Required runtime/tool versions and prerequisites have evidence.
- [ ] Install/start/build/usage commands exist or follow the verified ecosystem workflow; correct working directories and prerequisites are stated.
- [ ] Examples use real public exports, executable names, flags, registered routes and request/response shapes.
- [ ] Registry installation and clone URLs use verified identities; local metadata alone does not prove publication.
- [ ] Environment names match schemas/configuration; required/optional, public/secret and build/runtime distinctions are accurate.
- [ ] No credential values or credential-bearing URLs were copied. Suspected exposure is flagged without repetition.

## Tests, deployment and security

- [ ] Test/configuration files support the described suite. A dependency or placeholder script alone is insufficient.
- [ ] Lint/typecheck/build/test/quality commands and CI descriptions match actual configuration.
- [ ] Defined commands are distinguished from executed checks; no test success or coverage is fabricated.
- [ ] Deployment targets are supported; configured targets are distinguished from verified live deployments.
- [ ] Frontend, backend, worker, native builds and migrations have separate instructions where needed.
- [ ] Commands that modify production, destroy resources, publish packages, submit apps or migrate data include the documented context and consequences; they were not run as README validation.
- [ ] Authentication, authorization, rate limits, validation or encryption claims are code-backed and appropriately high-level.
- [ ] License text agrees with the named license/badge; missing or conflicting license evidence is not replaced by an assumed MIT label.

## Editorial and preservation

- [ ] README is scannable, appropriately sized and useful to evaluators and developers.
- [ ] Header/overview explain the project without unsupported hype; features and stack are not redundant.
- [ ] No empty/duplicate sections, instructional template comments, unnecessary contents list, badge wall or excessive emoji remain.
- [ ] Headings, lists, tables, fences and HTML are balanced and consistent.
- [ ] Credits, identity, compatibility notes, migration warnings, caveats and valid links survive redesign.
- [ ] Targeted edits affect only the requested scope; additional findings are reported separately.

## Verification procedure

Review the evidence ledger against the final text. Resolve local links and inspect the diff. Use already available Markdown/Mermaid tools or a preview when possible; do not silently install packages or execute arbitrary project scripts. Inspect any proposed local check first, since even install/test/help commands can execute hooks or touch services. Documentation usually needs command inspection, not every test suite rerun.

Report precisely: for example, “Checked scripts/configuration and local links; reviewed Mermaid syntax manually; application tests were not run.” Claim a renderer/parser result only after seeing it succeed. A visual preview and semantic repository check are separate gates.

## Audit findings

For each finding, give README location, problem, source path/symbol, practical impact and proposed correction. Useful severity conventions:

| Level | Examples |
| --- | --- |
| Critical | Exposed credential, dangerous production instruction with misleading context |
| Important | Nonworking setup, false feature, wrong backend, unsupported security or license claim |
| Improvement | Broken secondary docs link, stale screenshot, confusing architecture, duplicated sections |
| Optional | Cosmetic consistency or a helpful verified badge |

Prioritize actionable findings; do not fill every category. Audit is read-only. Report checks with no findings briefly and identify inaccessible evidence without inventing results.
