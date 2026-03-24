# Obsidian CLI Command Reference

Complete reference for all Obsidian CLI commands, parameters, and flags.

Source: https://obsidian.md/help/cli

## General Commands

### `help`

Show list of all available commands.

| Parameter | Description |
|-----------|-------------|
| `<command>` | Show help for a specific command |

### `version`

Show Obsidian version.

### `reload`

Reload the app window.

### `restart`

Restart the app.

## Bases

Commands for Obsidian Bases.

### `bases`

List all `.base` files in the vault.

### `base:views`

List views in the current base file.

### `base:create`

Create a new item in a base. Defaults to the active base view if no file is specified.

| Parameter | Description |
|-----------|-------------|
| `file=<name>` | Base file name |
| `path=<path>` | Base file path |
| `view=<name>` | View name |
| `name=<name>` | New file name |
| `content=<text>` | Initial content |
| `open` | Open file after creating (flag) |
| `newtab` | Open in new tab (flag) |

### `base:query`

Query a base and return results.

| Parameter | Description |
|-----------|-------------|
| `file=<name>` | Base file name |
| `path=<path>` | Base file path |
| `view=<name>` | View name to query |
| `format=json\|csv\|tsv\|md\|paths` | Output format (default: json) |

## Bookmarks

### `bookmarks`

List bookmarks.

| Parameter | Description |
|-----------|-------------|
| `total` | Return bookmark count (flag) |
| `verbose` | Include bookmark types (flag) |
| `format=json\|tsv\|csv` | Output format (default: tsv) |

### `bookmark`

Add a bookmark.

| Parameter | Description |
|-----------|-------------|
| `file=<path>` | File to bookmark |
| `subpath=<subpath>` | Subpath (heading or block) within file |
| `folder=<path>` | Folder to bookmark |
| `search=<query>` | Search query to bookmark |
| `url=<url>` | URL to bookmark |
| `title=<title>` | Bookmark title |

## Command Palette

Commands for the command palette and hotkeys. Includes all commands registered by plugins.

### `commands`

List available command IDs.

| Parameter | Description |
|-----------|-------------|
| `filter=<prefix>` | Filter by ID prefix |

### `command`

Execute an Obsidian command.

| Parameter | Description |
|-----------|-------------|
| `id=<command-id>` | **(required)** Command ID to execute |

### `hotkeys`

List hotkeys for all commands.

| Parameter | Description |
|-----------|-------------|
| `total` | Return hotkey count (flag) |
| `verbose` | Show if hotkey is custom (flag) |
| `format=json\|tsv\|csv` | Output format (default: tsv) |

### `hotkey`

Get hotkey for a command.

| Parameter | Description |
|-----------|-------------|
| `id=<command-id>` | **(required)** Command ID |
| `verbose` | Show if custom or default (flag) |

## Daily Notes

### `daily`

Open daily note.

| Parameter | Description |
|-----------|-------------|
| `paneType=tab\|split\|window` | Pane type to open in |

### `daily:path`

Get daily note path. Returns the expected path even if the file hasn't been created yet.

### `daily:read`

Read daily note contents.

### `daily:append`

Append content to daily note.

| Parameter | Description |
|-----------|-------------|
| `content=<text>` | **(required)** Content to append |
| `paneType=tab\|split\|window` | Pane type to open in |
| `inline` | Append without newline (flag) |
| `open` | Open file after adding (flag) |

### `daily:prepend`

Prepend content to daily note.

| Parameter | Description |
|-----------|-------------|
| `content=<text>` | **(required)** Content to prepend |
| `paneType=tab\|split\|window` | Pane type to open in |
| `inline` | Prepend without newline (flag) |
| `open` | Open file after adding (flag) |

## File History

### `diff`

List or compare versions from local File Recovery and Sync. Versions are numbered from newest to oldest.

| Parameter | Description |
|-----------|-------------|
| `file=<name>` | File name |
| `path=<path>` | File path |
| `from=<n>` | Version number to diff from |
| `to=<n>` | Version number to diff to |
| `filter=local\|sync` | Filter by version source |

**Examples:**

```bash
diff                           # List all versions of the active file
diff file=Recipe               # List all versions of a specific file
diff file=Recipe from=1        # Compare latest version to current file
diff file=Recipe from=2 to=1   # Compare two versions
diff filter=sync               # Only show Sync versions
```

