# Trademark policy

The Switchboard source code is licensed under the Apache License 2.0. The license covers the code, not the name. "Switchboard" and the Switchboard logo are trademarks of QubicsData. This policy explains how you may use them. It exists so that people can tell official builds from modified ones; it is not meant to stop you from using, changing or sharing the code.

## Allowed without asking

- Saying truthfully that your software works with, extends or is based on Switchboard ("a package for Switchboard", "based on Switchboard").
- Redistributing unmodified official releases under the Switchboard name.
- Referring to the project by name in articles, talks, tutorials, package indexes and comparisons.
- Using the unmodified logo to link to the project.
- Keeping the name in a fork's history, changelog and attribution notices.

## Needs written permission

- Using the name or logo as, or in, the name of a product, service, company or domain.
- Distributing modified builds under the Switchboard name or logo.
- Anything that suggests QubicsData endorses or supports your product or service.
- Changing the logo, or combining it with another mark.

Ask through a GitHub issue titled "Trademark request" in the private [installation and support repository](https://github.com/qubicsdata/switchboard-releases/issues/new), or contact QubicsData through [qubicsdata.com](https://qubicsdata.com).

## Forks

A fork that you distribute must use a different name and logo, and must not present itself as Switchboard. Start the rename in `packages/protocol/src/brand.ts`, update public prose and standalone installer declarations, and run the brand guard. Internal protocol identifiers are intentionally stable; review command and data-directory compatibility separately. Keep the LICENSE and NOTICE files, and say that your project is based on Switchboard.

## Vendor names

Switchboard mentions Claude Code, Codex, GitHub Copilot CLI and Gemini CLI only as plain-text compatibility statements, and uses no vendor logos. Not affiliated with or endorsed by Anthropic, OpenAI, GitHub or Google. Forks and packages should follow the same rule.
