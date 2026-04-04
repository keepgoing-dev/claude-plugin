---
name: continue
description: Use when the user wants to switch to another AI tool (ChatGPT, Gemini, Copilot, etc.) and carry context with them - "continue on ChatGPT", "export context for Gemini", "take this to Copilot", "export my context".
argument-hint: [target: chatgpt | gemini | copilot | claude | general]
allowed-tools: ["mcp__plugin_keepgoing_keepgoing__continue_on"]
---

The user wants to export their current project context to use in another AI tool.

Parse `$ARGUMENTS` to determine the target tool. Valid targets are: `chatgpt`, `gemini`, `copilot`, `claude`, `general`. If no argument is provided or unrecognized, use `general`.

Call `mcp__plugin_keepgoing_keepgoing__continue_on` with:
- `target`: The parsed target from `$ARGUMENTS`
- `include_commits`: true
- `include_files`: true

The tool will return a formatted prompt. Present it to the user as a code block they can copy and paste into the target AI tool. Let them know it contains their project status, last session summary, recent decisions, and commit history.
