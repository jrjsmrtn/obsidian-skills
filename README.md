<!-- SPDX-FileCopyrightText: 2026 Georges Martin <jrjsmrtn@gmail.com> -->
<!-- SPDX-License-Identifier: MIT -->

# Obsidian CLI Skills

A Claude Code plugin providing a skill for interacting with Obsidian vaults via the Obsidian CLI.

## Installation

### Claude Code

Install via the [jrjsmrtn-skills](https://github.com/jrjsmrtn/jrjsmrtn-skills) marketplace:

```
/plugin install github:jrjsmrtn/jrjsmrtn-skills
```

### Mistral Vibe

[Mistral Vibe](https://mistral.ai/products/vibe) scans `~/.vibe/skills/` as a flat directory. Bridge this plugin's nested layout via clone + symlink:

```bash
mkdir -p ~/.vibe/claude-skills ~/.vibe/skills
git clone https://github.com/jrjsmrtn/obsidian-skills.git ~/.vibe/claude-skills/obsidian-skills
cd ~/.vibe/skills
for skill_dir in ~/.vibe/claude-skills/obsidian-skills/skills/*/; do
  skill=$(basename "$skill_dir")
  ln -s "../claude-skills/obsidian-skills/skills/${skill}" "${skill}"
done
```

Update later: `git -C ~/.vibe/claude-skills/obsidian-skills pull`.

## Included Skills

| Skill | Description |
|-------|-------------|
| **obsidian-cli** | Interact with Obsidian vaults via the `obsidian` CLI — open vaults, create/search notes, manage daily notes |

## Requirements

- Obsidian desktop app v1.12+ with CLI enabled
- The app must be running for `obsidian` commands to work

## Usage

After installation, mention Obsidian, vaults, or daily notes in conversation — Claude will activate the skill automatically.

## License

MIT
