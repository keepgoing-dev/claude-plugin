# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Purpose

This package is the Claude Code plugin distribution for KeepGoing. It is not a Node.js package and has no build step. It is a static bundle of configuration files consumed by the Claude Code plugin system.

It is published (or referenced) as `keepgoing-dev/claude-plugin` in the Claude Code plugin marketplace, and installed by users via:

```
/plugin marketplace add keepgoing-dev/claude-plugin
/plugin install keepgoing@keepgoing-dev
```

## Structure and Key Files

- `.claude-plugin/plugin.json` - Plugin identity and metadata consumed by the Claude Code plugin registry
- `.claude-plugin/marketplace.json` - Marketplace listing entry pointing back to `./`
- `.mcp.json` - Declares the MCP server for the plugin. Uses the `session` key (not `keepgoing`) to avoid naming conflicts. Runs `@keepgoingdev/mcp-server` via `npx`.
- `hooks/hooks.json` - Declares Claude Code lifecycle hooks (see below)
- `skills/*/SKILL.md` - One skill per subdirectory, each a standalone slash command under the `/keepgoing:` namespace

## Hooks

The plugin wires four Claude Code lifecycle events:

| Event | Command | Purpose |
|-------|---------|---------|
| `SessionStart` | `keepgoing momentum --hook` | Shows last checkpoint and momentum on session open |
| `PostToolUse` (Edit/Write/MultiEdit) | `keepgoing task-update --hook` | Tracks file edits |
| `PostToolUse` (Read/Grep/Glob/Bash/WebSearch) | `keepgoing heartbeat --hook` | Keeps session alive |
| `Stop` / `SessionEnd` | `keepgoing save --hook` | Auto-saves checkpoint on exit |

All hook commands invoke the `keepgoing` CLI (from `apps/cli` in the monorepo), not `npx @keepgoingdev/mcp-server`.

## Skills

Each skill in `skills/*/SKILL.md` maps to a `/keepgoing:<name>` slash command. Skills call MCP tools via the `mcp__plugin_keepgoing_session__*` prefix (the `session` MCP key).

| Skill | Slash command | Main MCP tool(s) called |
|-------|--------------|------------------------|
| `reentry` | `/keepgoing:reentry` | `get_momentum`, `get_reentry_briefing` |
| `briefing` | `/keepgoing:briefing` | `get_reentry_briefing`, `get_decisions`, `get_session_history`, `get_momentum` |
| `save` | `/keepgoing:save [message]` | `save_checkpoint` |
| `progress` | `/keepgoing:progress` | `get_session_history`, `get_momentum` |
| `hot` | `/keepgoing:hot` | `get_whats_hot` |
| `handoff` | `/keepgoing:handoff [target]` | `continue_on` |

`get_decisions` and `get_whats_hot` are Pro-only MCP tools.

## Naming Constraints

Three skill names were changed in v0.3.0 because they collide with native Claude Code commands:
- `resume` - renamed to `reentry` (native `/resume` switches sessions)
- `continue` - renamed to `handoff` (native `/continue` is an alias for `/resume`)
- `checkpoint` - renamed to `save` (native `/checkpoint` is an alias for `/rewind`)

The MCP server key must remain `session` (not `keepgoing`) - changed in v0.1.3 to avoid naming conflicts.

## Relationship to the Monorepo

This package has no runtime dependency on other monorepo packages. The MCP server it references (`@keepgoingdev/mcp-server`) is the published npm package built from `apps/mcp-server`. The hooks reference the `keepgoing` CLI built from `apps/cli`. Neither is imported directly - they are invoked as external processes.

Changes to MCP tool names or CLI command interfaces in the monorepo must be reflected here in skill `allowed-tools` lists and hook commands.
