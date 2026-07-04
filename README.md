# homebrew-si4lockmac

Homebrew tap for [si4lockmac](https://github.com/Well365/si4lockmac) — a macOS
privacy veil with remote lock, dead-man switch, and emergency purge.

This is the **si4lockmac-branded** tap. It installs the exact same app as the
[`Well365/lockmac`](https://github.com/Well365/homebrew-lockmac) tap — the
Cask's `url` points at the same `.pkg` release. Pick whichever name you prefer.

## Install

Open **Terminal** (Applications → Utilities). No Homebrew yet? Install it first:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Then install lockmac:

```bash
brew tap Well365/si4lockmac
brew trust Well365/si4lockmac      # trust the third-party tap (Homebrew 6.x, if required)
brew install --cask si4lockmac
```

Or in one line, without a separate tap step:

```bash
brew install --cask Well365/si4lockmac/si4lockmac
```

## Update / uninstall

```bash
brew upgrade --cask si4lockmac
brew uninstall --cask si4lockmac
brew uninstall --zap --cask si4lockmac   # also remove config, cache, login agents
```

## Maintainer: cutting a new release

Automated: in the code repo, bump the version + commit, then run
`packaging/build-pkg.sh` — it builds the pkg and syncs the version + sha256 into
every `Casks/*.rb` in **both** tap clones (`homebrew-lockmac` and
`homebrew-si4lockmac`). Then, from `si4lockmac-release/`, run `./publish.sh` — it
creates the GitHub Release on `Well365/si4lockmac`, uploads the `.pkg`, and
pushes both taps.

> The `.pkg` must be signed with a Developer ID and notarized, otherwise
> Gatekeeper blocks the `installer` step and `brew install --cask` fails for
> users. An unsigned pkg only works with a manual "Open Anyway".
