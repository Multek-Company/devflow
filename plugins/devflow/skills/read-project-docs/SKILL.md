---
name: read-project-docs
description: This skill should be used when the user asks to "plan a feature", "implement a complex feature", "architect a solution", "design a new module", or any task that involves understanding how existing parts of the codebase work before writing code. Reads project documentation from .project-docs/ to build context efficiently instead of repeatedly reading source files.
version: 0.1.0
---

# Read Project Docs

Before planning or implementing complex features, check the `.project-docs/` directory for existing documentation that explains how parts of the codebase work.

## Why This Matters

Source code tells you *what* the code does, but project docs explain *why* it's structured that way, how modules connect, what conventions to follow, and what pitfalls to avoid. Reading docs first saves repeated file exploration and produces better plans.

## Process

### 1. Discover Available Docs

Before starting any complex feature plan:

1. **List `.project-docs/`** at the project root to see what documentation exists
2. **Scan filenames and subdirectories** to identify docs relevant to the feature area
3. **Read the relevant docs** to understand architecture, patterns, conventions, and integration points

### 2. Use Docs to Inform Planning

When planning a feature:

- **Check for architecture docs** — understand the high-level structure before diving into files
- **Check for module/domain docs** — learn how specific subsystems work (auth, billing, data pipeline, etc.)
- **Check for convention docs** — coding standards, naming patterns, folder structure rules
- **Check for API docs** — endpoint contracts, data shapes, error handling patterns
- **Check for integration docs** — how external services are connected, what SDKs are used, configuration patterns

### 3. Reference Docs in Your Plan

When presenting a plan to the user:

- Cite relevant docs that informed your decisions (e.g. "Per `.project-docs/auth.md`, the project uses JWT with refresh tokens")
- Flag when a planned change might conflict with documented conventions
- Note when docs are outdated or missing for the area being changed

## When to Read Docs

| Situation | Action |
|---|---|
| Planning a new feature | Read all potentially related docs before proposing an approach |
| Modifying an existing module | Read that module's doc if it exists |
| Integrating with an external service | Check for integration/API docs |
| Unsure about project conventions | Check for convention/standards docs |
| Repeated file exploration isn't yielding clarity | Step back and check if a doc explains the big picture |

## When Docs Don't Exist

If `.project-docs/` doesn't exist or lacks docs for the relevant area:

- Proceed with normal codebase exploration
- After understanding the area through code reading, **suggest to the user** that a doc would be valuable for that module — but don't create one unless asked

## Doc Format Expectations

Docs in `.project-docs/` can be any format but are typically markdown. They may include:

- Architecture overviews and diagrams (as text descriptions)
- Module-specific guides explaining data flow and key abstractions
- API references and endpoint documentation
- Convention and style guides
- Integration guides for third-party services
- Decision records (ADRs) explaining why certain approaches were chosen
