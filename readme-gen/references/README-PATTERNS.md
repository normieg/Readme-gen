# README patterns

Choose a primary reader and their next useful action. Section orders below are defaults; omit sections without evidence or reader value. Templates contain authoring prompts, not facts to copy.

## Application

- **Use for / audience:** web, mobile, desktop and full-stack products; evaluators and developers running the app.
- **Order:** header → technology badges → stack table → overview → features → architecture → screenshots/demo → getting started → project structure → usage → testing → deployment → security → documentation → roadmap → contributing → license.
- **Optional:** assets, hosted demo, roadmap, release status, contributing, operational sections when established.
- **Usually omit:** exhaustive routes/schema, every dependency, fictional deployment, API internals already documented elsewhere.
- **Architecture helps:** a UI talks to a backend, identity service, storage or external provider. A tiny local UI may need only prose.
- **Common mistakes:** describing frameworks as features; presenting a mobile build target as a published app; hiding setup below a large screenshot gallery.

## Library

- **Use for / audience:** packages, SDKs, reusable modules and component libraries; consumers first, maintainers second.
- **Order:** header → package/status and selected technology badges → overview → installation → quick start → usage → API/docs → compatibility → testing/development → contributing → license.
- **Optional:** compact stack table for a substantial library, benchmarks with sources/methodology, migration notes, architecture.
- **Usually omit:** application screenshots, deployment, server environment setup unrelated to consumers, invented registry links.
- **Architecture helps:** adapters, plugin interfaces, transforms or a layered SDK need explanation.
- **Common mistakes:** confusing repository setup with package installation; unsupported imports or method names; treating a version range as a compatibility promise.

## CLI

- **Use for / audience:** terminal applications; users seeking a working command, then contributors.
- **Order:** header → status/technology badges → overview → installation → quick start → commands → examples → configuration → optional architecture → development → testing → license.
- **Optional:** verified platform matrix, exit codes, shell completions, configuration precedence and architecture.
- **Usually omit:** screenshot-heavy product sections, web hosting and architecture for a simple executable.
- **Architecture helps:** command dispatch coordinates plugins, parsers, workers or remote systems.
- **Common mistakes:** wrong executable name, invented flags, missing working-directory context, unsafe examples that overwrite files without explanation. Validate against parser definitions and existing command tests/docs; invoke help only if its startup is safe.

## API

- **Use for / audience:** independent REST, GraphQL or RPC services; integrators and operators.
- **Order:** header → badges/stack → overview → architecture → authentication → getting started → environment → representative requests/endpoints → testing → deployment → security → documentation → license.
- **Optional:** versioning, rate limits, pagination, response/error examples and health checks when implemented.
- **Usually omit:** full endpoint/schema dumps when a specification exists, fabricated auth, client screenshots.
- **Architecture helps:** requests pass through auth, business logic, persistence, jobs or external providers.
- **Common mistakes:** documenting unregistered routes, unimplemented status codes or authorization policies; putting server secrets in browser examples.

## Monorepo

- **Use for / audience:** multiple packages, apps or services with workspace coordination; contributors navigating ownership and commands.
- **Order:** header → badges/stack → overview → architecture → workspace table → repository structure → getting started → development → testing → deployment → documentation → license.
- **Optional:** workspace-specific links, dependency graph, release strategy and package compatibility.
- **Usually omit:** duplicate child READMEs, a badge for every workspace dependency, a fake single deployment command.
- **Architecture helps:** clarify runtime services separately from internal package dependencies. Label a dependency graph as such.
- **Common mistakes:** treating all packages as deployed services; documenting root commands where workspace-local commands are needed; hiding different environment contracts.

## Framework

- **Use for / audience:** extensible frameworks, generators or developer platforms; adopters learning the mental model.
- **Order:** header → technology/status badges → overview → use cases → quick start → architecture → core concepts → documentation → examples → development → testing → contributing → license.
- **Optional:** extension points, supported integrations, migration/compatibility, compact stack table.
- **Usually omit:** unsupported ecosystem claims, elaborate internals before first use, invented scaffolding commands.
- **Architecture helps:** runtime phases, extension contracts or generation pipelines are central to adoption.
- **Common mistakes:** calling a reusable helper a framework; claiming plugins exist because extension interfaces do; showing an unpublished generator as a registry command.

## Minimal

- **Use for / audience:** small tools, prototypes, focused scripts and simple infrastructure modules; a reader who needs purpose and usage quickly.
- **Order:** header → overview → compact stack → getting started → usage → license when known.
- **Optional:** a few features, validation command or focused warning. A badge or small diagram only if it materially helps.
- **Usually omit:** badge walls, manual contents, architecture, deployment, security, roadmap and empty headings without evidence.
- **Architecture helps:** an otherwise surprising boundary or external dependency needs one small explanation.
- **Common mistakes:** making a two-file project look like an enterprise platform or omitting prerequisites because the project is small.

## Shared editorial decisions

Use a clear title and one sentence describing the project. Keep overview to one to three short paragraphs: purpose, intended user and normal workflow. Document actual user capabilities under features; put implementation technologies in the stack table. Prefer familiar terms over hype and emoji headings.

Technology badges provide recognition; a substantial project's table explains roles such as runtime, UI, state, backend, database, auth, storage, realtime, queue, maps, AI, testing and deployment. Do not repeat minor dependencies. Treat framework, runtime and language as distinct when that matters.

Repository trees should show major apps/packages, product modules, infrastructure, tests, docs and important scripts with responsibility comments. Verify each path. Link detailed architecture, security and API docs; do not duplicate them.

Use existing project branding and a verified demo near the header when helpful. Preserve accurate credits, migration notes, limits and warnings during redesign. Do not add a manual table of contents automatically. Keep core setup visible and move only secondary detail into collapsible blocks.

Roadmaps must come from documented/user-supplied plans. Release status needs evidence. A public repository can have a short fork → branch → change → run actual checks → pull request contribution workflow; a private/personal repo may not need one. Acknowledgements should credit meaningful contributions, datasets or inspiration, not list every dependency.
