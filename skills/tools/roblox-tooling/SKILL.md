---
name: roblox-tooling
description: "Use when configuring Roblox tooling such as Rojo, Wally, pesde, Selene, StyLua, Lune, Rokit, luau-lsp, or CI/CD."
last_reviewed: 2026-10-02
sources:
  - https://raw.githubusercontent.com/Roblox/creator-docs/main/content/en-us/reference/engine/classes/Players.yaml
  - https://rojo.space/docs/
  - https://wally.run/
  - https://kampfkarren.github.io/selene/
  - https://raw.githubusercontent.com/JohnnyMorganz/StyLua/master/README.md
  - https://lune-org.github.io/docs/
  - https://raw.githubusercontent.com/LPGhatguy/aftman/main/README.md
  - https://raw.githubusercontent.com/rojo-rbx/rokit/main/README.md
  - https://raw.githubusercontent.com/rojo-rbx/rojo/v7.7.1/src/cli/syncback.rs
  - https://raw.githubusercontent.com/pesde-pkg/pesde/main/docs/src/content/docs/reference/manifest.mdx
  - https://raw.githubusercontent.com/JohnnyMorganz/luau-lsp/main/README.md
  - https://create.roblox.com/docs/llms.txt
  - https://create.roblox.com/docs/reference/engine/llms.txt
  - https://create.roblox.com/docs/cloud/llms.txt
  - https://create.roblox.com/docs/llms-full.txt
  - https://create.roblox.com/docs/reference/engine/deprecated.md
  - https://devforum.roblox.com/t/evolving-luau-oss-community-contributions-more/4566806
  - original
---

# roblox tooling

## When to Load

Load when setting up a filesystem workflow, pinning tools, adding packages, configuring lint or format checks, generating a sourcemap, or building CI for a Roblox project.

## Quick Reference

- Use Rojo when the source of truth should live in files and sync or build into Studio.
- Use Wally only when the project wants package manifests and a lockfile; keep package scope and server/client placement explicit.
- Pin tools with the project's existing manager; for a new project lead with Rokit (Aftman is archived, but Rokit reads existing `aftman.toml` projects).
- Run Selene and StyLua in check mode in CI. Do not let a formatter rewrite a contributor's branch silently.
- Use Lune for standalone Luau scripts or test helpers when its standard libraries fit the task.
- Generate a Rojo sourcemap for editor tooling when the project needs Roblox-aware navigation.

**Source-of-truth first.** Know whether the place lives in Studio, in files (Rojo), or in a bidirectional sync before editing; never assume both sides match. `rojo syncback` pulls saved-place edits into files (dry-run/list first); it is a file pull, not live two-way sync. Name optional tools (Selene, StyLua, luau-lsp, Lune, Wally, pesde) when relevant; TestEZ is archived and belongs only in projects already using it. Do not impose a tool on a project that does not use it. Details in `references/full.md` §§1b–1c.

**Need the details?** Load `references/full.md` for setup, file layout, and CI examples.
