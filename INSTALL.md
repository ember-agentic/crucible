# Crucible Installation Guide

Crucible runs on macOS, Linux, and Windows. The installer handles everything except the two things only you can arrange.

## Prerequisites

1. **Anthropic account** — Crucible runs on Claude Code, which authenticates against Anthropic. Sign up at [console.anthropic.com](https://console.anthropic.com/) if you don't already have one. You'll log in during the `claude login` step after install.
2. **GitHub collaborator access** — Releases live in a private GitHub repo. When access is granted you'll receive a collaborator invitation by email. **Accept it before running the installer**, otherwise the download will fail with 404.

The installer takes care of the rest: VS Code, Node.js, Homebrew (on macOS), and the GitHub CLI are all installed automatically if missing.

## Install — pick your platform

### macOS — double-click `.pkg`

1. Download [`Crucible-0.1.0-alpha.pkg`](https://github.com/ember-agentic/crucible-releases/releases/download/v0.1.0-alpha/Crucible-0.1.0-alpha.pkg).
2. Double-click. Signed and notarized for macOS Sequoia — no Gatekeeper warnings.

### Windows — double-click `Setup.exe`

1. Download [`Crucible-0.1.0-alpha-Setup.exe`](https://github.com/ember-agentic/crucible-releases/releases/download/v0.1.0-alpha/Crucible-0.1.0-alpha-Setup.exe).
2. Double-click. Windows SmartScreen may show a warning (alpha builds are not yet code-signed) — click **More info → Run anyway**.

### Linux — `.deb` or `.rpm`

```bash
# Ubuntu / Debian
sudo dpkg -i crucible_0.1.0-alpha_amd64.deb

# Fedora / RHEL
sudo rpm -i crucible-0.1.0-alpha.x86_64.rpm
```

Or download the file from the [release page](https://github.com/ember-agentic/crucible-releases/releases/tag/v0.1.0-alpha) and double-click — your desktop's package manager will open the install dialog.

### Terminal (any platform)

If you already have the GitHub CLI installed and authenticated, skip the GUI installer:

```bash
# macOS / Linux
gh release download v0.1.0-alpha --repo ember-agentic/crucible-releases --pattern install.sh -O - | bash
```

```powershell
# Windows PowerShell
gh release download v0.1.0-alpha --repo ember-agentic/crucible-releases --pattern install.ps1
.\install.ps1
```

If `gh` isn't on your machine, the installer will install it for you.

## After install

```bash
claude login              # opens your browser to authenticate with Anthropic
code ~/workspaces/default # open your workspace in VS Code
```

Click a persona in the Crucible sidebar to start. See [QUICKSTART.md](QUICKSTART.md) for a walkthrough of your first session.

## System requirements

- **macOS** 11+ (arm64 or x64), **Linux** (x64, arm64), or **Windows** 10+ (x64)
- **Disk** ~500 MB for installation + workspace
- **Memory** 4 GB minimum

Node.js 20+ is installed by the installer on whichever platform you use.

## Install from source (advanced, for contributors)

Source access is granted separately. With access:

```bash
git clone https://github.com/ember-agentic/crucible.git
cd crucible
cd mcp-workflow-server && npm install && cd ..
node scripts/init-workspace.js my-project
code workspaces/my-project
bash scripts/build-and-install.sh   # build and install the VS Code extension locally
```

## Uninstalling

Delete the Crucible installation directory and your workspaces. No system-level changes are made during installation that need separate cleanup.
