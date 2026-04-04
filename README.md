# KeepGoing for Claude Code

Session memory for Claude Code. Auto-saves checkpoints, shows what you were working on when you return, and tracks progress across sessions.

## What it does

Once installed, KeepGoing runs automatically in the background:

- **Session start**: Shows your last checkpoint and what you were working on
- **While coding**: Tracks file edits and session activity
- **Session end**: Auto-saves a checkpoint so nothing is lost

## Installation

```
/plugin add keepgoing-dev/claude-plugin
/plugin install keepgoing
```

After installing, run `/keepgoing:setup` once to complete configuration (writes the rules file and statusline).

Full install guide: https://keepgoing.dev/setup/claude-plugin

## Slash commands

| Command | What it does |
|---------|-------------|
| `/keepgoing:resume` | Quick "where did I leave off?" briefing |
| `/keepgoing:briefing` | Full context reconstruction for a big session |
| `/keepgoing:checkpoint [message]` | Save a checkpoint manually with a custom message |
| `/keepgoing:progress` | Standup-ready progress summary across sessions |
| `/keepgoing:hot` | See what's actively in-progress |
| `/keepgoing:continue [target]` | Export context to another AI tool (chatgpt, gemini, copilot, claude, general) |
| `/keepgoing:setup` | Complete setup (rules file, statusline) |

## Upgrading from manual setup

If you previously configured KeepGoing via `keepgoing init` or `setup_project`, your `settings.json` already has KeepGoing hooks. The plugin provides those hooks too, so you'll have duplicates.

To clean up: remove the KeepGoing hook entries from your `.claude/settings.json` or `~/.claude/settings.json`, then run `/keepgoing:setup` to restore the rules file and statusline.

## MCP tools

With the plugin installed, Claude has direct access to all KeepGoing tools during your session:

- `save_checkpoint` - Save the current state
- `get_reentry_briefing` - Get structured context
- `get_momentum` - Current session and branch status
- `get_session_history` - Full session history
- `get_decisions` - Key architectural decisions (Pro)
- `get_whats_hot` - Recently active files and branches
- `continue_on` - Export context for other AI tools
- `setup_project` - Configure KeepGoing

## Pro

Some features (decisions tracking, detailed briefings) require a KeepGoing Pro license. Visit [keepgoing.dev](https://keepgoing.dev) to learn more.
