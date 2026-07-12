# Troubleshooting

[English](troubleshooting.md) | [한글](troubleshooting.ko.md) | [日本語](troubleshooting.ja.md) | [Deutsch](troubleshooting.de.md)

## Update channels

Glance auto-updates in the background. Pick a channel under **Settings → Updates**:

| Channel | What it is |
|---|---|
| **Stable** | Tested releases. Recommended for daily use. |
| **Preview** | Upcoming features, mostly stable, released more often. |

You can also enable checking the Preview channel from a Stable install without fully switching. Switching channels takes effect on the next update check.

## Built-in recovery

A few things run automatically so a bad moment doesn't turn into a lost repository:

- **Index/HEAD corruption detection and repair** — if `.git`'s index or HEAD ends up in a bad state (e.g. after a crash mid-write), Glance detects and repairs it rather than failing silently
- **Watcher resilience** — the background file watcher that powers real-time change detection is isolated from crashes and restarts itself if it dies, so the UI doesn't quietly stop updating
- **[Timeline](workflows.md#timeline)** — if you made a mistake (bad reset, wrong branch delete, etc.), Timeline's reflog view can usually get you back to where you were, even outside what Glance itself tracked
- **Detached HEAD warning** — checking out a tag or a specific commit (or a rebase that pauses mid-way) leaves HEAD pointing at a commit instead of a branch. Glance shows an amber badge when this happens; click it to create a branch at your current position and get back onto normal footing. Push/pull are disabled while detached, since there's no branch to track

## Something's still wrong

- [Open an issue](https://github.com/onmcore/glance-releases/issues/new) with what you were doing, what you expected, and what happened instead
- [Start a discussion](https://github.com/onmcore/glance-releases/discussions) for anything less bug-shaped — feature ideas, questions, feedback

All reports are read directly by the developer; response time varies.
