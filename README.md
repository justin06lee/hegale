# hegale

The game registry for the [shaw](https://github.com/justin06lee/shaw) terminal
arcade engine.

`hegale` is the catalog of available games. It is a single machine-readable
[`index.json`](./index.json) that lists each game and points at the per-OS game
binaries it can be installed from. The
[kalama](https://github.com/justin06lee/kalama) package manager reads this index
to install games onto a user's machine.

The registry is served raw from GitHub:

```
https://raw.githubusercontent.com/justin06lee/hegale/master/index.json
```

## Index format

```json
{
  "games": [
    {
      "name": "luma",
      "description": "Classic snake for the shaw terminal arcade",
      "version": "1.0.0",
      "binary": "luma",
      "assets": {
        "darwin/arm64": "https://github.com/.../luma-darwin-arm64",
        "darwin/amd64": "https://github.com/.../luma-darwin-amd64",
        "linux/amd64":  "https://github.com/.../luma-linux-amd64",
        "linux/arm64":  "https://github.com/.../luma-linux-arm64"
      }
    }
  ]
}
```

- `name` — install id (`kalama install <name>`).
- `binary` — the executable's filename once installed.
- `assets` — download URL per `GOOS/GOARCH`; binaries are hosted as GitHub
  Release assets on each game's own repo.

## Catalog

| Game | Version | Repo |
|------|---------|------|
| luma | 1.0.0 | [justin06lee/luma](https://github.com/justin06lee/luma) — Snake |

## Adding a game

1. Build and release per-OS binaries on the game's own repo (named `<game>-<os>-<arch>`).
2. Add an entry to `index.json` with the release-asset URLs.
3. Push. `kalama install <game>` picks it up immediately.

## Related

- [shaw](https://github.com/justin06lee/shaw) — the arcade engine games are built on.
- [kalama](https://github.com/justin06lee/kalama) — the package manager that pulls from this registry.
