# Core Workflows

[English](workflows.md) | [한글](workflows.ko.md)

## Browsing history

The **Branches** tab shows the commit graph — a virtualized list that stays smooth even at hundreds of thousands of commits. The sidebar's refs tree lists branches, remotes, tags, and stashes; selecting one filters or jumps the graph.

- `Ctrl+F` opens search — filter commits by message, author, or hash
- Right-click a commit for actions: checkout, create branch, cherry-pick, reset, compare
- Toggle **All Branches** to see the entire history as one flat list instead of just the current branch's ancestry
- Hovering a commit shows a quick preview; clicking opens full details (Info / Changes tabs) in the right panel

![Commit graph with refs sidebar](assets/screenshots/hero.png)

## Staging & committing

The **Changes** tab is your working directory staging area, split into **Staged**, **Unstaged**, and **Conflicts** (when present) sections. Switch between Flat, Grouped, and Tree layouts depending on how you like to scan a large changeset.

- Check a file or folder to stage/unstage it; checkboxes support `Ctrl`/`Shift` multi-select
- Open a file's diff to stage or discard individual hunks or lines, not just whole files
- Discard is available at the file or hunk level
- Write your commit message in the panel below and submit with `Ctrl+Enter`

Changes are detected in real time by a file watcher — no manual refresh needed.

![Changes panel with hunk-level staging](assets/screenshots/staging.png)

## Branching & merging

Create, checkout, rename, and delete branches from the sidebar or the Branch menu. Checkout shows progress for large repos and only touches the paths that actually changed.

- **Merge** a branch into the current one (fast-forward or a real merge commit); conflicts, if any, open the Merge Editor
- **Rebase onto** a branch or commit — progress is shown phase-by-phase (checking out, replaying commits, etc.)
- **Cherry-pick** a commit onto the current branch from its context menu
- **Tags** can be created, deleted, and pushed individually; annotated tag messages are viewable inline

### Stashing

Stash uncommitted changes from the Branch menu (**Stash Changes...**), optionally keeping staged changes in the working tree. Stashes appear in the sidebar's Stashes section and in the commit graph. Each stash supports:

- **Pop** — apply and remove
- **Apply** — apply but keep the stash
- **Drop** — delete without applying

### Resolving conflicts

Whenever a merge, rebase, or cherry-pick hits a conflict, Glance opens the **Merge Editor** — a three-way view (Ours / Base / Theirs) with `[` / `]` to jump between conflicts. Resolve, then continue or abort the operation from the same view.

![Merge Editor three-way view](assets/screenshots/merge-editor.png)

## Remote sync

Add, edit, or remove remotes from the sidebar. Fetch runs on demand or automatically in the background (default every 3 minutes — adjustable in Settings). Push supports force and force-with-lease. Pull can merge (fast-forward or three-way, with conflict resolution) or rebase.

### SSH remotes

For SSH-based clone/fetch/push, set up a key under **Settings → SSH Keys**:

1. **Generate a key** — pick an algorithm (Ed25519 recommended), name it, and create
2. Copy the public key into your Git host (GitHub/GitLab/etc.)
3. Under **Host configuration**, add a host entry (HostName, User, Port, IdentityFile) — this edits your real `~/.ssh/config`, so existing entries and directives Glance doesn't know about are preserved
4. The first time you connect to a new host, Glance prompts you to trust its SSH host key (TOFU) under **Known hosts** — same idea as `ssh`'s first-connection prompt

![SSH Keys settings section](assets/screenshots/ssh-keys.png)

## Comparing refs

Right-click any commit, branch, or tag for **Compare** — view the file-level diff between two arbitrary refs, independent of your current checkout. Toggle between two-dot (`a..b`) and three-dot (`a...b`, merge-base) comparison, and swap sides.

## Exploring files

The **File Explorer** tab browses the full repository tree (not just changed files), in Flat, Grouped, or Tree layout. Opening a file shows its contents with syntax highlighting; Markdown files can toggle between raw and rendered preview, and CSV files between raw text and a sortable table.

From a file's context menu you can also view its **history** (every commit that touched it) or its **blame** (line-by-line author/commit annotations).

## Timeline

The **Timeline** tab is a chronological feed of your repository's reflog — every place HEAD has pointed, across checkouts, commits, merges, rebases, resets, and pulls. It's a safety net independent of your visible branch history. From any entry you can:

- **Checkout** that point directly
- Create a **new branch** from it
- **Cherry-pick** its commit onto your current branch
- **Reset** the current branch to it
- **Undo** the last recovery action, if you just used Timeline to fix a mistake

![Timeline reflog feed](assets/screenshots/timeline.png)

---

Next: [Keyboard Shortcuts](shortcuts.md)
