# Glance

Ultra-hochleistungs-Git-GUI für Windows.

[![Download for Windows](https://img.shields.io/github/v/release/onmcore/glance-releases?label=Download%20for%20Windows&color=2f6feb)](https://github.com/onmcore/glance-releases/releases/latest)

[English](README.md) | [한글](README.ko.md) | [日本語](README.ja.md) | [Deutsch](README.de.md)

![Glance beim Durchsuchen des Linux-Kernel-Repositories — Commit-Graph, Commit-Details und Diff-Staging](docs/manual/assets/gifs/repo-open.gif)

Dieses Repository hostet die offiziellen Glance-Binärreleases und Release Notes.

## Über Glance

Glance ist eine Git-GUI, die von Grund auf mit einer Obsession entwickelt wurde: **Geschwindigkeit**. Sie bleibt reaktiv in Repositories mit Millionen von Commits und Hunderttausenden von Dateien und behält dabei einen winzigen Speicher-Footprint.

Glance ist **jetzt vollständig kostenlos für alle — persönliche und kommerzielle Nutzung gleichermaßen** — kein Trial-Timer, keine Funktionssperrung, keine Kontoerstellung erforderlich. (Eine bezahlte kommerzielle Lizenz ist für eine zukünftige Version geplant; sie wird nicht beeinflussen, was Sie bereits haben.)

Entwickelt als Solo-Projekt — mein Hauptjob ist C++-Spieleentwicklung, aber für dieses Projekt habe ich Rust, Tauri und Solid.js gelernt und mit viel AI-Pairing entwickelt.

### Highlights

- **Schnell, wo andere stottern** — sofortige Reaktion bei Enterprise-Scale-Monorepos; [in Aktion sehen](docs/manual/performance.de.md)
- **Leicht im Speicherverbrauch** — nicht die gigabyteintensive Sorte
- **Tauri-Runtime** — kleiner Installer, kein Electron-großer Footprint, mit nativen Besonderheiten wie Windows-Taskleisten-Fortschritt bei langwierigen Operationen
- **Vollständiger Git-Workflow** — Branch, Merge, Rebase, Stash, Cherry-Pick, Blame, Historien-Visualisierung
- **Integrierte Konfliktlösung** — ein visueller Drei-Wege-[Merge Editor](docs/manual/workflows.de.md#konflikte-lösen) für Merges, Rebases und Cherry-Picks
- **Interactive Rebase, kein Terminal nötig** — Commits direkt im Verlauf per Drag neu anordnen oder squashen, oder in einem dedizierten Editor pick/reword/fixup/drop; siehe [Interactive Rebase](docs/manual/workflows.de.md#interactive-rebase)
- **Native Worktrees als Tabs** — checken Sie einen anderen Branch in seinen eigenen Ordner aus, ohne den aktuellen zu beeinträchtigen, und wechseln Sie mit einem Tab-Strip statt durch ein Menü zu graben; siehe [Worktrees](docs/manual/workflows.de.md#worktrees)
- **Natives Git LFS mit Datei-Sperrung** — reiner Rust-Client, kein externer `git-lfs`-Binary erforderlich; Batch-Downloads und Inline-Vorschau, plus eingebaute Datei-Sperrung und eine [visuelle Speicheranalyse mit One-Click-Bereinigung](docs/manual/workflows.de.md#lfs-speicherbereinigung), die genau zeigt, wo Ihr Speicherplatz geblieben ist (die meisten Git GUIs überlassen beides dem CLI); siehe [Git LFS](docs/manual/workflows.de.md#dateien-erkunden)

### Für wen es gedacht ist

- Entwickler, die es satthaben, dass Git-GUIs bei großen Repos laggen
- Jeder, der lieber ein fokussiertes, native wirkendes Tool als einen Browser im Schafspelz nutzt
- Windows-Nutzer, die eine moderne Alternative zu den üblichen Verdächtigen suchen

## Download

Laden Sie das neueste Installationsprogramm von der [Releases](../../releases)-Seite herunter.

### Release-Kanäle

| Kanal | Was ist das | Wo erhältlich |
|---|---|---|
| **Stable** | Getestete Releases. Empfohlen für den täglichen Gebrauch. | [Latest release](../../releases/latest) |
| **Preview** | Kommende Funktionen, größtenteils stabil. | [Pre-releases](../../releases) (mit *Pre-release* gekennzeichnet) |

Auto-Update ist eingebaut — wählen Sie Ihren Kanal unter **Settings → Update**.

## Handbuch

Neu bei Glance? Das [Handbuch](docs/manual/README.de.md) behandelt die ersten Schritte, zentrale Workflows, Tastenkombinationen und Fehlerbehebung.

## Glance unterstützen

Glance ist jetzt für alle kostenlos, auch für kommerzielle Nutzung — ohne Lizenzschlüssel oder Zahlung erforderlich. Freiwillige Spenden sind willkommen, aber völlig optional. Eine bezahlte kommerzielle Lizenz ist für eine zukünftige Version geplant; sie wird bereits unter dieser Vereinbarung veröffentlichte Versionen nicht ändern.

## Fehlerberichte & Feedback

- Bug gefunden? [Issue öffnen](https://github.com/onmcore/glance-releases/issues/new)
- Funktionsidee? [Discussion starten](https://github.com/onmcore/glance-releases/discussions)

Glance wird nur von mir entwickelt — ich lese jeden Bericht persönlich, daher können Antworten ein oder zwei Tage dauern.

## Lizenz

Glance ist jetzt für alle kostenlos verwendbar, einschließlich kommerzieller Nutzung — kein Lizenzschlüssel oder Zahlung erforderlich. Freiwillige Spenden sind willkommen, aber optional. Eine bezahlte kommerzielle Lizenz ist für eine zukünftige Version geplant; sie wird Versionen, die bereits unter dieser Vereinbarung veröffentlicht wurden, nicht ändern.

Unmodifizierte Weiterverbreitung ist erlaubt; Reverse-Engineering, Modifikation und Umpaketierung sind nicht erlaubt (siehe [LICENSE](./LICENSE)). Keine Gewährleistung.

Lizenzen von Third-Party-Komponenten sind in [THIRD_PARTY_LICENSES.md](./THIRD_PARTY_LICENSES.md) aufgelistet.

---

**Glance** © 2026 onmcore
