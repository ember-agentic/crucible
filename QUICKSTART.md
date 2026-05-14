# Crucible Quick Start Guide

## Prerequisites

1. **VS Code** — [Download](https://code.visualstudio.com/)
2. **Claude Code** — Install: `npm install -g @anthropic-ai/claude-code`
3. **Anthropic account** — Sign up at [console.anthropic.com](https://console.anthropic.com)
4. **Node.js 20+**
5. **Git identity configured**:
   ```bash
   git config --global user.name "Your Name"
   git config --global user.email "you@example.com"
   ```

### One-time setup

```bash
claude login    # Opens browser to authenticate with Anthropic
```

## Your First Session

### 1. Open your workspace in VS Code

After installation, open your workspace:

```bash
code workspaces/my-first-project
```

### 2. Approve the MCP connection

VS Code opens and Claude Code detects the `.mcp.json` file. Click **Allow** to approve the MCP server connection. The Crucible sidebar appears in the activity bar.

### 3. Open a persona

Click **Planning** in the Crucible sidebar. This opens a Claude Code terminal with the planning persona's specialized instructions and access to 583 workflow tools.

### 4. Describe your project

Tell the planning persona what you want to build:

```
I want to build a task management API with user authentication,
CRUD operations, and a React frontend. Please research this
externally and create a comprehensive plan with tasks to get started.
```

The planning persona will:
- Research best practices and technology options
- Create a project plan
- Break the work into tasks assigned to the right personas

### 5. Work through the personas

Once planning creates tasks, switch to the persona that has work to do by clicking it in the Crucible sidebar. Each persona:

- Sees their assigned tasks
- Has domain-specific instructions
- Reads from and writes to `shared-docs/` so other personas can see the work
- Hands off completed work to the next persona in the pipeline

Typical flow: **Planning > Requirements > Design > Implementation > Testing > Deployment**

## How Personas Work

Each persona runs as a separate Claude Code session. When you click a persona in the sidebar:

1. A terminal opens in `personas/persona-<name>/`
2. Claude Code starts with that persona's `CLAUDE.md` instructions
3. The MCP server connects with 583 workflow tools
4. The persona reads shared documents and creates artifacts for other personas

### Key directories in your workspace

```
my-project/
  .crucible/           # Database and configuration
  personas/            # 13 persona directories (each has CLAUDE.md + .mcp.json)
  shared-docs/         # Shared project documentation
    requirements/      # User stories (written by requirements persona)
    architecture/      # Architecture docs (written by design persona)
    decisions/         # ADRs (written by design persona)
  src/                 # Your application source code
  test/                # Your test files
```

### Document templates

Each `shared-docs/` subdirectory contains a `_template.md` file. Personas read the template before creating documents, ensuring consistent structure with YAML frontmatter.

## Creating Additional Workspaces

```bash
node scripts/init-workspace.js another-project
code workspaces/another-project
```

Each workspace has its own database, personas, and shared documents.

## Troubleshooting

### MCP Server Not Connecting
1. Check that `.mcp.json` exists in your workspace root
2. Restart VS Code
3. Check the log: `cat <workspace>/.crucible/mcp-server.log`

### Claude Code Not Authenticated
Run `claude login` in your terminal.

### "Needs Approval" Stuck in Sidebar
Restart the persona session — click Stop, then click the persona again.

### Git Errors on Task Completion
Ensure git identity is configured:
```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```
