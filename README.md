# hegale

The game registry for the [shaw](https://github.com/justin06lee/shaw) terminal
arcade engine.

`hegale` is the catalog of available games: a machine-readable index plus the
per-OS game binaries it points at. The [kalama](https://github.com/justin06lee/kalama)
package manager reads this registry to install games onto a user's machine.

> **Status: stub.** Nothing is built yet. The design lives in the shaw repo at
> `docs/superpowers/specs/2026-05-23-arcade-engine-design.md`. This repo reserves
> the name and will hold the registry index (`index.json`) and release assets.

## Planned shape

- `index.json` — list of games, versions, and per-OS/arch download URLs.
- Game binaries served as release assets.

## Related

- [shaw](https://github.com/justin06lee/shaw) — the arcade engine games are built on.
- [kalama](https://github.com/justin06lee/kalama) — the package manager that pulls from this registry.
