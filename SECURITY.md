# Security policy

## Reporting a vulnerability

This repository is private. Report security problems to the QubicsData repository administrators through the existing private collaboration channel. A repository issue is visible to everyone with repository access, so share a minimal description there only when that audience is appropriate; send sensitive details directly to an administrator. Do not include credentials or private project data. Public vulnerability reporting will be configured before public access is enabled.

Include what you found, the Switchboard version (`switchboard --version`), your operating system, and the steps to reproduce. Do not include real credentials or other people's data.

## What to expect

- We acknowledge your report within **5 business days**.
- For critical issues we ship a fix or a mitigation within **30 days** of acknowledgement. Other issues are scheduled by severity.
- We publish a GitHub security advisory together with the fix, and credit you unless you ask us not to.
- We keep you informed while we work on it, and may ask you to check the fix.

## Supported versions

Only the latest minor release receives security fixes. Homebrew installations update with `brew update` and `brew upgrade switchboard`.

## Scope

In scope are official Switchboard binaries and installers, bundled first-party extension packages, and the source/build tools from which they are produced. Packages are built locally; GitHub Actions is disabled for this distribution.

Out of scope are user-installed agent CLIs and third-party packages (report to their authors), and attacks requiring control of the operating-system user account. Switchboard permissions do not replace operating-system account isolation; see the [privacy notice](PRIVACY.md).

## How fixes are made

Maintainers develop fixes in a private security advisory and temporary private fork, release the fix, then publish an advisory. Security-sensitive changes require maintainer review. There is no bug bounty.

## Safe harbour

We will not pursue legal action for research that follows this policy:

- you act in good faith;
- you avoid privacy violations and data destruction;
- you test only against your own installations and accounts;
- you give us reasonable time to fix the issue before disclosure.

## Appendix: key compromise runbook

If a Switchboard signing key may be compromised:

1. Report it as above, marked **critical**.
2. The maintainers revoke the key: release keys through a statement signed by the offline root key (PR-D18), and catalog keys through the revocation list.
3. A new release ships with the replacement key and a security notice.
4. Users see the security notice on their next update check.

The extensions repository's catalog runbook covers catalog keys in detail.
