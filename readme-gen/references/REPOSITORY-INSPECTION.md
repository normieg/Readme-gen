# Repository inspection

## Evidence and scope

Start with the requested README, repository root and `git status --short` when Git is available. Use repository search/read tools; inspect indexed code first when the environment provides a maintained index. With ordinary shell access, prefer `rg --files --hidden -g '!.git'` and focused `rg` queries. Do not dump the repository. Exclude `node_modules`, `dist`, `build`, `.next`, `coverage`, `vendor`, `generated`, `.cache`, `.expo`, and similar outputs unless the specific question requires them.

Read an existing README fully before redesigning. Inventory potentially relevant files, then read only sources needed to establish claims. File presence alone is preliminary evidence: check whether config is active and whether imported integrations have callers.

| Strength | Evidence | What it can establish |
| --- | --- | --- |
| Strong | Executable source, reachable imports, scripts, active configuration, manifests, lockfiles | Implemented behavior, declared/resolved versions, configured commands |
| Contextual | Deployment config, environment validation, CI jobs | Intended targets, required configuration, automated workflow definitions |
| Medium | Maintained internal docs, explanatory comments | Intent and constraints to cross-check |
| Weak | Old README, stale config, unused/transitive dependencies | Leads for investigation, not independent proof |

Working ledger example: `server/routes.ts:createTask → task creation endpoint implemented; authentication middleware checked in server/app.ts`. Record paths or symbols for each significant feature and diagram edge. Keep this working evidence separate from the polished README unless source links help the reader.

Use current executable configuration/source first, then manifests/lockfiles, deployment config, environment contracts, CI, current internal docs, existing README, and user description. This order is a heuristic. A user's uncommitted design intent can explain a mismatch but cannot make an unimplemented capability current. Report consequential conflicts with both sources.

## Language, runtime and framework

| Ecosystem | Inspect | Distinguish |
| --- | --- | --- |
| JavaScript / TypeScript | `package.json`, lockfiles, `tsconfig*`, imports, runtime pins, framework config | Language from source; runtime from engines/config; direct from transitive dependencies |
| Python | `pyproject.toml`, requirements files, `Pipfile`, `poetry.lock`, `uv.lock`, imports | Packaging/build backend, runtime constraints, application entry points |
| Rust | `Cargo.toml`, `Cargo.lock`, `rust-toolchain*`, source | Binary targets, library targets, workspace members, minimum Rust version |
| Go | `go.mod`, `go.sum`, `cmd/`, packages | Module path, Go directive, service versus library |
| Java / Kotlin | `pom.xml`, Gradle files, wrapper files, source | JVM/toolchain requirements, plugins, application and test tasks |
| PHP | `composer.json`, `composer.lock`, routes/bootstrap | Framework, PHP constraints, scripts and extensions |
| Native / desktop | Platform manifests, `app.json`, `app.config.*`, `eas.json`, Electron/Tauri config, native targets | Configured build targets versus released/supported platforms |
| Infrastructure | Dockerfiles, Compose, IaC modules, manifests, CI | Provisioned boundaries, deployment prerequisites, examples versus active definitions |

Match framework packages to entry points and active config: `next` plus Next configuration/routes; `expo` plus Expo config; `react-native` plus native/app entry points; `fastify` plus server registration; Supabase or Convex packages plus initialized clients and called functions. A directory named `app` does not prove Next.js, nor does a database client prove the database is in use.

Exact versions come from the relevant resolved lockfile entry. A manifest range is a declared constraint, not an exact installed version. Runtime support comes from explicit compatibility policy, engines/toolchain files and CI matrices; a developer's installed runtime is not the project's supported version. Omit noisy version labels.

## Archetype and boundaries

Determine the primary interface: product UI, imported API, terminal executable, service endpoint, workspace ecosystem, or framework extension/generator. Confirm actual workspace declarations (`workspaces`, `pnpm-workspace.yaml`, Cargo/Go workspace config, build-system config) before calling a repository a monorepo. A frontend/backend pair may be a full-stack application; choose the structure that helps its readers.

For each significant subsystem, trace its entry point and calls:

