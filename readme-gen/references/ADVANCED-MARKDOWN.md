# GitHub Markdown presentation

Use these patterns only when they improve reading. Asset paths below are illustrative syntax; replace them with verified paths relative to the target README, or omit the element. Never leave nonexistent screenshot/logo references in a generated README.

## Branding and themed assets

Use existing project branding, meaningful alt text, and restrained sizing. A logo is optional; do not create a new project identity or hotlink unrelated third-party images.

```html
<p align="center">
  <img src="./docs/assets/logo.png" width="120" alt="Project logo">
</p>
```

If both variants exist and are suitable, use `<picture>` with a fallback:

```html
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="./docs/assets/logo-dark.svg">
  <source media="(prefers-color-scheme: light)" srcset="./docs/assets/logo-light.svg">
  <img src="./docs/assets/logo-light.svg" width="120" alt="Project logo">
</picture>
```

Do not invent a second asset. Check its appearance on light and dark backgrounds when preview tooling permits. Keep the project description readable outside images.

## Screenshots and grids

```html
<p align="center">
  <img src="./docs/images/dashboard.png" width="800" alt="Dashboard showing tasks grouped by status">
</p>
```

For a small set of mobile screenshots, an HTML table can align them:

```html
<table>
  <tr>
    <td><img src="./docs/images/home.png" width="240" alt="Home with current projects"></td>
    <td><img src="./docs/images/task.png" width="240" alt="Task detail and completion action"></td>
  </tr>
</table>
```

Use actual assets, descriptive captions where useful, and consistent sizing. Label mockups as mockups; a prototype image is not evidence of an implemented feature. Avoid wide galleries and screenshots of credentials/private data. Missing assets normally mean omitting the section, not adding “coming soon.”

## Collapsible secondary material

```html
<details>
<summary>Optional troubleshooting</summary>

Markdown content belongs here, separated from the HTML tags by blank lines.

</details>
```

Use for advanced configuration, long optional examples, troubleshooting or detailed matrices. Keep prerequisites, installation, required environment setup and the first useful command visible. Raw HTML blocks may not parse embedded Markdown as expected; preview mixed content.

## Alerts

Use an alert for a specific actionable fact, not visual decoration. Choose NOTE for context, TIP for optional help, IMPORTANT for a necessary condition, WARNING for a potential problem, or CAUTION for a serious consequence. Follow the [GitHub alerts syntax](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/basic-writing-and-formatting-syntax#alerts):

```markdown
> [!WARNING]
> This migration changes live data. Confirm the target database and the documented backup procedure before running it.
```

Only use such wording when the migration and procedure actually exist. Avoid alert stacks and generic security checklists.

## Other useful patterns

Use a syntax identifier such as `bash`, `env`, `json`, `typescript`, or `text` on fences. Use a longer outer fence when documenting fenced Markdown so the example does not close prematurely. Keep terminal commands copyable; distinguish expected output from the command.

Use task lists only for verified roadmap items or deliberate checklists; never imply an invented task is planned or complete. Footnotes can hold a sourced compatibility caveat without interrupting prose:

```markdown
The compatibility table reflects the checked platforms.[^platforms]

[^platforms]: Explain the actual evidence and its limits here.
```

The example text above is instructional and must be replaced with evidence. A reference-style link can avoid repeated long URLs:

```markdown
Read the [contribution guide][contributing].

[contributing]: ./CONTRIBUTING.md
```

Verify that the file exists. Prefer relative links to repository documents and assets; preserve casing and encode spaces when needed. Resolve paths relative to the README's directory, including when it lives in a workspace. Root-relative links and branch-sensitive GitHub URLs need extra care. Check heading anchors after renaming headings; duplicate headings can produce suffixed IDs.

## Final layout check

Use one H1, a logical H2/H3 hierarchy, balanced fences and HTML tags, consistent table columns, and blank lines around lists and blocks. Do not use scripts, iframes, inline styling tricks or custom CSS that GitHub may strip. Use actual images with alt text, not plain links to badge SVGs. A local preview is useful but does not prove GitHub sanitization or rendering matches exactly; report what was checked.
