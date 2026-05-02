> **Note**: The internal `test` channel (daily timestamped builds) is **not** released through this repo and is not part of the commit convention.

### Examples

```
Release: v0.83.0
Preview: v0.84.0-preview.1
Hotfix: v0.83.1
Docs: Update license to personal-free / commercial-paid
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
- `LICENSE` — End user license (personal free / commercial paid; unmodified redistribution allowed; no reverse engineering / modification / repackaging). **Public canonical** — keep `G-Lance-2/LICENSE.md` byte-identical.
- `THIRD_PARTY_LICENSES.md` — Bundled OSS attribution
- `.gitattributes`, `.gitignore` — Repo configuration

### Update rules

1. **Public audience** — Write so a first-time visitor understands what Glance is and how to get it.
2. **Bilingual parity** — Update `README.md` (English) and `README.ko.md` (Korean) in the same commit. Content must match.
3. **Dual-license messaging** — Free for personal & non-commercial use; commercial use is paid (`glance@onmcore.com`). State both clearly; never imply the whole app is free or that commercial use is free. Sponsorship is voluntary and unlocks *nothing*.
4. **Commercial-license language is required, not forbidden** — User-facing docs must say commercial use needs a paid license. (Earlier policy retired "commercial tier" wording under a free-only model; that model is itself now retired — do NOT strip commercial-license language.) Still avoid "enterprise tier" / "beta program" framing unless such offerings actually exist.
5. **Channel naming** — Public channels are **Stable** and **Preview**. The internal `test` channel exists in the build system but is not documented in public-facing files.
6. **License clarity** — LICENSE is a custom EULA (not MIT). Free for personal/non-commercial use; commercial use requires a paid license. Permits unmodified redistribution; prohibits reverse engineering, modification, repackaging, and for-fee redistribution. `LICENSE` here is the public canonical; `G-Lance-2/LICENSE.md` must stay byte-identical.

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
4. **Dual-license model is load-bearing** — Keep "personal free / commercial paid" consistent across `LICENSE`, both READMEs, and the in-app EULA (`G-Lance-2/LICENSE.md`, byte-identical). Flag any wording that implies commercial use is free, or that the app is free with no conditions.
5. **Simplicity** — Short is better than thorough. Cut anything that doesn't help a visitor decide whether to download.