### `history`

List versions from File Recovery only. See `sync:history` for the equivalent Sync command.

| Parameter | Description |
|-----------|-------------|
| `file=<name>` | File name |
| `path=<path>` | File path |

### `history:list`

List all files with local history.

### `history:read`

Read a local history version.

| Parameter | Description |
|-----------|-------------|
| `file=<name>` | File name |
| `path=<path>` | File path |
| `version=<n>` | Version number (default: 1) |

### `history:restore`

Restore a local history version.

| Parameter | Description |
|-----------|-------------|
| `file=<name>` | File name |
| `path=<path>` | File path |
| `version=<n>` | **(required)** Version number |

### `history:open`

Open file recovery.

| Parameter | Description |
|-----------|-------------|
| `file=<name>` | File name |
| `path=<path>` | File path |

## Files and Folders

### `file`

Show file info (default: active file).

| Parameter | Description |
|-----------|-------------|
| `file=<name>` | File name |
| `path=<path>` | File path |

Example output:

```
path    Notes/Recipe.md
name    Recipe
extension    md
size    1024
created    1700000000000
modified    1700001000000
```

### `files`

List files in the vault.

| Parameter | Description |
|-----------|-------------|
| `folder=<path>` | Filter by folder |
| `ext=<extension>` | Filter by extension |
| `total` | Return file count (flag) |

### `folder`

Show folder info.

| Parameter | Description |
|-----------|-------------|
| `path=<path>` | **(required)** Folder path |
| `info=files\|folders\|size` | Return specific info only |

### `folders`

List folders in the vault.

| Parameter | Description |
|-----------|-------------|
| `folder=<path>` | Filter by parent folder |
| `total` | Return folder count (flag) |

### `open`

Open a file.

| Parameter | Description |
|-----------|-------------|
| `file=<name>` | File name |
| `path=<path>` | File path |
| `newtab` | Open in new tab (flag) |

### `create`

Create or overwrite a file.

| Parameter | Description |
|-----------|-------------|
| `name=<name>` | File name |
| `path=<path>` | File path |
| `content=<text>` | Initial content |
| `template=<name>` | Template to use |
| `overwrite` | Overwrite if file exists (flag) |
| `open` | Open file after creating (flag) |
| `newtab` | Open in new tab (flag) |

### `read`

Read file contents (default: active file).

| Parameter | Description |
|-----------|-------------|
| `file=<name>` | File name |
| `path=<path>` | File path |

### `append`

Append content to a file (default: active file).

| Parameter | Description |
|-----------|-------------|
| `file=<name>` | File name |
| `path=<path>` | File path |
| `content=<text>` | **(required)** Content to append |
| `inline` | Append without newline (flag) |

### `prepend`

Prepend content after frontmatter (default: active file).

| Parameter | Description |
|-----------|-------------|
| `file=<name>` | File name |
| `path=<path>` | File path |
| `content=<text>` | **(required)** Content to prepend |
| `inline` | Prepend without newline (flag) |

### `move`

Move or rename a file (default: active file). Automatically updates internal links if enabled in vault settings.

| Parameter | Description |
|-----------|-------------|
| `file=<name>` | File name |
| `path=<path>` | File path |
| `to=<path>` | **(required)** Destination folder or path |

### `rename`

Rename a file (default: active file). File extension is preserved automatically if omitted. Use `move` to rename and move simultaneously.

| Parameter | Description |
|-----------|-------------|
| `file=<name>` | File name |
| `path=<path>` | File path |
| `name=<name>` | **(required)** New file name |

### `delete`

Delete a file (default: active file, sends to trash by default).

| Parameter | Description |
|-----------|-------------|
| `file=<name>` | File name |
| `path=<path>` | File path |
| `permanent` | Skip trash, delete permanently (flag) |

## Links

Commands for backlinks and outgoing links.

### `backlinks`

List backlinks to a file (default: active file).

| Parameter | Description |
|-----------|-------------|
| `file=<name>` | Target file name |
| `path=<path>` | Target file path |
| `counts` | Include link counts (flag) |
| `total` | Return backlink count (flag) |
| `format=json\|tsv\|csv` | Output format (default: tsv) |

### `links`

List outgoing links from a file (default: active file).

| Parameter | Description |
|-----------|-------------|
| `file=<name>` | File name |
| `path=<path>` | File path |
| `total` | Return link count (flag) |

