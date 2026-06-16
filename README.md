# hegale

The game registry for the [shaw](https://github.com/justin06lee/shaw) terminal
arcade.

`hegale` is the catalog of available games. It is a single machine-readable
[`index.json`](./index.json) that lists each game and points at the per-OS game
binaries it can be installed from. The
[shaw](https://github.com/justin06lee/shaw) launcher reads this index to install
games onto a user's machine.

The registry is served raw from GitHub:

```
https://raw.githubusercontent.com/justin06lee/hegale/master/index.json
```

## Index format

```json
{
  "games": [
    {
      "name": "snake.shaw",
      "description": "Classic snake for the shaw terminal arcade",
      "version": "1.0.0",
      "binary": "snake.shaw",
      "assets": {
        "darwin/arm64": "https://github.com/.../snake.shaw-darwin-arm64",
        "darwin/amd64": "https://github.com/.../snake.shaw-darwin-amd64",
        "linux/amd64":  "https://github.com/.../snake.shaw-linux-amd64",
        "linux/arm64":  "https://github.com/.../snake.shaw-linux-arm64"
      }
    }
  ]
}
```

- `name` — install id (`shaw install <name>`). Games use the `.shaw` suffix; the
  launcher menu shows the friendly name (e.g. `snake.shaw` → `snake`).
- `binary` — the executable's filename once installed.
- `assets` — download URL per `GOOS/GOARCH`; binaries are hosted as GitHub
  Release assets on each game's own repo.

## Catalog

| Game | Version | Repo |
|------|---------|------|
| snake.shaw | 1.0.0 | [justin06lee/snake.shaw](https://github.com/justin06lee/snake.shaw) — Snake |

## Adding a game

1. Build and release per-OS binaries on the game's own repo (named `<game>-<os>-<arch>`).
2. Add an entry to `index.json` with the release-asset URLs.
3. Push. `shaw install <game>` picks it up immediately.

## Related

- [shaw](https://github.com/justin06lee/shaw) — the launcher that pulls from this registry.
- [kalama](https://github.com/justin06lee/kalama) — the engine games are built on.
