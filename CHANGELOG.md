# Changelog

User-facing change history for Glance. This project follows
[Keep a Changelog](https://keepachangelog.com/en/1.1.0/) and
[Semantic Versioning](https://semver.org/).

<!--
Release notes management (Model A — single file):
- During development, accumulate user-facing changes under [Unreleased] as Added / Changed / Fixed.
- Preview (pre-release) builds use [Unreleased] verbatim as the release notes (no section promotion).
- On a stable release, promote [Unreleased] -> "## [X.Y.Z] - YYYY-MM-DD" and add a fresh empty [Unreleased] on top.
- The build script slices the relevant section into the GitHub Release body + in-app updater notes.
- Notes are written in English. Rules & checklist: G-Lance-2/docs/release.md.
-->

## [Unreleased]

The **first public release** of Glance.
Glance is a **high-performance Git GUI for Windows** that stays responsive even on large
repositories (100k+ commits, tens of thousands of files), built on gitoxide (gix) — a pure-Rust
Git implementation. Designed for a light memory footprint with high frame rates and fast response.

### Added

**Repositories & Worktrees**
- Open local repositories + clone remotes (live progress, background multi-clone)
- Recent repository list & auto-restore, repository switcher dropdown, close/remove repository
- Native multi-worktree support — inline switching, add/remove (with safety checks), worktree-aware checkout
- Auto-detect external Git CLI changes (branches, tags, config, submodules) and reflect them in the UI instantly
- Built-in bottom terminal (Git Bash tab)

**Commit History & Graph**
- Virtualized commit list that stays smooth at 100k+ commits (infinite scroll)
- Commit graph + refs sidebar tree (branches, remotes, tags; HEAD highlight; ahead/behind counts)
- Commit search & filter (message, author, hash; Ctrl+F; navigate results with up/down)
- Combined multi-branch history with Incoming/Outgoing distinction, stash commit graph
- Commit detail panel (info, file list, change stats, diff) with hover quick-preview
- Gravatar author avatars

**Diff Viewer**
- Unified / Split view toggle, multi-language syntax highlighting
- Stepwise context-gap expansion, hunk navigator (`[` / `]`)
- Multiple split windows (independent tabs + synced file explorer)
- Per-field CSV coloring

**Staging & Change Management**
- Stage / unstage by file, folder, or all
- **Line / hunk-level precise staging** (drag multi-select, separated Staged / Unstaged model)
- Discard changes by file or hunk
- Real-time change detection (reflected within ~1s) + status-bar scan progress
- Changes tree view (Flat / Group / Tree), change-type badges (A/M/D/?/!)
- Guards against stale external edits and CRLF / binary corruption

**Commit**
- Separate title / body input, sign-off
- Amend (edit the previous commit's message, content, and author; per-file unstaging)
- Commit during a merge (auto parent + pre-filled message)
- Dynamic "Commit All / Commit Staged" button

**Branches & Merging**
- Create / checkout / delete / rename branches; checkout remote branches (auto-tracking)
- Merge (fast-forward / non-FF, conflict detection)
- **3-way visual conflict resolution editor** (Ours / Base / Theirs, inline hunk editing, resolution progress)
- Rebase onto a branch (local / remote)

**Remotes & Sync**
- Add / remove / edit remotes (separate fetch & push URLs, default push config)
- Fetch (manual + background auto-fetch)
- Push (incl. force / force-with-lease)
- Pull — Merge (FF) / Rebase / 3-way Merge (conflict resolution)
- Private repository auth (HTTPS credential manager / SSH agent)

**Advanced Git Tools**
- Stash (create, pop, apply, drop; includes untracked; graph display)
- Cherry-pick / Revert (conflict detection, auto-abort)
- Reset (Soft / Mixed / Hard, auto-cleans in-progress state)
- File history (per-file change log), Blame view (per-line authorship)

**File Explorer**
- Per-branch full file tree (Flat / Group / Tree), file-format icons
- Single-file full view (Blob), Markdown rendering, sortable CSV table

**Timeline & Operation History**
- Timeline — HEAD reflog visualization + non-destructive recovery (branch-at-point / checkout / revert + 1-click undo)
- Operation history — accumulated step timelines, durations, and logs for every write operation

**Settings & Ecosystem**
- Localization (Korean / English / Japanese, OS auto-detect), dark / light theme (OS-linked)
- Native Git LFS support (pure Rust, automatic pointer / content conversion)
- Submodules (list, init, update)
- Keyboard shortcuts, per-feature Git engine selection (gix / libgit2 / CLI)
- Responsive sidebar collapse, About & in-app open-source license viewer

**License & Updates**
- Automatic updates + notification center
- Free for personal / non-commercial use, paid for commercial use — dual license (Settings > License)

**Error Recovery**
- Automatic detection & repair of a corrupted Git index / HEAD
