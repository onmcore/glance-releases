# glance-releases AI Agent Guide

This document provides core guidelines for AI agents working in the glance-releases repository.

---

## 📜 Repository Overview

**glance-releases** is the public-facing distribution and documentation repository for Glance.

- **Purpose**: Host release binaries (via GitHub Releases), publish user-facing README/LICENSE, and serve as the contact point for bug reports and feature requests.
- **Distribution model**: Glance is **currently free for everyone, including commercial use** (voluntary [GitHub Sponsors](https://github.com/sponsors/yonmy) welcome). No trial mechanism, no account. A **paid commercial license is planned for future versions** but is **not active now** — do not present commercial use as paid in user-facing docs.
- **License source of truth**: `LICENSE` in THIS repo is the **public canonical**. The in-app copy (`G-Lance-2/LICENSE.md`, bundled into the app's EULA viewer) must stay **byte-identical** to it — edit both together. ⚠️ The EULA text is **unreviewed boilerplate pending legal review** (esp. the "Commercial Use" definition and the warranty/liability clauses) — refine with counsel before relying on it; do NOT put a "draft/pending review" marker inside `LICENSE` itself (it ships to users verbatim).
- **Source**: This repo contains **no application source code**. Source lives in the private `G-Lance` repo. Binaries are built there and uploaded here as GitHub Release assets.

---

## 🛠️ Commit Message Convention

### Format

Use a **release-focused prefix** (simple, scannable):

- `Release: <version>` — Stable release (e.g. `v0.83.0`)
- `Preview: <version>` — Preview channel release (e.g. `v0.84.0-preview.1`)
- `Hotfix: <version>` — Stable hotfix release
- `Docs: <description>` — README, LICENSE, or other doc updates
- `Deploy: <description>` — Repo config, automation, or asset housekeeping

> **Note**: The internal `test` channel (daily timestamped builds) is **not** released through this repo and is not part of the commit convention.

### Examples

```
Release: v0.83.0
Preview: v0.84.0-preview.1
Hotfix: v0.83.1
Docs: Update license to currently-free
Deploy: Update .gitattributes for binary files
```

### Rules

- **No `Co-Authored-By` line.**
- Body is optional; add one when the *why* isn't obvious from the subject.
- Keep subjects under ~70 characters.

---

## 📄 Documentation Rules

### Files considered documentation

- `README.md`, `README.ko.md` — Project overview (must stay in sync)
- `LICENSE` — End user license (**currently free for all use**; unmodified redistribution allowed; no reverse engineering / modification / repackaging; future versions may use different terms). **Public canonical** — keep `G-Lance-2/LICENSE.md` byte-identical.
- `THIRD_PARTY_LICENSES.md` — Bundled OSS attribution
- `.gitattributes`, `.gitignore` — Repo configuration

### Update rules

1. **Public audience** — Write so a first-time visitor understands what Glance is and how to get it.
2. **Bilingual parity** — Update `README.md` (English) and `README.ko.md` (Korean) in the same commit. Content must match.
3. **Currently-free messaging** — Glance is currently free for everyone, including commercial use. Do **not** present commercial use as paid; a paid commercial license is only *planned* for future versions. Sponsorship is voluntary and unlocks *nothing*.
4. **Currently free — don't add paid-now language** — The current model is free for all use (commercial included); paid commercial licensing is *future-planned*, not active. Do not reintroduce "commercial use requires a paid license (now)" wording. Avoid "enterprise tier" / "beta program" framing unless such offerings actually exist.
5. **Channel naming** — Public channels are **Stable** and **Preview**. The internal `test` channel exists in the build system but is not documented in public-facing files.
6. **License clarity** — LICENSE is a custom EULA (not MIT). **Currently free for all use** (commercial included); future versions may adopt paid commercial terms. Permits unmodified redistribution; prohibits reverse engineering, modification, repackaging, and for-fee redistribution. `LICENSE` here is the public canonical; `G-Lance-2/LICENSE.md` must stay byte-identical.

### Language style

- **README** — Friendly, project-by-an-indie-dev tone. Direct, low ceremony, no marketing puffery.
  - English: conversational but precise.
  - Korean: 존댓말, 기술 용어는 영어 그대로.
- **LICENSE** — Plain legal English. Short sentences. No jargon for jargon's sake.
- **Config files** — Comments only when behavior would surprise a reader.

---

## 🚀 Release Workflow

Binaries are produced by `G-Lance` build scripts (`scripts/prepare-release.cjs`, `scripts/prepare-preview.cjs`) and uploaded automatically via `gh release create` / `gh release upload`. Cloudflare Worker KV is updated in the same step so the in-app updater picks up the new version.

A typical release commit in **this** repo only touches docs or release notes — the binaries themselves live on GitHub Releases, not in the git tree.

1. **Cut the build** in `G-Lance` (`pnpm build:release` or `pnpm build:preview`).
2. **Verify** the GitHub Release page shows the expected assets (`.exe`, `.nsis.zip`, `.sig`).
3. **Update docs here** if user-visible behavior changed (rare for patch releases).
4. **Commit + push** with the appropriate prefix.

---

## 📌 Working Principles

1. **Public-facing repo** — Everything here is read by users. Default to clarity.
2. **No automatic commits** — Commit only when the user explicitly says so. Same rule for `amend` and `push`.
3. **Bilingual sync** — English and Korean READMEs change together, in one commit.
4. **Currently-free model** — Keep "currently free for everyone" consistent across `LICENSE`, both READMEs, and the in-app EULA (`G-Lance-2/LICENSE.md`, byte-identical). A paid commercial license is planned for future versions — don't present it as active now.
5. **Simplicity** — Short is better than thorough. Cut anything that doesn't help a visitor decide whether to download.
