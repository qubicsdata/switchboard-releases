Switchboard 2.0.2 hardens extension downloads and opens installation through QubicsData's public release repositories and Homebrew tap.

- HTTPS archive and catalog downloads validate every redirect before issuing the next request, allow at most five redirects, and share one bounded timeout. Requests carry no cookies or authorization headers.
- Pinned Git extension sources use canonical public HTTPS URLs, refuse redirects and other transports, and isolate Git configuration, credentials, templates and hooks. Private repositories can be checked out separately and installed as local packages through the existing developer workflow.
- The extension contract remains 2.0.0; existing workflow and connector packages retain that compatibility boundary.
- The public Homebrew formulas download pinned packages without GitHub credentials. Development repositories remain private.

Install or update:

```sh
brew tap qubicsdata/tap
brew install qubicsdata/tap/switchboard
switchboard ui
```

Homebrew 7 may ask for `brew trust qubicsdata/tap`. For an existing installation, finish active work and stop its service before `brew update` and `brew upgrade qubicsdata/tap/switchboard`. The [installation guide](https://github.com/qubicsdata/switchboard-releases/blob/main/docs/installation.md) covers standalone downloads and recovery. Installation does not start services or model work automatically.

Validation: 61 focused tests passed, with one existing release-only skip; type checking, production build, and the dependency audit passed. The About interface passed light/dark checks at 1440, 390 and 320 pixels with 18 accessibility audits. Each of the four installed standalone targets passed 20 checks, including the shipped HTTPS redirect policy with offline fixtures. Homebrew pours, payload verification, formula tests and coinstallation with Folio 1.1.2 passed on all four targets. See the accompanying evidence for exact identities and scope.

All packages were built locally with GitHub Actions disabled. macOS ARM64 and Linux ARM64 were tested natively; macOS x64 used Rosetta and Linux x64 used full-system QEMU TCG. macOS bottles target macOS 27. On this Mac, the stock `brew test` compiler precheck is unavailable because of the installed Command Line Tools version; the unchanged formula test blocks ran through Homebrew's test runner. Live provider accounts were not exercised.

This is an immutable GitHub release. Verify the release attestation with `gh release verify v2.0.2 --repo qubicsdata/switchboard-releases`; verify downloaded files against `SHA256SUMS` before use. GitHub's release attestation is separate from an independent publisher signature: the locally built packages remain unsigned and unnotarized, and this release does not use the separate signed-updater route.

Originally developed by [QubicsData](https://qubicsdata.com). Apache-2.0 with applicable NOTICE attribution; documentation retains CC-BY-4.0. Packages contain readable JavaScript and dependencies. No separate application development checkout or npm development package is published here. Report vulnerabilities [privately](https://github.com/qubicsdata/switchboard-releases/security/advisories/new).
