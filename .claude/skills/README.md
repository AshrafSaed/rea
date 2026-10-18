# `rea` skill (Claude Code and Claude Desktop)

A short entry-point skill for [REA](../../README.md). **`/rea` is a shortcut that
connects everything in one step:** it asks what to investigate, loads the
`reverse-engineer-anything` workflow, checks that the REA tools are connected, and runs
the investigation with them. You do not need to call each piece separately.

| Piece | Role |
| ----- | ---- |
| REA MCP server (`npx rea-agents setup`) | The tools that do the analysis |
| `reverse-engineer-anything` skill | The detailed investigation workflow |
| `rea` skill (this folder) | The shortcut that ties the two together |

Added in this fork by Ashraf Saed | MIGATRONIX. Not part of upstream `morluto/rea`.

## Files

| File | Purpose |
| ---- | ------- |
| `rea/SKILL.md` | The skill instructions |
| `rea.zip` | The same skill packaged for upload to Claude Desktop |

## Prerequisite: connect REA first

The skill is only instructions. The tools come from the REA MCP server:

```
npx rea-agents setup
```

Select **Claude Code** and **Claude Desktop** with Space, confirm with Enter, then
fully restart both apps (on macOS, Cmd+Q for Desktop).

## Claude Code

Copy the skill to your personal skills folder:

```
mkdir -p ~/.claude/skills && cp -R .claude/skills/rea ~/.claude/skills/
```

Restart Claude Code, then type `/rea` or write:

> Use rea to explain how feature X works in `/absolute/path/to/app` and show the evidence.

## Claude Desktop (add-on)

Claude Desktop does not read `~/.claude/skills`. Upload `rea.zip` in the app's skills
settings instead. The exact menu names depend on the app version and were not verified
here; see Anthropic's support documentation for the current steps.

After uploading, start a new chat and ask the same kind of question as above.
In Desktop, the skill cannot read files from this repository, so it follows its own
short instructions and the REA tools only.

## Notes

- Use REA only on software you own or are authorized to examine (see `DISCLAIMER.md`).
- Native-binary analysis needs Hopper, Ghidra or IDA. JavaScript, Electron and .NET
  inspection do not.
