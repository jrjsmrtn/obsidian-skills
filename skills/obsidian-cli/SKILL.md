---
name: Obsidian CLI
description: >
  This skill should be used when the user asks to "read an Obsidian note",
  "search my vault", "create a note in Obsidian", "append to my daily note",
  "list tags in Obsidian", "check my tasks", "open a file in Obsidian",
  "manage Obsidian plugins", "query a base", or any interaction with an
  Obsidian vault via the command line. Also triggered when the user mentions
  "obsidian", "vault", "daily note", or "Obsidian CLI".
---

# Obsidian CLI

Obsidian CLI (`obsidian`) is a command line interface for controlling Obsidian from the terminal. It enables scripting, automation, and integration with external tools. The Obsidian desktop app must be running for CLI commands to work.

## Prerequisites

- Obsidian installer v1.12+ with CLI enabled in **Settings > General > Command line interface**
- The Obsidian desktop app must be running (the first CLI command will launch it if not)

## Command Syntax

```bash
# Single command mode
obsidian <command> [parameters] [flags]

# Interactive TUI mode (autocomplete, history, Ctrl+R search)
obsidian
```

### Parameters and Flags

- **Parameter**: takes a value as `param=value`. Quote values with spaces: `content="Hello world"`
- **Flag**: boolean switch with no value. Include to enable: `open`, `overwrite`, `verbose`
- **Multiline content**: use `\n` for newline, `\t` for tab
- **Copy output**: append `--copy` to any command to copy output to clipboard

### Vault Targeting

If the terminal's cwd is inside a vault, that vault is used. Otherwise the active vault is used.

```bash
obsidian vault=Notes daily
obsidian vault="My Vault" search query="test"
```

### File Targeting

Many commands accept `file=<name>` (wikilink-style resolution) or `path=<path>` (exact path from vault root). If neither is provided, the active file is used.

```bash
obsidian read file=Recipe
obsidian read path="Templates/Recipe.md"
```

## Common Workflows

### Reading and Writing Notes

```bash
obsidian read                                    # read active file
obsidian read file=Recipe                        # read by name
obsidian create name="Trip to Paris" template=Travel open  # create from template
obsidian append file=TODO content="- [ ] Buy milk"         # append to file
obsidian prepend path="journal.md" content="---"           # prepend after frontmatter
```

### Daily Notes

```bash
obsidian daily                                              # open today's daily note
obsidian daily:read                                         # read daily note contents
obsidian daily:append content="- [ ] Buy groceries"         # add to daily note
obsidian daily:path                                         # get daily note path
```

### Search

```bash
obsidian search query="meeting notes"                       # search vault
obsidian search query="TODO" path=Projects limit=10         # scoped search
obsidian search:context query="meeting" format=json         # search with line context
```

### Tasks

```bash
obsidian tasks                          # list all tasks
obsidian tasks todo                     # incomplete tasks only
obsidian tasks daily                    # tasks from daily note
obsidian task ref="Recipe.md:8" toggle  # toggle task status
obsidian task daily line=3 done         # mark daily task done
```

### Properties and Tags

```bash
obsidian tags counts                                        # list tags with counts
obsidian properties file=Note format=yaml                   # show file properties
obsidian property:set name=status value=draft file=Note     # set property
obsidian property:read name=tags file=Note                  # read property
```

### Vault Analysis

```bash
obsidian files                          # list all files
obsidian files folder=Projects ext=md   # filter by folder/extension
obsidian backlinks file=Note            # find what links to a file
obsidian links file=Note                # outgoing links
obsidian orphans                        # files with no incoming links
obsidian unresolved                     # broken links
obsidian outline file=Note              # show heading structure
```

### Plugins

```bash
obsidian plugins                        # list installed plugins
obsidian plugins:enabled filter=community  # list enabled community plugins
obsidian plugin:install id=my-plugin enable # install and enable
obsidian plugin:reload id=my-plugin     # reload (for development)
```

### Developer Commands

```bash
obsidian devtools                                    # toggle dev tools
obsidian dev:screenshot path=screenshot.png          # take screenshot
obsidian eval code="app.vault.getFiles().length"     # run JavaScript
obsidian dev:console level=error                     # show error logs
obsidian dev:css selector=".workspace" prop=background  # inspect CSS
obsidian dev:dom selector=".nav-file-title" text all    # query DOM
```

## Output Formats

Many commands support `format=json|tsv|csv|md` for structured output. Default varies by command. Use `total` flag to get counts only.

## Command Categories

For the complete command reference with all parameters and flags, consult `references/commands.md`. Commands are organized into these categories:

- **General**: `help`, `version`, `reload`, `restart`
- **Bases**: `bases`, `base:views`, `base:create`, `base:query`
- **Bookmarks**: `bookmarks`, `bookmark`
- **Command palette**: `commands`, `command`, `hotkeys`, `hotkey`
- **Daily notes**: `daily`, `daily:path`, `daily:read`, `daily:append`, `daily:prepend`
- **File history**: `diff`, `history`, `history:list`, `history:read`, `history:restore`, `history:open`
- **Files and folders**: `file`, `files`, `folder`, `folders`, `open`, `create`, `read`, `append`, `prepend`, `move`, `rename`, `delete`
- **Links**: `backlinks`, `links`, `unresolved`, `orphans`, `deadends`
- **Outline**: `outline`
- **Plugins**: `plugins`, `plugins:enabled`, `plugins:restrict`, `plugin`, `plugin:enable`, `plugin:disable`, `plugin:install`, `plugin:uninstall`, `plugin:reload`
- **Properties**: `aliases`, `properties`, `property:set`, `property:remove`, `property:read`
- **Publish**: `publish:site`, `publish:list`, `publish:status`, `publish:add`, `publish:remove`, `publish:open`
- **Random notes**: `random`, `random:read`
- **Search**: `search`, `search:context`, `search:open`
- **Sync**: `sync`, `sync:status`, `sync:history`, `sync:read`, `sync:restore`, `sync:open`, `sync:deleted`
- **Tags**: `tags`, `tag`
- **Tasks**: `tasks`, `task`
- **Templates**: `templates`, `template:read`, `template:insert`
- **Themes and snippets**: `themes`, `theme`, `theme:set`, `theme:install`, `theme:uninstall`, `snippets`, `snippets:enabled`, `snippet:enable`, `snippet:disable`
- **Unique notes**: `unique`
- **Vault**: `vault`, `vaults`, `vault:open`
- **Web viewer**: `web`
- **Wordcount**: `wordcount`
- **Workspace**: `workspace`, `workspaces`, `workspace:save`, `workspace:load`, `workspace:delete`, `tabs`, `tab:open`, `recents`
- **Developer**: `devtools`, `dev:debug`, `dev:cdp`, `dev:errors`, `dev:screenshot`, `dev:console`, `dev:css`, `dev:dom`, `dev:mobile`, `eval`

## Additional Resources

### Reference Files

- **`references/commands.md`** - Complete command reference with all parameters, flags, and descriptions for every Obsidian CLI command
