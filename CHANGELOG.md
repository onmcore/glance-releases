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

## [0.87.2] - 2026-09-20

### Added
- Cherry-pick a range of commits onto a branch you don't have checked out —
  the cherry-pick dialog now lets you choose the range, the target branch,
  and options in one place
- Force a status rescan with F5 (also in the Repository menu) when a change
  is not picked up automatically

### Changed
- Merge forecast for a tracking branch with incoming upstream changes now
  predicts the pull ("will pulling upstream conflict?") instead of always
  the merge into the default branch
- Faster status updates, commit details, and file previews in large
  repositories, with lower memory use

### Fixed
- Sparse checkout repositories: excluded files were shown as deleted,
  "Stage All" could stage them as deletions, and the index repair banner
  kept reappearing. Working-copy operations (checkout, merge, reset, stash,
  pull, rebase, cherry-pick, revert) are now delegated to Git so they no
  longer restore excluded files or fail, and committing in a sparse-index
  repository no longer writes a broken tree
- The cherry-pick dialog on a detached HEAD defaulted to another branch;
  it now applies to HEAD like the context menu does
- Merge forecast badges could linger after the branch's base or upstream
  was gone
- Inline spinners on "Stage All" and stash rows no longer drift across
  the row
- File changes could go undetected: a continuously written file (e.g. a
  log directory) kept resetting the change debounce so status never
  refreshed, and edits inside a nested repository (such as a worktree
  inside the main repository) were attributed to the outer repository
- Continuous writes to an untracked file no longer trigger a full index
  re-read every few seconds in large repositories
- Updated the TLS library (rustls) to fix a security vulnerability
  (RUSTSEC-2026-0285) in HTTPS connections used for Git LFS and updates

## [0.87.1] - 2026-09-06

### Added
- Cherry-pick a range of commits at once — pick "just this commit" or "from
  here to there", with conflict skip and options to pick onto a branch other
  than the one you're on
- Settings now shows a diagnostic card recommending Git config changes for
  very large repositories

### Changed
- Commit search returns results much faster in large repositories

### Fixed
- Git configuration changes (like disabling untracked-file scanning) now
  take effect immediately instead of requiring you to reopen the repository
- Cherry-pick could get stuck in an unresolvable state when there were
  unrelated uncommitted changes in the working copy
- Push and other operations that don't touch the working copy no longer
  trigger a full, slow rescan afterward
- Deleting a branch could leave the commit list stuck on "Loading commits"
  in large repositories
- Adding/removing a remote or a worktree no longer triggers a full, slow
  rescan afterward
- Editing branch tracking, remotes, or the push default no longer risks
  corrupting your `.git/config` if the app is interrupted mid-write
- Reduced app slowdowns and unresponsiveness right after startup in large
  repositories
- Checkout, commit, and merge no longer pause noticeably on large
  repositories using Git LFS
- Fixed a rare crash under very low system memory

## [0.87.0] - 2026-08-31

### Added
- Blame your working copy — right-click a file in Changes to blame it exactly
  as it is on disk, with uncommitted lines marked as such

### Changed
- Branches and tags in the sidebar are now sorted by most recent commit
- The PR/MR merge dialog asks "Squash commits?" as a single toggle when merge
  and squash are the only options (GitLab), instead of a segmented control
- Scanning for untracked files in large repositories is much faster
- Commit details now cap the file list at 10,000 files (with a truncated
  indicator) — huge merge commits could previously freeze the app

### Fixed
- The commit list could permanently stop loading more commits while scrolling
- Selecting a local branch left the commit list at the top instead of
  scrolling to that branch's latest commit
- Binary and LFS badges disappeared from collapsed files in the Review view

## [0.86.6] - 2026-08-21

### Added
- Review view — pick any range (your uncommitted changes, unpushed commits,
  or two arbitrary commits) and see it as one continuous diff, with a
  commit-range picker right in the log
- A banner appears when your Git configuration has disabled untracked-file
  scanning, so new files don't silently disappear from the Changes list

### Changed
- The right-click "Compare" view has been replaced by the more capable
  Review view — same idea, a broader range picker, and it now shares the
  same continuous-scroll diff view as staging
- Large repositories use noticeably less peak memory during full scans and
  background conflict-forecast checks

## [0.86.5] - 2026-08-15

### Added
- Image diffs now support a before/after comparison view (swipe or onion-skin
  overlay) for changed image files
