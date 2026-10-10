# Switchboard Privacy Notice

Version: 1 (2026-10-11)

Data handling for the private Switchboard 2.0.x releases by QubicsData.

## Local data

Switchboard runs on your computer. Its dashboard listens on the loopback interface. Project registrations, settings, tasks, messages, context indexes, audit records and local backups are stored in the selected Switchboard home and project folders. `switchboard about --paths` lists installation and data locations.

Owner/session secrets and connected account credentials are kept in macOS Keychain, Linux Secret Service, or the encrypted-file vault you configure. Other local records, logs and working files are not all encrypted by Switchboard; use operating-system disk protection and review backup locations. Agent CLIs keep their own data under their own policies.

## Network use

There is no built-in analytics, telemetry or automatic crash-report upload. Network use can occur through:

- Agent CLIs you install and sign in to, which send prompts and content to their providers.
- Connectors, MCP services and workflow actions you configure and authorize. Scheduled work can make these requests later without another interactive action, within its grants.
- Catalogs and authentication endpoints you explicitly configure, including metadata and credential exchange needed to connect services.
- GitHub and Homebrew when you install or update the private distribution. GitHub receives your authentication and ordinary request information such as IP address. Homebrew manages updates; the app does not run the standalone weekly updater in a Homebrew installation.
- Browser speech recognition when you use voice input; the browser may use its vendor’s speech service.

The optional standalone signed-updater tooling uses GitHub metadata after opt-in when that channel is configured. It is separate from this private Homebrew release.

## Sharing and diagnostics

Switchboard does not automatically send diagnostics or project data to QubicsData. Diagnostics exports are local files with redaction; inspect them before sharing because automatic redaction is not a substitute for reviewing sensitive content. Issues and discussions in the current private repositories are visible to collaborators with access. Do not attach credentials or private customer data.

Third-party agents and connected services apply their own terms and privacy practices. Review them before sending sensitive material. Package grants and agent security classes restrict host-mediated access; they do not replace operating-system account isolation.

## Control and removal

Disconnect accounts and revoke grants to stop future authorized connector work. Pause or remove schedules before leaving unattended work. Back up the selected home and project metadata before migration. Homebrew uninstall removes software and retains user data; deleting a workspace or credentials requires the app’s explicit data-removal tools. User project files and agent vendor data are separate.

For questions about material you chose to share with QubicsData, contact the repository administrators through the existing private collaboration channel. Any public service or repository launch will document its operational contacts and data handling before it opens.
