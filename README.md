# Executive Function Skills

Seven slash commands for ADHD-friendly task management. Works in Claude Code and Claude.ai.

## Commands

| Command       | Purpose                                              |
| ------------- | ---------------------------------------------------- |
| `/decompose`  | Break an overwhelming task into micro-steps         |
| `/prioritize` | Triage a task list (Eisenhower + energy cost)       |
| `/timeblock`  | Build a time-blocked schedule with buffers          |
| `/decide`     | Definitive recommendation between two options       |
| `/focus`      | Pre-work ritual + distraction protocol              |
| `/momentum`   | Velocity check + bottleneck + next move             |
| `/reset`      | Evening shutdown ritual                             |

Usage pattern: `/<command> <your input>` — e.g. `/decompose write the AuthV6 state machine tests`.

If you type a command with no arguments, the skill will ask one focused question and stop. If you forget a command name, type `/` in Claude Code to see the full list.

## Install — Claude Code

Personal install (all projects):

```bash
mkdir -p ~/.claude/skills
cp -r decompose prioritize timeblock decide focus momentum reset ~/.claude/skills/
```

Restart Claude Code (or start a new session). Type `/` to confirm the seven commands appear.

Project-scoped install: replace `~/.claude/skills` with `.claude/skills` in your project root. Commit to share with a team.

## Install — Claude.ai

Requires a paid plan (Pro, Max, Team, or Enterprise) with code execution enabled.

1. Upload each `.skill` file via **Settings → Capabilities → Skills → Upload skill** (one at a time).
2. In any chat, type the command — e.g., `/decompose write the state machine tests`. The skill auto-triggers from the description match.

Note: Claude.ai's custom-skill invocation is description-driven rather than a hard slash-command parser. Typing `/decompose ...` still works because the description explicitly lists `/decompose` as a trigger phrase. You can also invoke naturally: "decompose: write the tests" or "I'm overwhelmed by writing the tests".

## Customizing

Each skill is a plain `SKILL.md`. Edit the body to change behavior; edit the `description:` field to change triggers. Keep the `name:` field lowercase with no spaces — that's the slash command.
