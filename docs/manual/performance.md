# Performance

[English](performance.md) | [한글](performance.ko.md) | [日本語](performance.ja.md) | [Deutsch](performance.de.md)

Glance is built around one goal: staying responsive on large repositories.

## What that looks like

- Opening a repository with hundreds of thousands of commits doesn't block the UI — the commit graph is virtualized, so scrolling through it stays smooth instead of getting choppy as the list grows.
- Operations that touch a lot of files (rebase, merge, pull) don't trigger a full rescan afterward — Glance updates only what changed.
- Checkout, pull, and stash operations that only touch a known set of files skip walking the rest of the working tree, instead of scanning everything.
- File changes on disk (from Git, another tool, or the OS) show up in the UI without a noticeable lag.

## Why

- **Tauri v2 + Rust, not Electron.** No bundled Chromium runtime — smaller installer, lower baseline memory.
- **gitoxide (`gix`) as the primary Git engine.** Most operations run through a pure-Rust implementation instead of always spawning `git.exe`. Where gitoxide doesn't yet cover an operation, Glance falls back to `libgit2` or the Git CLI automatically.

<!-- TODO: once we have our own measured numbers (self-timed, large repo, no
     competitor comparison per current scope), add a results section here.
     See local promo-plan notes for the simple measurement checklist. -->

## See it in action

<!-- TODO: embed GIF — opening a large repository -->
