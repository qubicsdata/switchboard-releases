# Install Switchboard

Switchboard 2.0.2 is distributed through this **public** [GitHub repository](https://github.com/qubicsdata/switchboard-releases). The [Homebrew tap](https://github.com/qubicsdata/homebrew-tap) is public; the application development repository remains private. The application is licensed under Apache-2.0. Packages are built locally. This release does not use GitHub Actions, native Apple installers, notarization or the separate signed-updater trust-key route.


The release repository provides installers, checksums, notices and acceptance evidence. Installing does not require access to the separate private source repository or a source checkout. Use the standalone installer below, or Homebrew if a bottle supports your platform.

## Standalone installer

Download `install-switchboard.sh`, `SHA256SUMS` and the matching `switchboard-2.0.2-…-TARGET-node.tar.gz` asset from the [2.0.2 release](https://github.com/qubicsdata/switchboard-releases/releases/tag/v2.0.2). No GitHub account is required for browser downloads. `TARGET` is `darwin-arm64`, `darwin-x64`, `linux-arm64` or `linux-x64`. Compute the bootstrap and archive hashes with `shasum -a 256 FILE` on macOS or `sha256sum FILE` on Linux, and compare both against `SHA256SUMS` before running them. Stop if either differs. Checksums detect altered bytes relative to the published manifest; they are not an independent publisher signature.

If you already use GitHub CLI, you can also download the files with:

```sh
gh release download v2.0.2 --repo qubicsdata/switchboard-releases \
  --pattern 'install-switchboard.sh' --pattern 'SHA256SUMS' \
  --pattern 'switchboard-2.0.2-*-darwin-arm64-node.tar.gz'
```

Choose the target matching your machine. Supply the archive's exact SHA-256 from `SHA256SUMS` and a private installation prefix:

```sh
sh install-switchboard.sh --archive /absolute/path/to/downloaded-archive.tar.gz \
  --sha256 TRUSTED_ARCHIVE_SHA256 --prefix "$HOME/.local/share/switchboard"
```

The bootstrap uses the archive's bundled runtime; Node and a compiler are unnecessary. The first install activates the new release. Installing into an existing prefix stages it; stop active work and use `switchboard upgrade apply RELEASE_ID --prefix PREFIX` to activate the staged release with its transactional snapshot lifecycle. `RELEASE_ID` is printed by the installer. Each prefix serves one Switchboard home. The installer does not start a service or delete user data.

## Homebrew alternative

The formula selects the matching verified Homebrew bottle and installs its pinned Node 24.21.0 runtime. Bottles preserve the accepted runtime bytes and use SHA-256 verification. The tested macOS bottle tags are `arm64_golden_gate` and `golden_gate` (macOS 27); Linux uses `arm64_linux` and `x86_64_linux`. On other macOS versions, use the matching standalone archive; the bottle formula refuses source fallback that could alter the runtime. A separate Node installation is unnecessary. Windows and musl Linux are not supported.

## Install with Homebrew

The tap and release assets are public. No GitHub account or token is required:

```sh
brew tap qubicsdata/tap https://github.com/qubicsdata/homebrew-tap
brew install qubicsdata/tap/switchboard
switchboard --version
```

Homebrew 7 may request `brew trust qubicsdata/tap` before installation.

Homebrew downloads public assets over HTTPS and verifies the pinned SHA-256 before pouring the bottle. Current formulas do not use the historical private download strategy.

First-run setup is explicit:

```sh
switchboard init
switchboard doctor --json
switchboard ui
```

Installation does not start a daemon, enable login startup, run model work, install vendor CLIs or sign in to vendor accounts. Switchboard uses `~/.switchboard` by default. Select another home with `--home` or `SWITCHBOARD_HOME`, and use that same home for subsequent commands. Application data and project repositories are separate from the Homebrew keg.

## Update and remove

```sh
brew upgrade qubicsdata/tap/switchboard
brew uninstall switchboard
```

Homebrew owns this installation. `switchboard upgrade` and the transactional archive installer are different distribution routes; use `brew upgrade` here. Homebrew does not claim the archive installer's snapshot/rollback transaction. Removing the formula keeps application homes and project data.

## Optional login service

```sh
brew services start qubicsdata/tap/switchboard
brew services stop qubicsdata/tap/switchboard
```

Use one supervisor for a home. If an existing checkout or transactional installation already owns its service, migrate that service deliberately before starting the Homebrew service. The wrapper uses the stable Homebrew `opt` path for hooks and marks the distribution and service owner as Homebrew. Install/test commands do not start a service automatically.

## Development and companion application

Developers with separate source access can see [building from source](https://github.com/qubicsdata/switchboard-distribution/blob/main/docs/building.md). Standalone and Homebrew launchers must remain separate.

The optional [Folio planning client](https://github.com/qubicsdata/folio-releases) provides public standalone downloads and installs independently with `brew install qubicsdata/tap/folio-workspace` through the public tap. Neither product writes directly into the other's databases.

## Upgrade and recover

Finish active work and stop the app before a Homebrew upgrade. Back up the selected Switchboard home and each project's `.switchboard` data while the daemon is stopped; keep registered project folders at their existing paths. The Homebrew keg contains software, while these folders contain user state.

Homebrew controls application activation and cleanup. Its upgrade does not run the standalone installer's transactional snapshot sequence. If you need to recover, stop the app first and restore both a compatible application version and the corresponding data backup. Do not run an older binary against data migrated by a newer version without a compatible backup. Retain backups until the upgraded app and connected workflows have been checked.

The optional standalone installer has its own `switchboard upgrade` snapshot and rollback lifecycle. Do not mix Homebrew and standalone supervisors or launchers for the same home.
