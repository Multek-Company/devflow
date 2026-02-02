# devflow - plugin

A Claude Code plugin that improves frontend code quality by enforcing your project's design system. Includes MCP integrations for database access, documentation lookup, browser testing, and DevTools debugging.

## Features

### Skills

| Skill | Trigger | Purpose |
|-------|---------|---------|
| **Frontend Design** | Building, styling, or modifying UI components | Reads your project's design system and ensures all frontend code follows defined tokens, spacing, colors, typography, and component patterns |
| **Read Project Docs** | Planning or implementing complex features | Checks `.project-docs/` for architecture and module documentation before exploring source files |

### Commands

| Command | Purpose |
|---------|---------|
| `/devflow:create-tailwind-theme` | Extract a Tailwind CSS theme (`@theme`, `:root`, `.dark`) from screenshots |
| `/devflow:create-design-system` | Interactive Q&A that builds a comprehensive `design-system.md` |

### MCP Integrations

| Server | Purpose |
|--------|---------|
| **Postgres** | Query the database for debugging and development |
| **Context7** | Up-to-date documentation for libraries and frameworks |
| **Playwright** | Browser-based UI testing and navigation |
| **Chrome DevTools** | Access network tab, console, and browser debugging |

## Installation

### From marketplace (recommended)

```
/plugin marketplace add Multek-Company/devflow
/plugin install devflow@devflow
```

Then restart Claude Code.

### From local path

If you have the repo cloned locally:

```
/plugin marketplace add ./path/to/devflow
/plugin install devflow@devflow
```

## Prerequisites

### Design System File

Create a `design-system.md` in your project root (or `.project-docs/`). You can generate one using:

- `/devflow:create-design-system` — interactive Q&A to build a design system from scratch
- `/devflow:create-tailwind-theme` — extract theme from screenshots of an existing interface

See `skills/frontend-design/references/design-system-template.md` for a template.

### Project Documentation (optional)

Create a `.project-docs/` directory in your project root with markdown files explaining your architecture, modules, conventions, and integrations. The **Read Project Docs** skill will use these when planning complex features.

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

- **Frontend Design skill** activates when you ask to build, style, or modify UI components
- **Read Project Docs skill** activates when planning or implementing complex features
- **MCP servers** are available as tools — use `/mcp` to verify they're connected
- Use `/devflow:create-tailwind-theme` to extract a theme from screenshots
- Use `/devflow:create-design-system` to build a design system through guided Q&A

## Plugin Structure

```
devflow/                          # marketplace repo
├── .claude-plugin/
│   └── marketplace.json
├── plugins/
│   └── devflow/
│       ├── .claude-plugin/
│       │   └── plugin.json
│       ├── .mcp.json
│       ├── commands/
│       │   ├── create-design-system.md
│       │   └── create-tailwind-theme.md
│       └── skills/
│           ├── frontend-design/
│           │   ├── SKILL.md
│           │   ├── references/
│           │   │   ├── design-system-template.md
│           │   │   └── component-checklist.md
│           │   └── examples/
│           │       └── design-system-example.md
│           └── read-project-docs/
│               └── SKILL.md
└── README.md
```
