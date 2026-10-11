# Switchboard

An extensible coordinator for agents, tools, context, and business workflows.

Originally developed by [QubicsData](https://qubicsdata.com). Licensed under [Apache-2.0](LICENSE).

This public repository provides ready-to-install Switchboard packages for macOS and Linux. Application development repositories remain private and are maintained separately.

## Install and open

The [standalone installation guide](docs/installation.md#standalone-installer) covers public downloads, checksum verification, and installation with the bundled runtime. No GitHub account is required.

### Homebrew

The Homebrew tap is public. Install without GitHub credentials:

```sh
brew tap qubicsdata/tap https://github.com/qubicsdata/homebrew-tap.git
brew trust qubicsdata/tap
brew install qubicsdata/tap/switchboard
switchboard ui
```

`brew trust` is available in Homebrew 7; earlier versions may not need this step. Public downloads use Homebrew’s standard HTTPS downloader with pinned SHA-256 hashes. Read access to the application development repository is not required for installation.

If an older installation appears first on PATH, use `$(brew --prefix)/bin/switchboard ui` to open the Homebrew version. Installation does not launch services or move existing workspaces.

## Packages

The [v2.0.1 release](https://github.com/qubicsdata/switchboard-releases/releases/tag/v2.0.1) contains standalone archives and Homebrew bottles for macOS and glibc Linux, on ARM64 and x64. Runtimes are bundled. SHA-256 checksums, license notices, source/build provenance and validation evidence accompany the packages.

The Homebrew macOS bottles target macOS 27. Other supported macOS versions can use the matching standalone archive, subject to its runtime requirements. macOS ARM64 and Linux ARM64 checks run natively; x64 checks use Rosetta and full-system QEMU TCG. Exact platform and test scopes are recorded in each release's evidence.

Download installers from the release's Assets list. The [standalone installation guide](docs/installation.md#standalone-installer) explains checksum verification and use of the bundled runtime. GitHub's automatically generated repository archives contain these distribution documents. Development source exports, wheels, source distributions and npm development packages are not installation assets in this channel. Packaged application code can remain readable, including Python and JavaScript; this distribution does not promise obfuscation.

Agent CLIs and provider sign-ins are separate. Run `switchboard doctor` to inspect available integrations. Headless installations need their configured vault unlocked; see the [installation guide](docs/installation.md). [Privacy notice](PRIVACY.md).

## Update and remove

Back up your workspace and finish active work before upgrading. Stop the running application or its Homebrew service, then run:

```sh
brew update
brew upgrade qubicsdata/tap/switchboard
switchboard ui
```

Optional background service: `brew services start qubicsdata/tap/switchboard`. Stop it with `brew services stop qubicsdata/tap/switchboard` before upgrading.

`brew uninstall switchboard` removes the application and retains workspace/project data. Existing standalone installations remain separate; their transactional installers and data locations are documented inside the downloaded packages.

## Attribution and redistribution

Switchboard is originally developed by QubicsData. Apache-2.0 permits modification and redistribution, including commercial use, subject to its terms. Redistributed copies must include the license and preserve applicable attribution notices from [NOTICE](NOTICE). Mark modified files as required by the license. Documentation copied into `docs/` retains its [CC-BY-4.0 license](docs/LICENSE). Third-party components retain their own licenses and notices.

The About screen identifies QubicsData in our official builds. This is an informational credit; it adds no visible-credit or advertising requirement to Apache-2.0. Product names and logos have [separate trademark terms](TRADEMARKS.md). Prior Apache-licensed releases and their grants remain unchanged.

## Support

Use [this repository's issues](https://github.com/qubicsdata/switchboard-releases/issues) for installation problems and bug reports. Include the application version, operating system, architecture, and steps to reproduce. Review diagnostics before sharing; omit credentials and private project data.

Report security vulnerabilities through [private vulnerability reporting](https://github.com/qubicsdata/switchboard-releases/security/advisories/new), rather than a public issue. See the [security policy](SECURITY.md).

All packages are built locally. GitHub Actions is disabled. Earlier releases and development histories are preserved in their original repositories.
