---
name: rea
description: Shortcut for reverse engineering with REA. Use when the user types /rea or asks to understand how an app, binary, Electron/JavaScript package, APK, firmware or website works from the shipped artifact. Loads the reverse-engineer-anything workflow and runs it against the target the user names.
---

# rea

Thin entry point for the `reverse-engineer-anything` skill and the REA MCP server.

## Steps

1. **Get the target.** If the user did not give an absolute path or URL, ask for it
   (in Hebrew if the user writes Hebrew). Also ask what they want to learn:
   a feature, a calculation, a version comparison, or a reconstruction.
2. **Restate the request** in one line before starting, so the user can confirm it.
3. **Load the workflow.** Read the `reverse-engineer-anything` skill
   (`.agents/skills/reverse-engineer-anything/SKILL.md` in this repository, or the
   installed copy in `~/.agents/skills` / `~/.claude/skills`) and follow it.
4. **Check REA is connected.** If no REA tools are available, do not guess results.
   Tell the user to run `npx rea-agents setup`, select Claude Code and Claude Desktop
   with Space, confirm with Enter, then restart the app.
5. **Investigate with evidence.** Use the REA tools. Report what was found, the
   evidence for each claim, and what could not be established.

## Rules

- Analyze only software the user owns or is authorized to examine (see DISCLAIMER.md).
- Native-binary analysis needs Hopper, Ghidra or IDA. If none is installed, say so
  and offer JavaScript, Electron or .NET inspection, which needs no native engine.
- Do not claim a conclusion the evidence does not support.