- PR/MR mentions and review requests now also show as OS notifications, in
  addition to the in-app notification center

### Changed
- Full scans on large repositories are faster, using file-watcher-verified
  state to skip redundant disk checks
- GitLab merge requests that need a rebase now reflect that in the merge and
  "update branch" button states

### Fixed
- Notifications for PR/MR mentions and review requests could reappear
  repeatedly, or dump a backlog of old notifications right after signing in
- Commit search by hash required an exact 7-character prefix; longer or
  full-length hashes now match too
- Switching commits quickly in the diff view could leave a file stuck
  showing "modified" with no visible changes
- Very large repositories could run out of memory during a full scan
- The reviewer avatar in inline PR comment cards could overflow the card
  width
- Unity `.meta` pair integrity checks could misfire in some cases (missed
  real issues or flagged false positives)
- Viewing a local branch with no upstream could show an incomplete commit
  graph, without a visible point where it diverged from the default branch
- Inline PR comment code snippets ignored your diff view's font size and
  color settings

## [0.86.4] - 2026-08-09

### Added
- Sign in to GitLab directly from your browser (no personal access token needed)
- Create and merge pull/merge requests from within Glance, with a confirmation
  step and provider-aware handling of "delete source branch"
- PR/MR lists, CI checks, and inline comments now refresh automatically on a
  configurable interval (or manually), instead of only when you open the tab
- Rate-limit errors from GitHub/GitLab now show a clear message and recovery
  time instead of being mistaken for access-denied errors
- Inline PR comment threads that no longer match the current diff now also
  appear in the Review tab feed, with the original code snippet for context
- LFS upload size is now estimated and shown before you push
- The Merge Editor shows a conflicted file's size and whether it's an LFS
  pointer before you start resolving it
- An "Update branch" button appears on PRs that are behind their target
  branch, and the Approve button is now a promoted, always-visible action
- @mentions in PR/MR comments are rendered as links, and emoji shortcodes
  render as emoji
- Commit author avatars now fall back to your GitHub/GitLab profile photo
  when no Gravatar is available
- PR/MR mentions and review requests now show up in the notification center
- Unity `.meta` sidecar files are now checked for missing/orphaned pairs,
  shown as a badge in the Changes list

### Changed
- Conflict radar's binary-file detection now distinguishes definite, probable,
  and unknown cases instead of treating all binary-like files the same

### Fixed
- LFS quota-exceeded errors were reported as generic failures instead of the
  actual reason
- Comparing two refs with a very large number of changed files could freeze
  the UI
- The sidebar's ahead/behind counts could stay stuck at pre-push values after
  pushing
- Opening a row's details in the Op History timeline could crash the panel
- The Continue/Abort buttons for an in-progress operation could get stuck
  permanently disabled
- Repos with a custom Git merge driver configured could get conflict markers
  merged into files, or silently incorrect results, during merge, pull,
  rebase, cherry-pick, revert, or stash

## [0.86.3] - 2026-08-06

### Added
- Merge conflict forecast — a badge on branches and log labels shows
  whether merging into the default branch would conflict, kept live
  automatically
- Conflict prevention radar — warns in the Changes list and commit panel
  when a file you're editing was also changed on a teammate's recently
  active branch
- Pull request review status is now shown in the PR header strip and as
  review cards (approvals, pending reviewers)
- Inline PR comments — read and write line-level comments on diff lines,
  reply to threads, resolve/unresolve, and edit or delete your own
  comments

### Fixed
- Switching repositories could leave the previous repository's Changes
  list showing until the new one finished scanning
- The repository list popup could stop responding to clicks
- The forge account setup's "verified" message could show the wrong
  provider after switching services; GitLab personal access token
  creation now also pre-fills the description field

## [0.86.2] - 2026-08-03

### Added
- GitHub/GitLab integration — link accounts via device flow, personal access
  token, or a self-hosted instance; browse PR/MR lists and details with CI
  check status and file diffs; switch accounts per repository from the
  sidebar chip
- Personal access token setup now opens the provider's token page with the
  name and required scopes pre-filled
- (Beta) Submit PR/MR reviews — approve, request changes, or comment — and
  follow the activity timeline

### Changed
- LFS store analysis is much faster and now resumes incrementally instead
  of re-scanning your entire history on every fetch
- Blame now uses the built-in gix engine by default
- Enumerating LFS objects to upload on push is faster
- LFS cleanup analysis reuses cached results instead of re-walking history
  on every recompute

