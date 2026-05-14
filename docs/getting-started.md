# Getting started with Crucible Alpha.

What to expect, how to work with agents, and how to get the most out of the system.

## What Crucible Alpha is

Crucible Alpha is an early release that came out of a couple weeks of intensive building. It works, it provides real productivity gains, and it represents **only the tip of the iceberg** of what's possible with structured AI development.

It's a **best-effort system**. The agents do a good job of following the workflow, creating documents, and managing tasks -- but it's not 100% automated. You are an active participant, not a passive observer.

> **Set your expectations:** Think of each agent as a capable but new team member. They'll do good work, but they need direction. You'll sometimes need to remind them to create tasks, update documents, or search the knowledge base. This is by design -- Crucible Pro will lock this down with enforced structure and quality gates.

## Prerequisites

> Two things you arrange yourself. The installer takes care of everything else -- including VS Code, Node.js, Homebrew (on macOS), and the GitHub CLI.

### 1. Anthropic account

Crucible uses Claude Code, which requires an Anthropic account. Sign up at [console.anthropic.com](https://console.anthropic.com/). You'll authenticate during the `claude login` step after install.

### 2. GitHub collaborator access

Crucible releases live in a private GitHub repo. Once your access is granted, you'll receive a collaborator invitation by email. **Accept it before running the installer** -- otherwise the download will fail with a 404.

## Install

Pick the path that matches your platform.

### macOS -- double-click `.pkg`

1. Download `Crucible-0.1.0-alpha.pkg` from the release page
2. Double-click and follow the installer (signed and notarized for macOS Sequoia -- no Gatekeeper warnings).

### Windows -- double-click `Setup.exe`

1. Download `Crucible-0.1.0-alpha-Setup.exe` from the release page
2. Double-click. Windows SmartScreen may show a warning -- click "More info" then "Run anyway".

### Linux -- `.deb` or `.rpm`

- Ubuntu / Debian: `sudo dpkg -i crucible_0.1.0-alpha_amd64.deb`
- Fedora / RHEL: `sudo rpm -i crucible-0.1.0-alpha.x86_64.rpm`

### Terminal (any platform)

```bash
# macOS / Linux (requires gh CLI)
gh release download v0.1.0-alpha --repo ember-agentic/crucible-releases --pattern install.sh -O - | bash
```

```powershell
# Windows PowerShell
gh release download v0.1.0-alpha --repo ember-agentic/crucible-releases --pattern install.ps1
.\install.ps1
```

The installer handles everything -- Node.js, VS Code extension, workspace setup, and all 13 personas.

### After install

1. `claude login` -- opens your browser to authenticate with Anthropic
2. `code ~/workspaces/default` -- open your workspace in VS Code
3. Click a persona in the Crucible sidebar to start

## How to work with agents

Crucible gives you specialized AI personas -- requirements, design, architecture, implementation, testing, security, DevOps, and more. Each one has a full chat interface through Claude Code and access to specialized MCP tools.

**Treat each agent like a person.** Ask questions. Give feedback. Push back on decisions you disagree with. The agents work best when you're actively guiding them, not just watching.

> **The key things you need to do:**

- **Create tasks** -- tell the agent what you want built, and ask it to create a Crucible task using the MCP tools
- **Remind agents to use MCP functions** -- sometimes the LLM will try to do things manually instead of using Crucible's tools. Nudge it: "use the Crucible tools to create that task" or "search the knowledge base first"
- **Ensure documents get created** -- requirements, designs, and architecture docs should be written as part of the workflow. If the agent skips this, ask for it
- **Complete tasks** -- when work is done, make sure the agent marks the task as complete with proper documentation
- **Search before creating** -- remind agents to search the knowledge base for existing work before starting something new
- **Review and sign off** -- the quality gates are there for a reason. Review what agents produce before moving on

## Tips for getting the most out of it

> **Start small.** Pick one feature or user story. Walk through the full workflow -- requirements, design, implementation, testing -- before scaling up. You'll learn the system faster this way.

> **Use the knowledge base.** The more documents and artifacts you create, the smarter the system gets. Prior requirements inform future design. Past architecture decisions guide new implementation. Don't skip the docs.

> **Be specific with agents.** Instead of "build a login page," try "create a requirements doc for user authentication with OAuth support, then create an implementation task." The more structure you give, the better the output.

> **Check the task board.** The VS Code sidebar shows all tasks grouped by status and persona. Use it to track what's in progress, what's blocked, and what's done.

> **Don't fight the workflow.** Requirements before design. Design before implementation. Implementation before testing. The agents work best when you follow the natural flow from intent to ship.

## What to expect

Crucible Alpha will sometimes surprise you with how well it handles complex multi-file development. It will also sometimes forget to update a task or skip a documentation step. That's normal at this stage.

The system is **genuinely useful** -- it was used to build significantly more complex systems on top of itself. But it requires an engaged human operator who understands what good software development looks like.

**Crucible Pro** is in active development and will address these gaps with enforced process structure, locked-in quality gates, multi-LLM support, and predictable file organization. Alpha is the foundation.
