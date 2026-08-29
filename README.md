# herman-skills

Personal skills for AI coding agents. One folder per skill, and each folder holds a `SKILL.md` in the standard [agent skills](https://agentskills.io) format.

More skills will be added over time.

## Skills

| Skill | What it does |
| --- | --- |
| edu-writer | Professional UK English writing standard for assignment and educational content. Triggers on `/edu-writer` or asking for the edu-writer standard. Not for code or project output. |

## Install

### Option 1: skills CLI (recommended)

```bash
npx skills add ChamHerman/herman-skills
```

The CLI scans this repository, lists the skills it finds, detects which coding agents you have installed, and installs each skill to the right directory. It will prompt you to pick skills, agents, and whether to symlink or copy. Useful flags:

- Install only one skill: `npx skills add ChamHerman/herman-skills --skill edu-writer`
- Target specific agents: add `-a claude-code -a codex` (and so on)
- Install globally for all projects instead of the current project: add `-g`

If your agent is not detected by the CLI, use option 2.

### Option 2: manual copy

1. Choose your skills directory:
   - Cross-agent (works for Claude Code, ZCode, Codex, Copilot CLI, and Gemini CLI): `~/.agents/skills`
   - Claude Code also reads `~/.claude/skills`
2. Clone this repository anywhere:
   ```bash
   git clone https://github.com/ChamHerman/herman-skills.git
   ```
3. Copy the skill folder into your skills directory. Each skill must sit directly inside the skills folder, so copy folders individually rather than cloning the repository into it.
   - macOS, Linux, or Git Bash:
     ```bash
     cp -r herman-skills/edu-writer ~/.agents/skills/
     ```
   - Windows PowerShell:
     ```powershell
     Copy-Item -Recurse herman-skills\edu-writer $HOME\.agents\skills\
     ```
4. Start a new session. Agents read the skill list when a session starts, so a session that is already running will not see the skill until it restarts.

Verify by invoking `/edu-writer`, or by asking the agent which skills it can see.

## Update

With the CLI: run `npx skills check` to see pending updates and `npx skills update` to apply them.

Manual: pull the latest version and copy the changed folders again:

```bash
git -C herman-skills pull
cp -r herman-skills/edu-writer ~/.agents/skills/
```

## Adding more skills

Each skill is a folder at the repository root containing a `SKILL.md` with `name` and `description` frontmatter. Drop a new folder in, commit, and push; users then install it with `npx skills add ChamHerman/herman-skills` or copy the new folder manually.

## Licence

[MIT](LICENSE)
