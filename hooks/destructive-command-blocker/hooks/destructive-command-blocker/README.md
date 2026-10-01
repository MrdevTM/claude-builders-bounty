# Claude Code Destructive Command Blocker

A `pre-tool-use` hook for Claude Code that intercepts and aborts dangerous bash commands before execution.

## Features
- **Blocked Patterns:**
  - `rm -rf` / `rm -fr` (recursive forced deletion)
  - `git push --force` / `git push -f`
  - SQL `DROP TABLE`
  - SQL `TRUNCATE`
  - SQL `DELETE FROM <table>` when missing a `WHERE` clause
- Does **not** interfere with safe commands (e.g., `rm file.txt`, `git push origin branch`, `DELETE FROM users WHERE id = 1`).
- Logs all blocked operations to `~/.claude/hooks/blocked.log` with timestamp, project directory
