# oats-authoring

Official additive [OATS](https://github.com/awebai/oats) authoring guidance. This repository is the single canonical home of three Agent Skills:

- `integration-authoring` routes reusable capability/integration work to the framework's integrations expert;
- `skill-craft` teaches grounded Agent Skills design, triggering, evaluation, and maintenance; and
- `soul-craft` teaches concise durable soul operating docs and the boundary between always-loaded instructions, on-demand skills, and knowledge.

It claims no fundamental layer and contributes no commands, hooks, host requirements, or deployment policy.

## Requirements

A compatible OATS deployment must provide the `integrations-expert` soul for the delegation workflow. The skill uses the public `oats spawn` command; it does not locate or import private kernel files.

The frozen addendum supports this flat capability-root declaration. The package requires OATS `>=0.19.0`; see [`SCHEMA-STATUS.md`](SCHEMA-STATUS.md) for the remaining released-kernel fixture gate.

## Acquire and activate

Acquisition does not activate the capability. After an official release exists:

```bash
oats install oats.authoring --dir /path/to/scope
oats use oats.authoring --global --dir /path/to/scope
oats doctor /path/to/scope --soul <authoring-soul>
```

A pinned Git source may be used after publication:

```bash
oats install git:https://github.com/awebai/oats-authoring.git@v1.0.0 --dir /path/to/scope
```

No `oats trust` step is needed because the manifest exports skills only. Targeting remains config-owned; activate for an authoring agent type or selected souls instead of globally when appropriate.

## Development

```bash
npm test
```

This validates both manifests, checks that all three skill paths are package-contained, validates skill frontmatter/name contracts, and rejects private-kernel import guidance. The full acquire → lock → activate → spawn probe remains pending released OATS 0.19.0 consumer fixtures.
