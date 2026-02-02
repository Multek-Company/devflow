# devflow-frontend-design

A Claude Code plugin that improves frontend code quality by enforcing your project's design system. Includes MCP integrations for database access, documentation lookup, browser testing, and DevTools debugging.

## Features

### Frontend Design Skill
Automatically activates when building UI components. Reads your project's `design-system.md` file and ensures all frontend code follows defined tokens, spacing, colors, typography, and component patterns.

### MCP Integrations

| Server | Purpose |
|--------|---------|
| **Postgres** | Query the database for debugging and development |
| **Context7** | Up-to-date documentation for libraries and frameworks |
| **Playwright** | Browser-based UI testing and navigation |
| **Chrome DevTools** | Access network tab, console, and browser debugging |

## Installation

Add as a plugin directory:

```bash
claude --plugin-dir /path/to/devflow-frontend-design
```

## Prerequisites

### Design System File

Create a `design-system.md` in your project root (or `docs/`). See `skills/frontend-design/references/design-system-template.md` for a template.

### Environment Variables (Postgres MCP)

Configure database access using **either** method:

**Option A — Connection string:**
```bash
export DATABASE_URL="postgresql://user:password@localhost:5432/mydb"
```

**Option B — Individual variables:**
```bash
export PGHOST="localhost"
export PGPORT="5432"
export PGDATABASE="mydb"
export PGUSER="user"
export PGPASSWORD="password"
```

### NPM Packages (auto-installed)

The MCP servers install automatically via `npx`:
- `@modelcontextprotocol/server-postgres`
- `@upstash/context7-mcp`
- `@anthropic/mcp-server-playwright`
- `@anthropic/mcp-server-chrome-devtools`

## Usage

Once installed, the plugin works automatically:

- **Frontend skill** activates when you ask to build, style, or modify UI components
- **MCP servers** are available as tools — use `/mcp` to verify they're connected
- Ask Claude to "check the design system" or "follow the design tokens" to explicitly trigger the skill

## Plugin Structure

```
devflow-frontend-design/
├── .claude-plugin/
│   └── plugin.json
├── .mcp.json
├── skills/
│   └── frontend-design/
│       ├── SKILL.md
│       ├── references/
│       │   ├── design-system-template.md
│       │   └── component-checklist.md
│       └── examples/
│           └── design-system-example.md
└── README.md
```
