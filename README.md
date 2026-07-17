# Multi-Repository Codex Workspace

This repository provides a reusable coordination layer for people who work
across multiple, independent Git repositories. It tracks shared instructions,
portable agent configuration, and small setup tools. It does not track child
repositories, repository inventory, or working memory.

## Set up a workspace

```sh
git clone <workspace-repository-url> codex-workspace
cd codex-workspace
scripts/init-workspace
```

Edit `workspace.local.toml` to describe your repositories, then run:

```sh
scripts/render-repos
```

The generated `REPOS.md` gives agents local repository context. `MEMORY.md` is
private working memory. Both files, the local manifest, and all repository
checkouts are ignored by Git.

The scripts never clone, update, or modify child repositories. Clone them at
the paths declared in your local manifest using your normal access method.

## Local manifest

Each `[[repositories]]` entry supports:

- `name`: display name
- `path`: workspace-relative checkout path
- `remote`: optional clone URL shown in the generated inventory
- `purpose`: optional short description
- `test_command`: optional project check command
- `notes`: optional operational notes

See `workspace.example.toml` for fictional examples.
