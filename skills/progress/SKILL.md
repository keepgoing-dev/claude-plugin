---
name: progress
description: Use when the user needs a standup update, sprint review summary, "what did I do this week", "summarize my progress", "catch me up for standup", or wants to see recent development activity across sessions.
allowed-tools: ["mcp__plugin_keepgoing_session__get_session_history", "mcp__plugin_keepgoing_session__get_momentum"]
---

The user needs a progress summary for a standup, sprint review, or personal review.

1. Call `mcp__plugin_keepgoing_session__get_session_history` with a higher limit (20) for broader session coverage.
2. Call `mcp__plugin_keepgoing_session__get_momentum` for current branch context.

Synthesize a progress summary grouped by branch or feature area. Highlight the current branch and what's in-progress. Format it so it can be read aloud in a standup or pasted into a sprint review:

- What was completed (past sessions)
- What's in progress (current branch/session)
- What's next or blocked

Keep it factual and concise - this is a status report, not an analysis.
