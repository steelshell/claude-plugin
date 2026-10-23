# Steelshell for Claude Code

Let Claude Code work on the servers you keep in [Steelshell](https://steelshell.dev): run commands, read logs, edit files and fix bugs over SSH. The agent never sees a password or key, only reaches the servers you share, and every call lands in your audit log.

The plugin adds the `steelshell` MCP server and a skill that teaches the agent to work carefully: look before touching, back up, validate, verify, and ask before anything destructive.

## Install

1. Install the Steelshell CLI on the machine where Claude Code runs (Debian or Ubuntu):

   ```sh
   curl -fsSL https://steelshell.dev/install.sh | sh
   steelshell login
   ```

2. Share the servers the agent may use:

   ```sh
   steelshell agent allow prod-api            # run commands and edit files
   steelshell agent allow db-1 --read-only    # only read folders and files
   ```

3. Add the plugin in Claude Code:

   ```
   /plugin marketplace add steelshell/claude-plugin
   /plugin install steelshell@steelshell
   ```

Without the plugin, `steelshell agent setup` connects the MCP server and installs the same skill for Claude Code directly. Use one of the two, not both.

## Other agents

`steelshell agent setup` also prints the MCP configuration for Codex, Cursor and Claude Desktop. `steelshell agent skill` prints the skill as a `SKILL.md` file.
