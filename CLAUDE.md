# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is a Claude Code plugin (`obsidian-skill`) that provides a skill for interacting with Obsidian vaults via the Obsidian CLI. It is not a buildable/testable project — it consists of declarative plugin metadata and skill documentation.

## Structure

- `.claude-plugin/plugin.json` — Plugin manifest (name, version, description)
- `skills/obsidian-cli/SKILL.md` — Skill definition with trigger conditions and usage documentation
- `skills/obsidian-cli/references/commands.md` — Complete Obsidian CLI command reference (sourced from obsidian.md/help/cli)

## How It Works

The plugin registers a single skill ("Obsidian CLI") that triggers when users mention Obsidian, vaults, daily notes, or ask to interact with an Obsidian vault. The skill provides Claude Code with knowledge of the `obsidian` CLI command syntax so it can execute vault operations.

Key constraint: the Obsidian desktop app must be running (v1.12+ with CLI enabled) for any `obsidian` commands to work.

## Editing Guidelines

- SKILL.md uses YAML frontmatter (`name`, `description`) for skill metadata — the `description` field controls when the skill triggers
- The reference file in `references/` is loaded as additional context when the skill activates — keep it comprehensive but structured
- Command syntax follows `obsidian <command> [param=value] [flags]` — not POSIX-style flags
