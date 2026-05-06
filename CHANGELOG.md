# Changelog

## 0.6.1

- Update to match MCP server 0.14.3 and CLI 2.8.3 with session deactivation support

## 0.6.0

- Update to match MCP server 0.14.2 and CLI 2.8.0 with OpenCode setup support
- Add OpenCode plugin hooks so Claude Code installs the new plugin flow alongside MCP configuration

## 0.5.0

- Update to match MCP server 0.14.2 and CLI 2.5.0 with decisions surfaced at session start
- Briefing skill now frames decisions as session constraints so the AI treats them as guardrails, not just history
- Reentry skill now surfaces active decisions during re-entry so past choices are immediately visible

## 0.4.4

- Update to match MCP server 0.14.1: project registry now filters out temp dirs and common home subdirectories

## 0.4.3

- Update to match MCP server 0.13.0: `save_checkpoint` now records checkpoint time for statusline display

## 0.4.2

- Refresh documentation and README

## 0.4.1

- Update hook commands from `npx -y @keepgoingdev/mcp-server` to `keepgoing` CLI for faster startup

## 0.4.0

- Update to match MCP server 0.12.0 with GlobalDatabase, BYO API key, and improved decision detection
- Auto-trigger background refinement after decision detection when an API key is configured
- Show decision count teaser for free users

## 0.3.2

- Remove deprecated setup skill reference
- Clean up README documentation

## 0.3.1

- Update to match MCP server 0.11.0 with staleness detection and framework message filtering

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
