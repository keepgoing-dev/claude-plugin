---
name: setup
description: Use when the user says "set up keepgoing", "configure keepgoing", "keepgoing setup", "install keepgoing rules", or wants to verify/repair their KeepGoing configuration after installing the plugin.
allowed-tools: ["mcp__plugin_keepgoing_session__setup_project"]
---

The user wants to complete their KeepGoing setup after installing the plugin.

The plugin already handles hooks automatically - do NOT write hooks again. This skill handles the two things the plugin cannot do on its own:

1. **Rules file**: Creates `.claude/rules/keepgoing.md` so Claude knows to call `save_checkpoint` after completing work.
2. **Statusline**: Adds the `[KG]` statusline command to `settings.json` so current session state shows in the Claude Code status bar.

Call `mcp__plugin_keepgoing_session__setup_project` with:
- `sessionHooks`: false (hooks are already provided by the plugin - skip to avoid duplicates)
- `claudeMd`: true (write the rules file)
- `scope`: "user" for global setup across all projects, or "project" for this project only. Default to "user" unless the user specifies otherwise.

After the tool responds, tell the user:
- What was configured (rules file location, statusline)
- That hooks were intentionally skipped because the plugin provides them
- To restart Claude Code if the statusline doesn't appear immediately

If the user previously ran `keepgoing init` or `setup_project` manually (before installing the plugin), their `settings.json` already has KeepGoing hooks. Those duplicate hooks won't cause data loss (a 2-minute dedup prevents double checkpoints), but they will fire twice on every event. Advise them to remove the hooks from `settings.json` manually, or uninstall and reinstall the plugin after removing the manual hooks.
