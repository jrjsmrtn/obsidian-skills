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

### Other agents (Copilot CLI, Cursor, Codex, Gemini CLI, Antigravity, Goose, …)

Use the GitHub CLI (`gh` ≥ 2.90.0) — it auto-detects the agent host and installs into the right skills directory:

```
gh skill install jrjsmrtn/obsidian-skills
```

Pin a single skill or version: `gh skill install jrjsmrtn/obsidian-skills <skill-name>[@v<version>]`. Update later with `gh skill update --all`.

For [Mistral Vibe](https://mistral.ai/products/vibe) (not yet in `gh skill`'s host detection), pass `--dir`:

```
gh skill install jrjsmrtn/obsidian-skills --dir ~/.vibe/skills
```

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
