---
name: save
description: Use when the user says "save a checkpoint", "checkpoint", "save progress", "mark this milestone", or wants to explicitly capture current state with a custom message.
argument-hint: [optional message describing what was accomplished]
allowed-tools: ["mcp__plugin_keepgoing_session__save_checkpoint"]
---

The user wants to save a checkpoint manually.

If `$ARGUMENTS` is provided, use it as the checkpoint summary. Otherwise, infer a 1-2 sentence summary from what was just accomplished in this session (look at recent tool use and conversation context).

Call `mcp__plugin_keepgoing_session__save_checkpoint` with:
- `summary`: The message from `$ARGUMENTS`, or your inferred 1-sentence summary of what was accomplished and why. Max 140 chars. No file paths or implementation details.
- `nextStep`: Max 100 chars. What should be done next (infer from context if not obvious).
- `blocker`: Max 100 chars. Any blocker if one is apparent, otherwise omit.

Confirm to the user that the checkpoint was saved.
