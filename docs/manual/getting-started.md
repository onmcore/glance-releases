# Getting Started

[English](getting-started.md) | [한글](getting-started.ko.md)

## Installing

Download the latest installer from the [Releases](../../releases/latest) page and run it. Glance updates itself afterward — no need to manually download future versions unless you want to switch channels (see [Troubleshooting](troubleshooting.md#update-channels)).

Windows will likely show a **"Windows protected your PC"** SmartScreen warning the first time you run the installer. This isn't a sign of anything malicious — Glance just isn't code-signed, since a signing certificate is a recurring cost a free, solo-developed project doesn't have budget for. Click **More info → Run anyway** to continue.

## Opening a repository

On first launch, Glance shows a **Recent Repositories** list (empty at first) with options to:

- **Open** an existing local repository
- **Clone** a repository from a URL (HTTPS or SSH)

You can have multiple repositories open at once and switch between them from the sidebar's repository switcher. Cloning runs in the background — you can start a clone and keep working in another repo while it finishes.

If you're cloning over SSH and haven't set up a key yet, see [SSH setup](workflows.md#ssh-remotes) in Core Workflows.

<!-- TODO: screenshot — Recent Repositories / clone entry point -->

## Touring the interface

The left sidebar has five tabs, top to bottom:

| Tab | Shows |
|---|---|
| **Branches** | Commit history graph, refs (branches/remotes/tags), stashes |
| **Changes** | Working directory staging area (staged / unstaged / conflicts) |
| **File Explorer** | Full repository file tree, independent of what's changed |
| **Timeline** | Chronological reflog — every place HEAD has been, with undo |
| **Settings** | Git config, engine, appearance, editor, updates, SSH keys, license |

Selecting a commit, branch, or file opens its details in the panel on the right — commit metadata and diffs, a file's contents, or a conflict resolution editor, depending on context.

![Sidebar tab rail](assets/screenshots/hero.png)

Next: [Core Workflows](workflows.md) walks through the day-to-day operations — viewing history, staging, branching, syncing with remotes, and more.
