# Changelog

## 0.3.0

- Rename skills to avoid collisions with native Claude Code commands:
  - `resume` - `reentry` (native `/resume` switches sessions)
  - `continue` - `handoff` (native `/continue` is an alias for `/resume`)
  - `checkpoint` - `save` (native `/checkpoint` is an alias for `/rewind`)

## 0.2.0

- Update to match MCP server 0.10.0 with structural decision detection

## 0.1.3

- Rename MCP server key from `keepgoing` to `session` to avoid naming conflicts
- Update all skill tool references to match new MCP server key
- Add concise checkpoint text guidance in checkpoint skill

## 0.1.2

- Add `marketplace.json` for plugin discovery
- Update install commands to use `/plugin marketplace add` and `/plugin install keepgoing@keepgoing-dev`

## 0.1.1

- Switch plugin repository from `keepgoing-dev/community` to `keepgoing-dev/claude-plugin`

## 0.1.0

Initial release of the KeepGoing Claude Code plugin.

- Auto-configures session hooks (SessionStart, Stop, SessionEnd, PostToolUse) on install
- Registers `@keepgoingdev/mcp-server` as an MCP server so all 12 KeepGoing tools are available mid-session
- Adds 7 slash commands under the `/keepgoing:` namespace: `reentry`, `briefing`, `save`, `progress`, `hot`, `handoff`, `setup`
- Available via `/plugin marketplace add keepgoing-dev/claude-plugin` then `/plugin install keepgoing@keepgoing-dev`