| Area | Stronger evidence than a package name |
| --- | --- |
| Frontend/mobile | Routes, screens, entry points and UI actions |
| Backend/API | Registered handlers, service methods, reachable endpoints |
| Database | Schema/migrations and actual read/write call sites |
| Authentication/authorization | Session setup, middleware, identity checks and ownership/policy enforcement |
| Storage/realtime | Upload/download code, bucket config, subscriptions or socket handlers |
| Cache/queue/jobs | Cache use and invalidation; enqueue/consumer pair; scheduled handler |
| Maps | Rendered map component, provider initialization, token contract |
| AI | Provider client, actual invocation, configured model selection, retrieval/index paths |
| External providers | Outbound calls and the server/client boundary where credentials are used |

Do not equate sign-in with authorization, a Redis client with a cache, or an AI SDK with a chatbot. Trace enough of each feature to describe what a user can do. For diagrams, distinguish runtime calls, data movement, imports and deployment grouping; never draw an edge solely because two folders coexist.

## Setup and package managers

| Evidence | Candidate |
| --- | --- |
| `package-lock.json` / `npm-shrinkwrap.json` | npm |
| `pnpm-lock.yaml` | pnpm |
| `yarn.lock` | Yarn; inspect major version/config |
| `bun.lock` / `bun.lockb` | Bun |
| `poetry.lock`, `uv.lock`, `Pipfile.lock` | Corresponding Python workflow |

Cross-check `packageManager`, manager configuration, task scripts, CI and contributor docs. Multiple lockfiles may belong to independent workspaces; determine their scope. For competing root lockfiles, investigate active CI and conventions. If unresolved, surface the conflict instead of guessing.

Read actual scripts, Makefile/task targets, wrappers and commands they call. Document install, build and run commands with the correct working directory and prerequisites. Do not assume `dev`, `start`, `lint`, `typecheck`, or `test` scripts exist. Distinguish contributor installation from consuming a published package. Verify a package is published before recommending registry installation; local package metadata alone does not prove publication.

Obtain a clone URL from a relevant Git remote or explicit user input. Inspect only the needed remote; strip embedded credentials, and avoid publishing private/internal hostnames without context. Unknown remote: start with “From the repository root” and omit cloning. Never substitute `owner/repo` in a finished README.

## Environment contract and secrets

Prefer `.env.example`, `.env.sample`, schema validators, config loaders, and named environment accesses. Inspect references, not secret-bearing `.env` files, credential stores or private keys. Examples may themselves contain sensitive values: extract names and classifications, not values.

For each documented name, establish required versus optional, default behavior, client/public versus server secret, and build-time versus runtime. If the contract is inconsistent, say so. Show `NAME=` with blank values and explain acquisition/configuration in prose where established. A public prefix is framework-specific, not a universal security guarantee.

If the existing README appears to contain a credential, report its location without reproducing it. In an authorized rewrite, remove the exposed value from the documentation and flag the need for owner-led rotation; do not claim history cleanup or rotation occurred.

## Tests, CI and deployment

Inspect test files/configuration together with commands: Vitest, Jest, Playwright, Cypress, pytest, Go tests, Cargo tests, or JUnit as relevant. A dependency without tests is insufficient. A script that prints “no tests” is not a suite. Surface an existing unified check command, and explain whether it includes build or integration services. Separate static verification from an actual run and report run outcomes accurately.

Read workflow triggers, job commands and workflow filenames before describing CI or constructing status badges. Configured jobs do not prove a recent run succeeded, coverage exists, or a release was published.

Find active deployment configuration: `vercel.json`, `netlify.toml`, `wrangler.toml`/JSON config, `railway.json`, `render.yaml`, `fly.toml`, Docker/Compose, Kubernetes/IaC, `eas.json`, or provider workflows. Corroborate with build outputs and scripts. Say “configured for” unless live deployment is separately verified. Docker does not prove Kubernetes; EAS configuration does not prove an App Store release.

Document distinct frontend, backend, worker, native, static export and migration surfaces separately. Explain required target/environment and consequences of deployment, infrastructure teardown, live database migrations, package publication and app submission. Do not run them to verify documentation.

## Assets, docs and identity

Inspect actual logos, screenshots, filenames, source-relative paths and casing. View assets when visual suitability or staleness matters; existence alone does not establish that a screenshot matches the current UI. Link deeper architecture, API, data-model, business-rule, security, roadmap and contributor docs only if present.

Verify license text and reconcile manifest metadata; never infer MIT from project type. Source release status, supported platforms, roadmap, acknowledgements, contributors and demo URLs from explicit evidence. School or prototype status is not permission to invent planned features. Omit unavailable optional facts.