### `unresolved`

List unresolved links in vault.

| Parameter | Description |
|-----------|-------------|
| `total` | Return unresolved link count (flag) |
| `counts` | Include link counts (flag) |
| `verbose` | Include source files (flag) |
| `format=json\|tsv\|csv` | Output format (default: tsv) |

### `orphans`

List files with no incoming links.

| Parameter | Description |
|-----------|-------------|
| `total` | Return orphan count (flag) |

### `deadends`

List files with no outgoing links.

| Parameter | Description |
|-----------|-------------|
| `total` | Return dead-end count (flag) |

## Outline

### `outline`

Show headings for the current file.

| Parameter | Description |
|-----------|-------------|
| `file=<name>` | File name |
| `path=<path>` | File path |
| `format=tree\|md\|json` | Output format (default: tree) |
| `total` | Return heading count (flag) |

## Plugins

Commands for core and community plugins.

### `plugins`

List installed plugins.

| Parameter | Description |
|-----------|-------------|
| `filter=core\|community` | Filter by plugin type |
| `versions` | Include version numbers (flag) |
| `format=json\|tsv\|csv` | Output format (default: tsv) |

### `plugins:enabled`

List enabled plugins.

| Parameter | Description |
|-----------|-------------|
| `filter=core\|community` | Filter by plugin type |
| `versions` | Include version numbers (flag) |
| `format=json\|tsv\|csv` | Output format (default: tsv) |

### `plugins:restrict`

Toggle or check restricted mode.

| Parameter | Description |
|-----------|-------------|
| `on` | Enable restricted mode (flag) |
| `off` | Disable restricted mode (flag) |

### `plugin`

Get plugin info.

| Parameter | Description |
|-----------|-------------|
| `id=<plugin-id>` | **(required)** Plugin ID |

### `plugin:enable`

Enable a plugin.

| Parameter | Description |
|-----------|-------------|
| `id=<id>` | **(required)** Plugin ID |
| `filter=core\|community` | Plugin type |

### `plugin:disable`

Disable a plugin.

| Parameter | Description |
|-----------|-------------|
| `id=<id>` | **(required)** Plugin ID |
| `filter=core\|community` | Plugin type |

### `plugin:install`

Install a community plugin.

| Parameter | Description |
|-----------|-------------|
| `id=<id>` | **(required)** Plugin ID |
| `enable` | Enable after install (flag) |

### `plugin:uninstall`

Uninstall a community plugin.

| Parameter | Description |
|-----------|-------------|
| `id=<id>` | **(required)** Plugin ID |

### `plugin:reload`

Reload a plugin (for developers).

| Parameter | Description |
|-----------|-------------|
| `id=<id>` | **(required)** Plugin ID |

## Properties

Commands related to note properties (frontmatter).

### `aliases`

List aliases in the vault. Use `active` or `file`/`path` to show aliases for a specific file.

| Parameter | Description |
|-----------|-------------|
| `file=<name>` | File name |
| `path=<path>` | File path |
| `total` | Return alias count (flag) |
| `verbose` | Include file paths (flag) |
| `active` | Show aliases for active file (flag) |

### `properties`

List properties in the vault. Use `active` or `file`/`path` to show properties for a specific file.

| Parameter | Description |
|-----------|-------------|
| `file=<name>` | Show properties for file |
| `path=<path>` | Show properties for path |
| `name=<name>` | Get specific property |
| `count` | (unknown usage) |
| `sort=count` | Sort by count (default: name) |
| `format=yaml\|json\|tsv` | Output format (default: yaml) |
| `total` | Return property count (flag) |
| `counts` | Include occurrence counts (flag) |
| `active` | Show properties for active file (flag) |

### `property:set`

Set a property on a file (default: active file).

| Parameter | Description |
|-----------|-------------|
| `name=<name>` | **(required)** Property name |
| `value=<value>` | **(required)** Property value |
| `type=text\|list\|number\|checkbox\|date\|datetime` | Property type |
| `file=<name>` | File name |
| `path=<path>` | File path |

### `property:remove`

Remove a property from a file (default: active file).

| Parameter | Description |
|-----------|-------------|
| `name=<name>` | **(required)** Property name |
| `file=<name>` | File name |
| `path=<path>` | File path |

### `property:read`