### Fixed
- LFS store analysis results could disappear after a full scan completed,
  or when switching between repositories
- Blame could attribute lines to the commit that renamed a file instead of
  the commit that actually changed them
- The push dialog's set-upstream toggle stayed disabled after the upstream
  branch was deleted on the remote

## [0.86.1] - 2026-07-31

### Added
- CSV/TSV diffs are now table-aware — cell-level change highlighting,
  column-aligned layout, a pinned header row, and (in the unified view)
  folding of unchanged columns
- The unified diff view now marks the file currently selected in the sidebar

### Changed
- LFS store analysis shows real progress percentages and no longer blocks
  push/commit while it runs

### Fixed
- Various fixes across staging, file-change watching, merge/cherry-pick/revert,
  and sync

## [0.86.0] - 2026-07-27

### Added
- Interactive rebase — reorder, reword, squash, fixup, or drop commits from a modal with drag-and-drop, then run the plan; available from a commit's context menu, a branch's context menu, or by dragging a commit in the log
- LFS store analysis & cleanup — see local Git LFS storage usage broken down by folder and extension, classified as in-use / retained / old versions / unreferenced, and clean up unreferenced or superseded objects that are safely backed up remotely (including per-folder cleanup); a remote fetch runs automatically first so "backed up" status is current
- Code font selection — choose the font used for code and diffs independently of the general UI font, with a searchable picker and live preview
- Code font size — adjust code/diff text size independently of the overall UI zoom

### Fixed
- LFS file locking could fail with an authentication error when locking or unlocking a file
- The LFS locks list could show a single lock duplicated many times over
- Branch/tag labels on a commit could appear duplicated
- Rapidly clicking between branches on a large repository could make the commit log hang for minutes while memory usage spiked, and a related background retry loop could fire continuously
- Soft and mixed reset now also update the Changes panel instantly
- Performance improvements — file-change detection no longer temporarily slows to full rescans right after a Git operation completes

## [0.85.6] - 2026-07-23

### Added
- Git LFS file locking — view locks, lock/unlock (including force-unlock) from the file explorer and Changes panel, with lock badges and a "locks only" filter
- LFS tracking guardrail — large binary files not tracked by LFS are flagged with a badge in the Changes list, with a "track with LFS" action (non-blocking; size threshold and on/off in Settings)
- Windows taskbar progress — operation progress (checkout, pull, push, …) now shows on the taskbar icon even when the window is minimized or in the background
- Diff pane file headers now have stage checkboxes synced with the sidebar, and file collapse state survives view switches

### Changed
- Dark theme retuned to neutral grays for a more consistent look
- Commit detail: co-author trailers are now highlighted while the original message body is preserved as written

### Fixed
- Editing .gitignore now takes effect in the Changes view immediately
- The Changes header discard button now only discards the files currently shown, not files hidden by filtering
- Performance improvements — fewer redundant full rescans after cherry-pick/revert and during heavy repository churn, and faster reflection of detected changes on very large repositories

## [0.85.4] - 2026-07-21

### Added
- Worktree tabs — all worktrees now appear as tabs in a global strip below the title bar (create with ＋, delete via right-click), replacing the sidebar worktree selector
- Secondary (split) window diff tab now uses the unified multi-file view — every changed file in one continuous scroll
- Changes panel: Staged/Unstaged section headers stay pinned while scrolling and can be collapsed; the view-mode toolbar is pinned to the top
- Current branch context menu: new "Rebase onto upstream" action

### Changed
- LFS files are now marked with a compact "LFS" chip instead of a verbose description
- Commit graph is now incrementally refreshed as refs change, keeping the commit log fast on very actively-committed repositories

### Fixed
- Performance improvements — eliminated redundant repeated full rescans on very large repositories, and unnecessary stash list re-renders on refresh
- Operation history log: rapid CLI progress updates (e.g. during a hard reset) no longer collapse into a single line
- Busy indicators for tag/remote-branch deletion and submodule operations now pulse instead of appearing frozen
- Reset shows a flowing progress bar when progress is indeterminate, instead of an empty static track
- Branch operation progress bar pacing corrected — a paused bar could look finished, and the preparing phase moved unrealistically fast

## [0.85.3] - 2026-07-19

### Added
- Unified (multi-file) diff view now supports word-level diff highlighting, per-field CSV coloring, and indent guides — previously only available in the single-file view; word-diff highlight contrast also increased for readability

