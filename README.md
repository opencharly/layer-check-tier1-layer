# check-tier1-layer

Tier-1 benchmark marker layer for the harness `tier1-easy` recipe.

The `check-tier1-layer` candy (`bench-tier1`) writes `/etc/charly-bench-marker`
containing the string `charly benchmark target`, satisfying the `tier1-easy`
harness recipe. It is a minimal, deterministic layer used as the target of
harness benchmark scenarios.

## What it provides

| Property | Value |
|---|---|
| Layer / candy | `check-tier1-layer` (`bench-tier1`) |
| Packages | none |
| Artifact | `/etc/charly-bench-marker` (mode `0644`, contents `charly benchmark target`) |
| Service / port | none |

## How to use it

Compose the layer by pinning this repo in a box's `candy:` list:

```yaml
my-bed:
  candy:
    base: fedora
    candy:
      - '@github.com/opencharly/layer-check-tier1-layer:v2026.239.1623'
```

The layer creates `/etc`, writes the marker at mode `0644`, and asserts the
file's presence, its mode, and its benchmark-target string.

## Layout

- `charly.yml` — the `check-tier1-layer:` candy entity: the `mkdir:`/`write:`
  steps and the `check:` assertions.
- `.github/workflows/tag-on-merge.yml` — CalVer tag + `CHANGELOG/` on merge.
- `README.md` — this user overview.

## Related

- Owning skill: `/charly-check:check` — the check bed and `plan:` authoring
  reference (this repo declares no `skill:` entity; the gap is tracked in
  [`opencharly/opencharly#291`](https://github.com/opencharly/opencharly/issues/291))
- The `tier1-easy` harness benchmark recipe
- [`opencharly/charly`](https://github.com/opencharly/charly) — the charly CLI and image builder
- [`opencharly/opencharly`](https://github.com/opencharly/opencharly) — the umbrella
