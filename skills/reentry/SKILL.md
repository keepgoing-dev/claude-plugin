---
name: reentry
description: Use when the user says "where did I leave off", "what was I working on", "pick up where I left off", "what's the status", or opens a project after a break. Gives a quick re-entry briefing from KeepGoing session data.
allowed-tools: ["mcp__plugin_keepgoing_session__get_momentum", "mcp__plugin_keepgoing_session__get_reentry_briefing", "mcp__plugin_keepgoing_session__get_decisions"]
---

The user wants a quick re-entry briefing for this project.

1. Call `mcp__plugin_keepgoing_session__get_momentum` to get the current session state and recent activity.
2. Call `mcp__plugin_keepgoing_session__get_reentry_briefing` to get structured context (last checkpoint, next step, blockers).
3. Call `mcp__plugin_keepgoing_session__get_decisions` with `limit: 3` to check for recent decisions on the current branch.
4. Respond with a concise welcome: what was last worked on, the suggested next step, and any blockers. Keep it to 3-5 lines - this is a quick orientation, not a deep dive.
   - If decisions are returned, append one compact line: "Decisions on this branch: N (categories) - review with get_decisions before touching relevant areas." Omit this line if no decisions are returned (free user or none exist).

If no session data exists yet, tell the user KeepGoing will start tracking once they make their first edit.
