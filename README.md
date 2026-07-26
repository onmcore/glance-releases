# Glance

Ultra-high-performance Git GUI for Windows.

[![Download for Windows](https://img.shields.io/github/v/release/onmcore/glance-releases?label=Download%20for%20Windows&color=2f6feb)](https://github.com/onmcore/glance-releases/releases/latest)

[English](README.md) | [한글](README.ko.md) | [日本語](README.ja.md) | [Deutsch](README.de.md)

![Glance browsing the Linux kernel repository — commit graph, commit detail, and diff staging](docs/manual/assets/gifs/repo-open.gif)

This repository hosts official Glance binary releases and release notes.

## About Glance

Glance is a Git GUI built from scratch with one obsession: **speed**. It stays snappy in repositories with millions of commits and hundreds of thousands of files, while keeping a tiny memory footprint.

Glance is **completely free to use right now — personal and commercial alike** — no trial timer, no feature lock, no account required. (A paid commercial license is planned for a future version; it won't affect what you've already got.)

Built solo — my day job is C++ game development, but I picked up Rust, Tauri, and Solid.js for this one, with a lot of AI pairing along the way.

### Highlights

- **Fast where others stall** — instant response on enterprise-scale monorepos; see it [in action](docs/manual/performance.md)
- **Light on memory** — not the gigabyte-hungry kind
- **Tauri runtime** — small installer, no Electron-sized footprint, with native touches like Windows taskbar progress on long-running operations
- **Full Git workflow** — branch, merge, rebase, stash, cherry-pick, blame, history visualization
- **Built-in conflict resolution** — a visual three-way [Merge Editor](docs/manual/workflows.md#resolving-conflicts) for merges, rebases, and cherry-picks
- **Interactive rebase, no terminal needed** — drag to reorder or squash commits right in the log, or use pick/reword/fixup/drop from a dedicated editor; see [Interactive rebase](docs/manual/workflows.md#interactive-rebase)
- **Native worktrees, as tabs** — check out another branch into its own folder without disturbing your current one, and switch between them from a tab strip instead of digging through a menu; see [Worktrees](docs/manual/workflows.md#worktrees)
- **Native Git LFS, locking included** — pure-Rust client, no external `git-lfs` binary; batched downloads and inline previews, plus built-in file locking and a [visual storage breakdown with one-click cleanup](docs/manual/workflows.md#lfs-storage-cleanup) that shows exactly where your space went (most Git GUIs leave both to the CLI); see [Git LFS](docs/manual/workflows.md#exploring-files)

### Who it's for

- Developers tired of Git GUIs that lag on large repos
- Anyone who prefers a focused, native-feeling tool over a browser in disguise
- Windows users who want a modern alternative to the usual suspects

## Download

Get the latest installer from the [Releases](../../releases) page.

### Release channels

| Channel | What it is | Where to get it |
|---|---|---|
| **Stable** | Tested releases. Recommended for daily use. | [Latest release](../../releases/latest) |
| **Preview** | Upcoming features, mostly stable. | [Pre-releases](../../releases) (marked *Pre-release*) |

Auto-update is built in — pick your channel under **Settings → Update**.

## Manual

New to Glance? The [manual](docs/manual/README.md) covers getting started, core workflows, keyboard shortcuts, and troubleshooting.

## Support Glance

Glance is free for everyone right now, commercial use included, with no strings attached. If it's useful to you, [consider a small donation](https://onmcore.github.io/glance-releases/sponsor.html) — entirely optional, and it goes a long way toward keeping development going.

## Bug reports & feedback

- Found a bug? [Open an issue](https://github.com/onmcore/glance-releases/issues/new)
- Have a feature idea? [Start a discussion](https://github.com/onmcore/glance-releases/discussions)

It's just me behind Glance — I read every report myself, so replies might take a day or two.

## License

Glance is currently free for everyone, including commercial use — no license key or payment required. Voluntary donations are welcome but optional. A paid commercial license is planned for a future version; it won't change versions already released under this agreement.

Unmodified redistribution is allowed; reverse engineering, modification, and repackaging are not (see [LICENSE](./LICENSE)). No warranty.

Third-party components and their licenses are listed in [THIRD_PARTY_LICENSES.md](./THIRD_PARTY_LICENSES.md).

---

**Glance** © 2026 onmcore
