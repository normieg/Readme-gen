# Badges

## Evidence before appearance

Technology badges identify the important stack; status badges report metadata or current service state. Usually use 4–8 major technology badges in `for-the-badge` style and, if useful, 2–5 metadata badges in `flat-square`. Smaller projects need fewer. Keep styling consistent within each group. A substantial README should also explain technology roles in a stack table.

Verify technology use, any displayed version, platform support, workflow filename, package identity/publication, release, license or coverage integration before emitting a badge. Never use static “build passing,” coverage percentages, downloads or release numbers to decorate an unverified project. A test runner badge identifies tooling, not test results.

## Static URL construction

The static path is `/badge/label-message-color`, or `/badge/message-color` without a label. `label` names the subject; `message` is the displayed value; `color` is a named color or hexadecimal value without `#`. Query parameters include `style`, `logo` (Simple Icons slug) and `logoColor`. Use `%20` for spaces, `%2B` for plus and `%2F` for slash; encode values rather than the whole URL. Static badge path text additionally uses `--` for a literal dash and `__` for an underscore; a single `_` becomes a space. Avoid double encoding. Browser/builders may encode input, but hand-authored URLs need explicit encoding. See [Shields static badge documentation](https://shields.io/badges/static-badge).

```markdown
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white)
![React](https://img.shields.io/badge/React-61DAFB?style=for-the-badge&logo=react&logoColor=20232A)
![Fastify](https://img.shields.io/badge/Fastify-000000?style=for-the-badge)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white)
```

These are syntax examples, not evidence that any target repository uses this stack. Versions are intentionally absent. Select actual major technologies: frontend/mobile, runtime, language, backend, persistence, styling, infrastructure and testing where they help recognition.

For encoded text, `/badge/C%2B%2B-00599C` displays C++; `/badge/CI%2FCD-2088FF` displays CI/CD. Do not interpret a syntactically valid example as a recommended project claim.

Use the [Simple Icons catalog](https://simpleicons.org/) or its linked slug list to confirm a logo identifier and branding color. Logos can be removed or change between releases; if unavailable or uncertain, omit `logo` rather than inventing it. Pick a readable foreground; do not convey meaning only through color.

## Embed as an image

```html
<p align="center">
  <img src="https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&amp;logo=typescript&amp;logoColor=white" alt="TypeScript">
</p>
```

Markdown uses `![description](image-url)`. `[description](image-url)` is only a hyperlink and will not display the badge. For a clickable badge, wrap the image in a link to the actual workflow, package or release. Use `&amp;` in HTML attributes and ordinary `&` in Markdown URLs. Do not put Markdown images inside a raw HTML paragraph and assume they will parse.

## Dynamic metadata

The uppercase tokens below are reference placeholders, never finished README content. Replace each only with verified identifiers; otherwise omit the badge. URL-encode individual path segments, including scoped package identifiers, and query values. Verify endpoints against current provider docs when using unfamiliar integrations.

| Kind | Shields URL shape | Required evidence |
| --- | --- | --- |
| GitHub Actions | `https://img.shields.io/github/actions/workflow/status/OWNER/REPO/WORKFLOW.yml?branch=BRANCH&style=flat-square` | Correct GitHub repo, actual workflow filename and selected branch |
| npm version | `https://img.shields.io/npm/v/PACKAGE?style=flat-square` | Actual published npm package; encode `@scope/name` as a path value |
| PyPI version | `https://img.shields.io/pypi/v/PACKAGE?style=flat-square` | Actual PyPI distribution name, not just Python import name |
| crates.io version | `https://img.shields.io/crates/v/CRATE?style=flat-square` | Actual published crate |
| Latest GitHub release | `https://img.shields.io/github/v/release/OWNER/REPO?style=flat-square` | Repository with a release; a Git tag alone is insufficient |
| GitHub license | `https://img.shields.io/github/license/OWNER/REPO?style=flat-square` | License text and repository identity; check provider detection |
| Codecov coverage | `https://img.shields.io/codecov/c/github/OWNER/REPO?style=flat-square` | Configured Codecov project and report upload; verify visibility/branch |

GitHub's own workflow badge shape is `https://github.com/OWNER/REPO/actions/workflows/WORKFLOW.yml/badge.svg?branch=BRANCH`; link to the corresponding workflow page. Shields exposes branch selection and styling through its [workflow badge endpoint](https://shields.io/badges/git-hub-actions-workflow-status). Do not infer workflow success from YAML presence.

For test counts or other coverage providers, use a real reporting integration and its documented badge endpoint. No provider/report means no dynamic result badge. A static platform badge is appropriate only for evidenced targets/support; distinguish configured targets from promised compatibility. Prefer dynamic package/release badges to a manually maintained current-version claim.

For private repositories, assess whether the external badge provider can access the metadata without credentials. Never place tokens in URLs or publish a private repo's identifiers simply to add status decoration. Omit unavailable metadata instead.

## Validate

1. Map every badge claim to repository or explicit user evidence.
2. Check URL encoding, image embedding, alt text, consistent style and contrast.
3. Verify workflow, package, branch, license and icon identifiers when used.
4. If network access is available and appropriate, inspect the returned SVG/preview; an HTTP 200 may still display “not found,” “invalid” or “unknown.” Do not treat unavailable network access as successful verification.
5. Keep technology identification separate from live status; omit badges that add noise or cannot be supported.
