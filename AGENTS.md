# Multi-Repository Workspace Instructions

This directory is a coordination workspace. Repositories are local checkouts
listed in `workspace.local.toml`; they are not part of the workspace repository.

## Workflow

- The root agent owns scope, routing, decisions, steering, and the final response.
- Delegate one bounded task to one direct subagent by default. Add agents only
  for genuinely independent work, and never run multiple write-capable agents
  in the same repository or worktree concurrently.
- Before repository work, read `REPOS.md` and `MEMORY.md`, identify the relevant
  repositories, and read their applicable `AGENTS.md` files.
- Run Git and project commands from the relevant repository directory.
- Preserve unrelated worktree changes and keep edits focused on the request.
- Use project-local environments and documented test commands when available.
- Subagents own their assigned exploration, edits, tests, verification, and
  handoff. They must not spawn additional agents.
- On completion, summarize changes, checks, and unresolved risks or follow-ups.
- Do not update `MEMORY.md` routinely. It is private local working memory.

## Local Files

- `workspace.local.toml` defines this user's repository layout.
- `REPOS.md` is generated from that manifest with `scripts/render-repos`.
- `MEMORY.md` contains private working context.
- `repos/` is the conventional location for child repositories, but manifest
  entries may use any workspace-relative path.

These files and all child repositories are intentionally ignored by the
workspace repository.
