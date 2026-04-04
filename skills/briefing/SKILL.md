---
name: briefing
description: Use when the user wants a comprehensive context reconstruction before a big session - "full briefing", "catch me up completely", "full context", "what decisions were made", or returning after a long break and needing complete context.
allowed-tools: ["mcp__plugin_keepgoing_keepgoing__get_reentry_briefing", "mcp__plugin_keepgoing_keepgoing__get_decisions", "mcp__plugin_keepgoing_keepgoing__get_session_history", "mcp__plugin_keepgoing_keepgoing__get_momentum"]
---

The user wants a comprehensive context briefing - more thorough than `/keepgoing:resume`.

1. Call `mcp__plugin_keepgoing_keepgoing__get_reentry_briefing` to get the structured briefing.
2. Call `mcp__plugin_keepgoing_keepgoing__get_decisions` to surface key architectural and design decisions.
3. Call `mcp__plugin_keepgoing_keepgoing__get_session_history` to get recent session history.
4. Call `mcp__plugin_keepgoing_keepgoing__get_momentum` for current branch and task context.

Synthesize all results into a complete briefing covering:
- Current state and what was last worked on
- Key decisions that shaped the current direction
- Recent session history across branches
- Suggested next step with context for why

This is the "full reconstruction" mode - the user is about to start a substantial work block and needs complete context. Be thorough.
