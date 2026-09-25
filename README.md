# oats-authoring

Official additive [OATS](https://github.com/awebai/oats) authoring guidance. This repository is the single canonical home of three Agent Skills:

- `integration-authoring` routes reusable capability/integration work to the framework's integrations expert;
- `skill-craft` teaches grounded Agent Skills design, triggering, evaluation, and maintenance; and
- `soul-craft` teaches concise durable soul operating docs and the boundary between always-loaded instructions, on-demand skills, and knowledge.

It is not a core capability (no `layer`) and contributes no commands, hooks, host requirements, or deployment policy.

## Requirements

A compatible OATS deployment must provide the `integrations-expert` soul for the delegation workflow. The skill uses the public `oats spawn` command; it does not locate or import private kernel files.

The frozen addendum supports this flat capability-root declaration. The package requires OATS `>=0.25.0` (the workspace model its guidance teaches); see [`SCHEMA-STATUS.md`](SCHEMA-STATUS.md) for the remaining released-kernel fixture gate.

## Use it in a workspace

Declare the package in the workspace's `oats-workspace.yaml` (declaring it is
the trust decision; this package exports skills only, so nothing runs), give
the capability to the souls that author, then run `oats sync`:

```yaml
packages:
  oats.authoring: v1.0.2                  # through the official catalog
  # or: git:github.com/awebai/oats-authoring@v1.0.2
defaults:
  capabilities:
    oats.authoring: { from: package }     # or per soul, in its soul.yaml
```

```bash
oats sync
oats spawn <authoring-soul> --preview     # the composed skills include the three above
```

## Development

```bash
npm test
```

This validates both manifests, checks that all three skill paths are package-contained, validates skill frontmatter/name contracts, and rejects private-kernel import guidance. The full acquire → lock → activate → spawn probe remains pending released OATS 0.19.0 consumer fixtures.