Read a property value from a file (default: active file).

| Parameter | Description |
|-----------|-------------|
| `name=<name>` | **(required)** Property name |
| `file=<name>` | File name |
| `path=<path>` | File path |

## Publish

Commands for Obsidian Publish.

### `publish:site`

Show publish site info (slug, URL).

### `publish:list`

List published files.

| Parameter | Description |
|-----------|-------------|
| `total` | Return published file count (flag) |

### `publish:status`

List publish changes.

| Parameter | Description |
|-----------|-------------|
| `total` | Return change count (flag) |
| `new` | Show new files only (flag) |
| `changed` | Show changed files only (flag) |
| `deleted` | Show deleted files only (flag) |

### `publish:add`

Publish a file or all changed files (default: active file).

| Parameter | Description |
|-----------|-------------|
| `file=<name>` | File name |
| `path=<path>` | File path |
| `changed` | Publish all changed files (flag) |

### `publish:remove`

Unpublish a file (default: active file).

| Parameter | Description |
|-----------|-------------|
| `file=<name>` | File name |
| `path=<path>` | File path |

### `publish:open`

Open file on published site (default: active file).

| Parameter | Description |
|-----------|-------------|
| `file=<name>` | File name |
| `path=<path>` | File path |

## Random Notes

### `random`

Open a random note.

| Parameter | Description |
|-----------|-------------|
| `folder=<path>` | Limit to folder |
| `newtab` | Open in new tab (flag) |

### `random:read`

Read a random note (includes path).

| Parameter | Description |
|-----------|-------------|
| `folder=<path>` | Limit to folder |

## Search

### `search`

Search vault for text. Returns matching file paths.

| Parameter | Description |
|-----------|-------------|
| `query=<text>` | **(required)** Search query |
| `path=<folder>` | Limit to folder |
| `limit=<n>` | Max files |
| `format=text\|json` | Output format (default: text) |
| `total` | Return match count (flag) |
| `case` | Case sensitive (flag) |

### `search:context`

Search with matching line context. Returns grep-style `path:line: text` output.

| Parameter | Description |
|-----------|-------------|
| `query=<text>` | **(required)** Search query |
| `path=<folder>` | Limit to folder |
| `limit=<n>` | Max files |
| `format=text\|json` | Output format (default: text) |
| `case` | Case sensitive (flag) |

### `search:open`

Open search view.

| Parameter | Description |
|-----------|-------------|
| `query=<text>` | Initial search query |

## Sync

Commands for Obsidian Sync. To sync without the desktop app, see Obsidian Headless.

### `sync`

Pause or resume sync.

| Parameter | Description |
|-----------|-------------|
| `on` | Resume sync (flag) |
| `off` | Pause sync (flag) |

### `sync:status`

Show sync status and usage.

### `sync:history`

List sync version history for a file (default: active file).

| Parameter | Description |
|-----------|-------------|
| `file=<name>` | File name |
| `path=<path>` | File path |
| `total` | Return version count (flag) |

### `sync:read`

Read a sync version (default: active file).

| Parameter | Description |
|-----------|-------------|
| `file=<name>` | File name |
| `path=<path>` | File path |
| `version=<n>` | **(required)** Version number |

### `sync:restore`

Restore a sync version (default: active file).

| Parameter | Description |
|-----------|-------------|
| `file=<name>` | File name |
| `path=<path>` | File path |
| `version=<n>` | **(required)** Version number |

### `sync:open`

Open sync history (default: active file).

| Parameter | Description |
|-----------|-------------|
| `file=<name>` | File name |
| `path=<path>` | File path |

### `sync:deleted`

List deleted files in sync.

| Parameter | Description |
|-----------|-------------|
| `total` | Return deleted file count (flag) |

## Tags

### `tags`

List tags in the vault. Use `active` or `file`/`path` to show tags for a specific file.

| Parameter | Description |
|-----------|-------------|
| `file=<name>` | File name |
| `path=<path>` | File path |
| `sort=count` | Sort by count (default: name) |
| `total` | Return tag count (flag) |
| `counts` | Include tag counts (flag) |
| `format=json\|tsv\|csv` | Output format (default: tsv) |
| `active` | Show tags for active file (flag) |

### `tag`

Get tag info.

