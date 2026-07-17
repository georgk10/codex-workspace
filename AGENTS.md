# Multi-Repository Workspace

This coordination workspace contains local repository checkouts listed in
`workspace.local.toml`; they are not part of the workspace repository.

## Workflow

- The root agent is the user-facing manager. It owns scope, routing, decisions,
  steering, and the final response, but must not perform or repeat delegated
  project work.
- By default, delegate one bounded task to one direct subagent. Use at most three
  direct subagents, adding them only for genuinely independent parallel work.
  Never parallelize sequential or dependent work or run multiple write-capable
  agents concurrently in the same repository or worktree.
- Choose the lowest-cost safe role:
  - `quick_check`: bounded read-only searches, inventories, status checks, and
    evidence gathering.
  - `standard_worker`: ordinary scoped diagnosis, implementation, tests,
    verification, and handoff.
  - `deep_reviewer`: difficult read-only correctness, security, concurrency,
    data-integrity, architecture, or operational-risk review.
  - `deep_worker`: rare ambiguous, cross-repository, high-risk, or quality-first
    implementation requiring the parent session's model and reasoning settings.
- Never use the built-in standard worker.
- Before repository work, each subagent reads `REPOS.md` and `MEMORY.md`,
  identifies the relevant repositories, reads their applicable `AGENTS.md`
  files, and makes a short plan.
- Subagents own their assigned exploration, edits, review, tests, verification,
  and handoff. Keep changes focused, touch only necessary repositories, and run
  Git and project commands from the relevant repository.
- The manager may read routing instructions, ask for decisions, steer agents,
  and report distilled results. Keep exploration notes, command output, and test
  logs in subagent tasks.
- On completion, summarize changes, checks, and unresolved risks or follow-ups.
- Do not routinely update `MEMORY.md`.

## Local Files

- `workspace.local.toml` defines the user's repository layout.
- `REPOS.md` is generated from it by `scripts/render-repos`.
- `MEMORY.md` contains private working context.
- Child repositories conventionally live in `repos/`, but manifest entries may
  use any workspace-relative path.

These files and all child repositories are intentionally ignored by the
workspace repository.