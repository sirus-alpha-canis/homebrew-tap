# sirus-alpha-canis/homebrew-tap

Homebrew formulae for [Mirante](https://github.com/sirus-alpha-canis/mirante), a
local-first cockpit for dispatching and supervising coding agents.

| Formula | What it installs |
| --- | --- |
| `mirante` | The prebuilt CLI (`mirante`), daemon (`mirante-daemon`), agent hook (`mirante-hook`) and MCP server (`mirante-mcp`), for macOS on Apple silicon and Intel |

The desktop app is not here yet: it is unsigned until there are signed releases, so build it
from the [Mirante repository](https://github.com/sirus-alpha-canis/mirante#2-the-desktop-app)
(`scripts/install.sh --app`).

## Install

```bash
brew install sirus-alpha-canis/tap/mirante
mirante daemon start
mirante doctor
```

Mirante runs Claude Code and/or the Codex CLI, which must be installed and logged in.
If you installed Mirante from source before (`scripts/install.sh`, which links into
`~/.local/bin`), run its `scripts/uninstall.sh` first so only one copy is on your `PATH`.

## Upgrade

```bash
brew update
brew upgrade mirante
mirante daemon restart      # once no task is running, so the new daemon takes over
```

## Uninstall

```bash
mirante daemon stop
brew uninstall mirante
brew untap sirus-alpha-canis/tap
```

Your data in `~/.mirante` (tasks, history, the skill library) is kept; delete it yourself
if you want it gone.

## How the formula is updated

Each Mirante release (a `v*` tag) builds the binaries on GitHub Actions and publishes them,
with `SHA256SUMS`, on the [releases page](https://github.com/sirus-alpha-canis/mirante/releases).
The release workflow then rewrites `Formula/mirante.rb` here with
[`scripts/homebrew-formula.sh`](https://github.com/sirus-alpha-canis/mirante/blob/main/scripts/homebrew-formula.sh).
Details: [RELEASING.md](https://github.com/sirus-alpha-canis/mirante/blob/main/RELEASING.md).

## License

[Apache-2.0](LICENSE), like Mirante.