| Parameter | Description |
|-----------|-------------|
| `name=<tag>` | **(required)** Tag name |
| `total` | Return occurrence count (flag) |
| `verbose` | Include file list and count (flag) |

## Tasks

### `tasks`

List tasks in the vault. Use `active` or `file`/`path` to show tasks for a specific file.

| Parameter | Description |
|-----------|-------------|
| `file=<name>` | Filter by file name |
| `path=<path>` | Filter by file path |
| `status="<char>"` | Filter by status character |
| `total` | Return task count (flag) |
| `done` | Show completed tasks (flag) |
| `todo` | Show incomplete tasks (flag) |
| `verbose` | Group by file with line numbers (flag) |
| `format=json\|tsv\|csv` | Output format (default: text) |
| `active` | Show tasks for active file (flag) |
| `daily` | Show tasks from daily note (flag) |

**Examples:**

```bash
tasks                        # List all tasks in the vault
tasks todo                   # List incomplete tasks
tasks file=Recipe done       # Completed tasks from a specific file
tasks daily                  # Tasks from today's daily note
tasks daily total            # Count tasks in daily note
tasks verbose                # Tasks with file paths and line numbers
tasks 'status=?'             # Filter by custom status (quote special chars)
```

### `task`

Show or update a task.

| Parameter | Description |
|-----------|-------------|
| `ref=<path:line>` | Task reference (path:line) |
| `file=<name>` | File name |
| `path=<path>` | File path |
| `line=<n>` | Line number |
| `status="<char>"` | Set status character |
| `toggle` | Toggle task status (flag) |
| `daily` | Daily note (flag) |
| `done` | Mark as done (flag) |
| `todo` | Mark as todo (flag) |

**Examples:**

```bash
task file=Recipe line=8           # Show task info
task ref="Recipe.md:8"            # Same, using ref
task ref="Recipe.md:8" toggle     # Toggle completion
task daily line=3 toggle          # Toggle daily note task
task file=Recipe line=8 done      # Mark done → [x]
task file=Recipe line=8 todo      # Mark todo → [ ]
task file=Recipe line=8 status=-  # Set status → [-]
task daily line=3 done            # Mark daily note task done
```

## Templates

### `templates`

List templates.

| Parameter | Description |
|-----------|-------------|
| `total` | Return template count (flag) |

### `template:read`

Read template content.

| Parameter | Description |
|-----------|-------------|
| `name=<template>` | **(required)** Template name |
| `title=<title>` | Title for variable resolution |
| `resolve` | Resolve template variables (flag) |

Notes:
- `resolve` processes `{{date}}`, `{{time}}`, `{{title}}` variables
- Use `create path=<path> template=<name>` to create a file with a template

### `template:insert`

Insert template into active file.

| Parameter | Description |
|-----------|-------------|
| `name=<template>` | **(required)** Template name |

## Themes and Snippets

### `themes`

List installed themes.

| Parameter | Description |
|-----------|-------------|
| `versions` | Include version numbers (flag) |

### `theme`

Show active theme or get info.

| Parameter | Description |
|-----------|-------------|
| `name=<name>` | Theme name for details |

### `theme:set`

Set active theme.

| Parameter | Description |
|-----------|-------------|
| `name=<name>` | **(required)** Theme name (empty for default) |

### `theme:install`

Install a community theme.

| Parameter | Description |
|-----------|-------------|
| `name=<name>` | **(required)** Theme name |
| `enable` | Activate after install (flag) |

### `theme:uninstall`

Uninstall a theme.

| Parameter | Description |
|-----------|-------------|
| `name=<name>` | **(required)** Theme name |

### `snippets`

List installed CSS snippets.

### `snippets:enabled`

List enabled CSS snippets.

### `snippet:enable`

Enable a CSS snippet.

| Parameter | Description |
|-----------|-------------|
| `name=<name>` | **(required)** Snippet name |

### `snippet:disable`

Disable a CSS snippet.

| Parameter | Description |
|-----------|-------------|
| `name=<name>` | **(required)** Snippet name |

## Unique Notes

### `unique`

Create unique note.

| Parameter | Description |
|-----------|-------------|
| `name=<text>` | Note name |
| `content=<text>` | Initial content |
| `paneType=tab\|split\|window` | Pane type to open in |
| `open` | Open file after creating (flag) |

## Vault

### `vault`

Show vault info.

