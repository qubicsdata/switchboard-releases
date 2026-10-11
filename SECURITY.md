# Security policy

## Report a vulnerability privately

Use [GitHub private vulnerability reporting](https://github.com/qubicsdata/switchboard-releases/security/advisories/new). Do not post security details, credentials, or private project data in public issues. Include the application version, operating system and architecture, the affected feature, expected and observed behavior, and a minimal example using synthetic data.

This repository is public. Private reports are visible to the repository's security maintainers and invited collaborators, not ordinary repository visitors. Test only installations and accounts you control.

## Scope and support

Official Switchboard packages, installers, and bundled first-party components are in scope. The latest patch release receives security fixes; install updates from this repository's Releases page or the QubicsData public Homebrew tap. Third-party agents, tools, and extensions have their own maintainers and permissions.

Switchboard runs with the operating-system user's privileges. Use separate operating-system accounts or isolated environments for mutually untrusted users, agents, and projects. Application permissions do not sandbox arbitrary native programs with the same account's filesystem access. Keep local application ports on loopback; do not expose them through a reverse proxy, public tunnel, or port forwarding.

## Release integrity

Download assets over HTTPS from this repository. Verify the selected archive and any separately downloaded bootstrap against its published SHA-256 checksum before extracting or running it. A checksum confirms correspondence with the manifest; it is not an independent publisher signature. These packages are not Apple-notarized and do not claim the separate signed-updater distribution route.

GitHub secret scanning and push protection are enabled. The default branch is protected against force pushes and deletion, and version tags against modification and deletion. GitHub Actions is disabled; packages are built and tested locally. Private vulnerability reporting is enabled.

Release immutability was enabled after Folio 1.1.1 and Switchboard 2.0.1 were published. It applies to future releases, not those existing releases. Maintainers must assemble and verify all assets in a draft before publishing a new immutable release. Correct a released package with a new version; preserve old version identities.

## Handling reports and compromised releases

Maintainers investigate in the private application development repositories. Keep patches and sensitive discussion private until a corrected package or mitigation is available. Coordinate public disclosure with the reporter and credit them according to their preference. This project does not offer a bug bounty.

If a release or publishing credential may be compromised, report it through the private channel above. Maintainers should revoke the affected credential, review account access and release/download history, publish a security advisory with affected versions and verified replacement hashes, and ship a new corrected version. Do not silently replace previously published assets. Restore trust through a verified maintainer account and the published advisory, not through a checksum uploaded by a suspected compromised account.
