# glance-releases AI Agent Guide

This document provides core guidelines for AI agents supporting the glance-releases repository.

---

## 📜 Repository Overview

**glance-releases** manages official releases and deployment logs for Glance.

- **Purpose**: Store built binaries, deployment logs, and release notes
- **Characteristic**: Completely separate from G-Lance source code repository (release-only repository)

---

## 🛠️ Commit Message Convention

### Format

Use **Release-focused format** (simple and clear)

- `Release: <version>` — Official release
- `Hotfix: <version>` — Hotfix release
- `Docs: <description>` — Documentation updates (README, settings, etc.)
- `Deploy: <description>` — Deployment tasks, log updates

### Examples

```
Release: v0.83.0-beta.1
```

```
Hotfix: v0.83.0-beta.2
```

```
Docs: Add commit and documentation conventions
```

```
Deploy: Update Windows binaries and signatures
```

### Rules

- **No Co-Authored-By line** — Not needed for a release repository
- Add detailed explanation in message body if needed (optional)
- Keep it simple and clear

---

## 📄 Documentation Rules

### Documentation Scope

The following files are considered documentation:
- `README.md`, `README.ko.md` — Project description
- `LICENSE` — License information
- `.gitattributes`, `.gitignore` — Repository configuration files

### Documentation Update Rules

1. **Clarity First** — This is a public repository, write for everyone
2. **Multi-language Support** — Update both English (README.md) and Korean (README.ko.md) simultaneously
3. **Keep in Sync** — English and Korean documentation must have identical content
4. **License Clarity** — Since this is a release repository, license information must always be clear

### Language Style

- **README**: Clear and professional tone
  - English: Standard English
  - Korean: Formal speech (존댓말), technical terms in English
- **LICENSE**: Legal terminology, precise expressions
- **Configuration Files**: Comments only when necessary

---

## 📋 Common Commands

```bash
# Commit (follow conventions)
git commit -m "Release: v0.83.0-beta.1"

# Documentation update
git commit -m "Docs: Update README with new features"

# Push
git push origin main
```

---

## 🚀 Deployment Workflow

1. **Prepare New Release** — Determine version number
2. **Build Binaries** — Generated from G-Lance repository
3. **Release Folder Structure** — Organize under releases/<version>/
4. **Update Documentation** — Update README and release notes if needed
5. **Commit and Push** — Commit with "Release: vX.Y.Z" format
6. **Create GitHub Release** — Add release notes on GitHub if needed

---

## 📌 Working Principles

1. **Documentation for Public Repository** — Write so anyone can understand
2. **Commit Only on Explicit Instruction** — No auto-commits
3. **Multi-language Sync** — Update Korean and English documents together
4. **Simplicity** — Avoid unnecessary explanations or comments
