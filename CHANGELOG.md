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

The first public release of Glance — a high-performance Git GUI for Windows.

Built on gitoxide (pure-Rust Git) and Tauri, Glance is designed to stay fast and
lightweight even on very large repositories: a virtualized history that scrolls
smoothly across hundreds of thousands of commits, sub-second status, and checkouts
and resets that touch only the files that actually changed.

### Repositories & worktrees
- Open local repositories or clone remotes, with live progress and background multi-clone; URL typo checks, a stall warning, and forceful cancel if a clone gets stuck
- Recent-repository list with auto-restore, a quick repository switcher, and close/remove
- Multi-worktree support: inline switching, add/remove, and worktree-aware checkout
- Automatic detection of external Git CLI changes (branches, tags, config, submodules)
- Built-in bottom terminal (Git Bash)
- Open the repository folder in File Explorer from the Repository menu

### History & graph
- Virtualized commit list that stays smooth on very large histories
- Commit graph with a refs sidebar (branches, remotes, tags), HEAD highlight, and ahead/behind; a first-parent view toggle and a lane-width cap keep merge-heavy histories readable
- Commit search & filter by message, author, or hash (Ctrl+F)
- Combined multi-branch history (Incoming / Outgoing) and a stash graph
- Commit detail panel — info, files, change stats, and diff — with hover preview
- Compare any two branches, tags, or commits — full file list and per-file diff
- Gravatar avatars

### Diff viewer
- Unified and Split views with multi-language syntax highlighting
- Stepwise context expansion and a hunk navigator (`[` / `]`)
- Multiple independent split windows (tabs plus a synced file explorer)
- File encoding and line-ending (LF/CRLF) display with one-click conversion
- Whitespace-ignore toggle
- Per-field CSV coloring
- External diff/merge tool integration (VS Code, Beyond Compare, KDiff3, WinMerge, P4Merge, and more) with auto-detection
- Binary file changes show a size card (old → new, with a delta) instead of a plain "can't display" message

### Staging & changes
- Stage / unstage by file, folder, or all at once
- Precise line- and hunk-level staging (drag multi-select; separated Staged / Unstaged)
- Discard by file or by hunk
- Real-time change detection with a status-bar scan progress indicator; scans adapt to system load and defer politely when the window is unfocused or the machine is busy
- Changes view in Flat / Group / Tree layouts, with change-type badges (A/M/D/?/!)
- Guards against stale external edits and CRLF / binary corruption

### Commit
- Separate title and body, with sign-off
- Amend the previous commit's message, content, and author, with per-file unstage
- Co-authors (Co-authored-by) — display, add, and edit on commit and amend
- SSH commit signing (pure Rust)
- Commit during a merge, with an auto parent and a pre-filled message
- Dynamic "Commit All / Commit Staged" button

### Branches, tags & merging
- Create / checkout / delete / rename branches; checkout remote branches with auto-tracking
- Delete and push tags
- Merge (fast-forward and non-fast-forward) with conflict detection
- 3-way visual conflict editor (Ours / Base / Theirs) — Split / Unified views, clear conflict markers, inline hunk editing, and an abort button always at hand
- Rebase onto a local or remote branch
- Per-branch operation indicators (checkout / pull / push / rebase / sync progress), including a live pre-check scan phase on large worktrees

### Remotes & sync
- Add / remove / edit remotes (separate fetch & push URLs, default push target)
- Fetch, manually or via background auto-fetch (skips itself on a busy machine)
- Push, including force and force-with-lease
- Pull — Merge (FF), Rebase, or 3-way Merge with conflict resolution
- One-click Sync (pull then push) with retry feedback
- Private-repository auth via HTTPS credential manager or SSH agent
- Push / Pull / Sync always target the checked-out branch and its tracked upstream

### Advanced tools
- Stash — create, pop, apply, drop; includes untracked files; graph display
- Cherry-pick and Revert, with conflict detection and auto-abort
- Reset (Soft / Mixed / Hard), auto-cleaning any in-progress state; hard reset rewrites only changed files, staying fast on huge worktrees
- Discard all changes back to HEAD in one step, with a confirmation step — no commit selection required
- Export commits as .patch files and apply .patch/.diff files to the worktree — share changes without a remote
- Restore a single file to its state at any commit, right from the file history or a commit's file list
- Per-file history and per-line Blame

### File explorer
- Per-branch file tree in Flat / Group / Tree layouts, with file-format icons; directories load lazily, so even multi-million-file trees open instantly
- Single-file full view, Markdown rendering, inline image preview, and a sortable CSV table

### Git LFS
- Native Git LFS (pure Rust) — automatic pointer / content conversion, batched download of missing content on checkout / reset / discard, inline image preview with on-demand download, and progress for batch negotiation and cache restore
- Option to delegate downloads to the git-lfs CLI instead of the built-in transfer, for advanced/custom setups

### Timeline & operation history
- Timeline — a HEAD reflog visualization with non-destructive recovery (branch-at-point, checkout, revert, one-click undo)
- Operation history — step timelines, durations, logs, and live memory usage for every write operation

### Settings & ecosystem
- Localization (Korean / English / Japanese / German, with OS auto-detect) and dark / light theme (OS-linked)
- Submodules — list, add, init, update
- Git config management — view / edit, with per-repository identity override
- SSH key management — generate Ed25519 / RSA keys, edit ~/.ssh/config hosts, and manage known_hosts (trust new host keys on first use, view/add/remove trusted hosts, in-flow trust prompt with auto-retry when an operation fails on an untrusted host)
- Command Palette (Ctrl+P) — search and run any menu command by typing
- Keyboard shortcuts and per-feature Git engine selection (gix / libgit2 / CLI)
- Diff algorithm selection (Histogram / Myers / Minimal)
- Collapsible sidebar, About dialog, and an in-app open-source license viewer

### Updates & licensing
- Automatic updates with a notification center
- Free to use; voluntary donations welcome via Ko-fi (Help menu or About dialog)

### Reliability & recovery
- Resilient live updates — the file watcher auto-restarts and warns if it becomes unresponsive
- Automatic detection and repair of a corrupted Git index or HEAD, including stale index metadata that would force full rescans
- Automatic in-place recovery if the embedded WebView crashes
- Detects when Windows Defender is measurably slowing Git operations and offers a shortcut to the exclusion settings
- One-click bug reporting from the Help menu or an error toast — attach logs and a screenshot (both optional, with a preview before sending), no GitHub account needed
- If Glance crashes, you're asked every time before anything is sent — nothing is stored or sent without that per-crash confirmation (no personal data beyond a scrubbed Windows username)
