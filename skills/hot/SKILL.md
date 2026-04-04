---
name: hot
description: Use when the user asks "what am I working on these days", "what's active", "show all my projects", "cross-project activity", or wants an overview of momentum across multiple projects or branches.
allowed-tools: ["mcp__plugin_keepgoing_session__get_whats_hot"]
---

The user wants to see what's currently active across their project.

Call `mcp__plugin_keepgoing_session__get_whats_hot` to get recently touched files and active branches.

Present the results as a quick activity overview: which branches/features are hot, which files have been touched recently, and what looks most in-progress. This helps prioritize when returning to a project with multiple active threads.