### Changed
- In-progress git operation status is now shown entirely inline (branch row, commit detail conflict banner, toolbar hover, sidebar tab) instead of a status chip at the bottom of the window
- Improved reliability of file-change detection inside Git-ignored folders — changes are no longer missed, and unnecessary background rescans are reduced

### Fixed
- Changes panel could keep showing an already-reverted or already-committed file as modified; now clears as soon as you view its diff
- Committing from outside Glance (another Git client, or an AI coding agent) no longer triggers a slow full rescan or leaves phantom modified files while it catches up
- Auto-fetch no longer runs at the same time as a large background scan, avoiding slowdowns

## [0.85.2] - 2026-07-18

### Added
- Merge, Cherry-pick, and Revert now run on the gix (pure-Rust) engine by default (previously CLI/libgit2 for some cases) — same behavior, other engines remain selectable per feature in Settings
- Cherry-pick / Revert now tells you when a commit was already applied or reverted, instead of silently doing nothing
- Changes panel now updates instantly after stash, commit, merge, cherry-pick, revert, checkout, pull, and hard reset, instead of waiting for the background rescan to catch up
- "Rescan scheduled" indicator now shows an hourglass with a countdown to when the scan will run
- Unified diff view (split mode): horizontal scroll for long lines, synced between both sides and pinned to the bottom; click a collapsed gap to expand it

### Fixed
- Commit list could occasionally get stuck or show a stale "incoming" indicator when many refresh signals arrived in quick succession (e.g. during a merge)
- Fixed a rare case where newly created files could permanently fail to appear in the Changes view when a background scan overlapped with certain operations
- Fixed some HEAD movements not being recorded in the reflog, which could make them missing from Timeline
- Welcome screen now respects the selected UI language, instead of always showing Korean text

## [0.85.1] - 2026-07-17

### Added
- Fetch results summary toast — shows what came in (new/updated/deleted branches and tags) after a fetch; multiple remotes merge into a single card
- Toggle to disable decorative animations while keeping progress/status motion (Settings > Appearance)
- Unified multi-file diff view — see every changed file in one continuous scroll, in both the commit detail's Changed Files tab and the Changes tab; supports line-drag staging in unified and split layouts, separate Staged/Unstaged sections, binary-file size cards, and the encoding/EOL chip
- Pull now offers to stash uncommitted changes and automatically retry when they'd otherwise block the operation — works with any pull strategy or engine, and restores your changes if the retry still fails
- "Rescan scheduled" status now shows as a clearer slow spinner instead of an easy-to-miss breathing dot, and appears during more kinds of scan delays

### Changed
- New app icon

### Fixed
- App could hang for minutes and consume excessive memory when an external process rewrote the repository rapidly (e.g. another tool churning HEAD/refs/index); overlapping duplicate reads are now coalesced into a single call
- Git config viewer now reads system-scope config and includes, so effective values (e.g. autocrlf) display correctly instead of showing "not set"
- Submodule log: selecting a commit now correctly shows its details, changed files, and diff
- Sidebar submodule "update available" badge now stays in sync with the Changes panel
- "Discard all changes" is now disabled in the branch context menu when there are no changes, matching the Changes panel
- Update channel badge spacing, and context menu tooltips no longer cover submenu flyouts
- Push rejected by a server-side hook now shows the actual rejection reason directly in the toast, instead of only in the operation history
- Changes panel could show stale modified files for up to ~2 minutes after a successful rebase on large repositories; it now clears in seconds
- Bug report modal no longer stretches to fill the screen when pasted error text contains very long unbroken tokens
- Submodule log commit menu: actions that would modify the parent repository are now disabled; Compare and Export Patch now correctly target the submodule
- No longer shows a false "crash reported" prompt for a harmless browser resize-loop warning
- Files staged by an external tool could vanish from the Changes view for a long time after a checkout that preserved staged changes (e.g. pull/merge fast-forward)
- Sync could loop forever retrying pull/push when a push was rejected for a reason pull couldn't actually fix (e.g. a rejected server hook, a duplicate tag); retries are now capped with a safety net
- Fixed rare cases where Glance would keep rescanning a repository without end when an external tool (e.g. an AI agent) rewrote the repository faster than a scan could finish
- Fixed newly created files sometimes never appearing in the Changes view when created at the same moment as an external git operation

## [0.85.0] - 2026-07-12

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
