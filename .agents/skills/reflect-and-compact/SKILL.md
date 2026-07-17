---
name: reflect-and-compact
description: Create a fast workspace checkpoint before compaction. Use only when explicitly asked to checkpoint, preserve context, update the repository inventory or MEMORY.md, improve workflow, or prepare for `/compact`.
---

# Reflect And Compact

Create a concise, trustworthy continuation checkpoint. Execute directly; do not delegate.

## Inspect

Read applicable `AGENTS.md` and root `MEMORY.md`.

Treat `workspace.local.toml` as the repository inventory source of truth. Before
reading `REPOS.md`, confirm that the manifest and `scripts/render-repos` exist,
then run `scripts/render-repos` from the workspace root. If either file is
missing or rendering fails, stop and report the problem clearly. Read the
manifest and generated `REPOS.md` only after rendering succeeds.

Use the conversation, existing handoffs, `git status`, relevant diffs, changed
files, and recent checks to determine:

- objective, decisions, and constraints
- completed and validated work
- current state, blockers, and next action

Prefer diffs and summaries. Inspect logs, artifacts, or unchanged files only
when needed to verify a material claim. Do not record unverified claims.

## Reflect and Persist

Briefly identify what went well, what failed or remains uncertain, and concrete
workflow improvements.

Persist only reusable information:

- `workspace.local.toml`: stable repository inventory, commands, and
  operational notes
- `MEMORY.md`: active priorities, durable facts, gotchas, and open follow-ups

Never edit generated `REPOS.md` directly. After changing
`workspace.local.toml`, run `scripts/render-repos` again. If rendering fails,
stop and report the failure.

Keep edits concise, evidence-backed, deduplicated, and current. Exclude raw
logs, routine output, temporary details, speculation, secrets, and task history.

Do not edit `AGENTS.md` without explicit approval. When a reusable rule is
warranted, include the exact proposal in the handoff.

## Validate

Review final diffs and reread changed workspace documents. Confirm that:

- persisted facts are supported
- `REPOS.md` reflects `workspace.local.toml`
- repository inventory and `MEMORY.md` retain separate roles
- no transient or unrelated content was added
- `AGENTS.md` remained unchanged unless approved
- the handoff is sufficient to continue

Do not rerun broad tests solely for the checkpoint.

## Handoff

Return a compact handoff with:

- `Objective`
- `Decisions and constraints`
- `Completed`
- `Validation`
- `Current state`
- `Open items and next step`
- `Workflow self-reflection`
- `Repository, memory, and workflow updates`

Under reflection, include what went well, what did not, and what can improve.
Under updates, report whether `workspace.local.toml`, generated `REPOS.md`,
`MEMORY.md`, and `AGENTS.md` changed, list changed workspace documents, and
include any pending `AGENTS.md` proposal.

Omit raw commands, logs, test output, and exploration history.

Use a compaction control only when explicitly available. Otherwise do not claim
compaction occurred or run `/compact` in a shell.

End with:

`Checkpoint complete - run /compact now.`