| Parameter | Description |
|-----------|-------------|
| `info=name\|path\|files\|folders\|size` | Return specific info only |

### `vaults`

List known vaults.

| Parameter | Description |
|-----------|-------------|
| `total` | Return vault count (flag) |
| `verbose` | Include vault paths (flag) |

### `vault:open`

Switch to a different vault (TUI only).

| Parameter | Description |
|-----------|-------------|
| `name=<name>` | **(required)** Vault name |

## Web Viewer

### `web`

Open URL in web viewer.

| Parameter | Description |
|-----------|-------------|
| `url=<url>` | **(required)** URL to open |
| `newtab` | Open in new tab (flag) |

## Wordcount

### `wordcount`

Count words and characters (default: active file).

| Parameter | Description |
|-----------|-------------|
| `file=<name>` | File name |
| `path=<path>` | File path |
| `words` | Return word count only (flag) |
| `characters` | Return character count only (flag) |

## Workspace

### `workspace`

Show workspace tree.

| Parameter | Description |
|-----------|-------------|
| `ids` | Include workspace item IDs (flag) |

### `workspaces`

List saved workspaces.

| Parameter | Description |
|-----------|-------------|
| `total` | Return workspace count (flag) |

### `workspace:save`

Save current layout as workspace.

| Parameter | Description |
|-----------|-------------|
| `name=<name>` | Workspace name |

### `workspace:load`

Load a saved workspace.

| Parameter | Description |
|-----------|-------------|
| `name=<name>` | **(required)** Workspace name |

### `workspace:delete`

Delete a saved workspace.

| Parameter | Description |
|-----------|-------------|
| `name=<name>` | **(required)** Workspace name |

### `tabs`

List open tabs.

| Parameter | Description |
|-----------|-------------|
| `ids` | Include tab IDs (flag) |

### `tab:open`

Open a new tab.

| Parameter | Description |
|-----------|-------------|
| `group=<id>` | Tab group ID |
| `file=<path>` | File to open |
| `view=<type>` | View type to open |

### `recents`

List recently opened files.

| Parameter | Description |
|-----------|-------------|
| `total` | Return recent file count (flag) |

## Developer Commands

Commands to help develop community plugins and themes. See https://docs.obsidian.md for developer documentation.

### `devtools`

Toggle Electron dev tools.

### `dev:debug`

Attach/detach Chrome DevTools Protocol debugger.

| Parameter | Description |
|-----------|-------------|
| `on` | Attach debugger (flag) |
| `off` | Detach debugger (flag) |

### `dev:cdp`

Run a Chrome DevTools Protocol command.

| Parameter | Description |
|-----------|-------------|
| `method=<CDP.method>` | **(required)** CDP method to call |
| `params=<json>` | Method parameters as JSON |

### `dev:errors`

Show captured JavaScript errors.

| Parameter | Description |
|-----------|-------------|
| `clear` | Clear the error buffer (flag) |

### `dev:screenshot`

Take a screenshot (returns base64 PNG).

| Parameter | Description |
|-----------|-------------|
| `path=<filename>` | Output file path |

### `dev:console`

Show captured console messages.

| Parameter | Description |
|-----------|-------------|
| `limit=<n>` | Max messages to show (default: 50) |
| `level=log\|warn\|error\|info\|debug` | Filter by log level |
| `clear` | Clear the console buffer (flag) |

### `dev:css`

Inspect CSS with source locations.

| Parameter | Description |
|-----------|-------------|
| `selector=<css>` | **(required)** CSS selector |
| `prop=<name>` | Filter by property name |

### `dev:dom`

Query DOM elements.

| Parameter | Description |
|-----------|-------------|
| `selector=<css>` | **(required)** CSS selector |
| `attr=<name>` | Get attribute value |
| `css=<prop>` | Get CSS property value |
| `total` | Return element count (flag) |
| `text` | Return text content (flag) |
| `inner` | Return innerHTML instead of outerHTML (flag) |
| `all` | Return all matches instead of first (flag) |

### `dev:mobile`

Toggle mobile emulation.

| Parameter | Description |
|-----------|-------------|
| `on` | Enable mobile emulation (flag) |
| `off` | Disable mobile emulation (flag) |

### `eval`

Execute JavaScript and return result.

| Parameter | Description |
|-----------|-------------|
| `code=<javascript>` | **(required)** JavaScript code to execute |
