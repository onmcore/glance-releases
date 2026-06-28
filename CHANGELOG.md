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

Glance — the first public release. A high-performance Git GUI for Windows built on
gitoxide (pure-Rust Git), designed to stay lightweight and fast on large repositories.

### Repositories & worktrees
- Open local repositories / clone remotes (live progress, background multi-clone)
- Recent-repository list & auto-restore, repository switcher, close/remove
- Multi-worktree support (inline switching, add/remove, worktree-aware checkout)
- Auto-detect external Git CLI changes (branches, tags, config, submodules)
- Built-in bottom terminal (Git Bash)

### History & graph
- Virtualized commit list that stays smooth on large histories
- Commit graph + refs sidebar (branches, remotes, tags; HEAD highlight; ahead/behind)
- Commit search & filter (message, author, hash; Ctrl+F)
- Combined multi-branch history (Incoming/Outgoing), stash graph
- Commit detail panel (info, files, change stats, diff) with hover preview
- Gravatar avatars

### Diff viewer
- Unified / Split views, multi-language syntax highlighting
- Stepwise context expansion, hunk navigator (`[` / `]`)
- Multiple split windows (independent tabs + synced file explorer)
- File encoding & line-ending (LF/CRLF) display with one-click conversion
- Per-field CSV coloring

### Staging & changes
- Stage / unstage by file, folder, or all
- Precise line- and hunk-level staging (drag multi-select, separated Staged / Unstaged)
- Discard by file or hunk
- Real-time change detection + status-bar scan progress
- Changes view (Flat / Group / Tree), change-type badges (A/M/D/?/!)
- Guards against stale external edits and CRLF / binary corruption

### Commit
- Separate title / body, sign-off
- Amend (edit the previous commit's message, content, and author; per-file unstage)
- Commit during a merge (auto parent + pre-filled message)
- Dynamic "Commit All / Commit Staged" button

### Branches & merging
- Create / checkout / delete / rename branches; checkout remote branches (auto-tracking)
- Merge (fast-forward / non-FF, conflict detection)
- 3-way visual conflict editor (Ours / Base / Theirs, inline hunk editing, progress)
- Rebase onto a branch (local / remote)

### Remotes & sync
- Add / remove / edit remotes (separate fetch & push URLs, default push target)
- Fetch (manual + background auto-fetch)
- Push (incl. force / force-with-lease)
- Pull — Merge (FF) / Rebase / 3-way Merge (conflict resolution)
- Private-repository auth (HTTPS credential manager / SSH agent)
- Push / Pull / Sync always target the checked-out branch and its tracked upstream

### Advanced tools
- Stash (create, pop, apply, drop; includes untracked; graph display)
- Cherry-pick / Revert (conflict detection, auto-abort)
- Reset (Soft / Mixed / Hard, auto-cleans in-progress state)
- Per-file history, per-line Blame

### File explorer
- Per-branch file tree (Flat / Group / Tree), file-format icons
- Single-file full view, Markdown rendering, sortable CSV table

### Timeline & operation history
- Timeline — HEAD reflog visualization + non-destructive recovery (branch-at-point, checkout, revert, one-click undo)
- Operation history — step timelines, durations, and logs for every write operation

### Settings & ecosystem
- Localization (Korean / English / Japanese, OS auto-detect), dark / light theme (OS-linked)
- Native Git LFS (pure Rust, automatic pointer / content conversion)
- Submodules (list, init, update)
- Keyboard shortcuts, per-feature Git engine selection (gix / libgit2 / CLI)
- Collapsible sidebar, About & in-app open-source license viewer

### Updates & licensing
- Automatic updates + notification center
- Free for personal / non-commercial use, paid for commercial use (dual license)

### Reliability & recovery
- Resilient live updates (file watcher auto-restarts; warns if unresponsive)
- Automatic detection & repair of a corrupted Git index / HEAD
