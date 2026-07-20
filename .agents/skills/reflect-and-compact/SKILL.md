---
name: reflect-and-compact
description: Create a fast workspace checkpoint before compaction. Use only when explicitly asked to checkpoint, preserve context, update the repository inventory or MEMORY.md, improve workflow, or prepare for `/compact`.
---

# Reflect And Compact

Create a concise, trustworthy continuation checkpoint. Do not delegate.

## Inspect

Read applicable `AGENTS.md` and root `MEMORY.md`.

Treat `workspace.local.toml` as inventory source of truth. Confirm it and
`scripts/render-repos` exist, then render from the workspace root before reading
the manifest and generated `REPOS.md`. Stop and report missing files or render
failure.

Use the conversation, handoffs, Git status, relevant diffs, changed files, and
recent checks to establish the objective, decisions, constraints, validated
work, current state, blockers, and next action. Prefer diffs and summaries;
inspect other evidence only to verify material claims. Record no unverified
claims.

## Persist

Briefly capture successes, failures or uncertainty, and concrete workflow
improvements. Persist only reusable information:

- `workspace.local.toml`: stable inventory, commands, and operational notes
- `MEMORY.md`: active priorities, durable facts, gotchas, and open follow-ups

Never edit generated `REPOS.md` directly. Rerender after a manifest change; stop
and report failure. Keep edits concise, supported, deduplicated, and current.
Exclude raw logs, routine output, temporary details, speculation, secrets, and
task history.

Enforce a strict 100-line maximum for `MEMORY.md`; count before and after
editing. If over budget, prioritize active risks and next actions, then durable
facts and gotchas. Compact related details and remove stale, resolved,
redundant, or lower-priority material until it fits. Never truncate blindly.

Do not edit `AGENTS.md` without explicit approval. When a reusable rule is
warranted, include the exact proposal in the handoff.

## Validate

Review final diffs, reread changed workspace documents, and confirm:

- facts are supported; no transient or unrelated content was added
- `REPOS.md` reflects the manifest; inventory and memory retain separate roles
- `MEMORY.md` has at most 100 lines
- `AGENTS.md` remained unchanged unless approved
- the handoff supports immediate continuation

Do not rerun broad tests solely for the checkpoint.

## Handoff

Return a compact handoff with these sections: `Objective`; `Decisions and
constraints`; `Completed`; `Validation`; `Current state`; `Open items and next
step`; `Workflow self-reflection`; and `Repository, memory, and workflow
updates`.

In reflection, cover what went well, what did not, and improvements. In updates,
state whether the manifest, generated `REPOS.md`, `MEMORY.md`, and `AGENTS.md`
changed; list changed workspace documents and any pending `AGENTS.md` proposal.

Omit raw commands, logs, test output, and exploration history.

Use a compaction control only when explicitly available. Otherwise, neither
claim compaction occurred nor run `/compact` in a shell.

End with:

`Checkpoint complete - run /compact now.`
