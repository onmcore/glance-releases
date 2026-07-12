# Erste Schritte

[English](getting-started.md) | [한글](getting-started.ko.md) | [日本語](getting-started.ja.md) | [Deutsch](getting-started.de.md)

## Installation

Laden Sie das neueste Installationsprogramm von der Seite [Releases](../../releases/latest) herunter und führen Sie es aus. Glance aktualisiert sich danach selbst — Sie müssen zukünftige Versionen nicht manuell herunterladen, es sei denn, Sie möchten Kanäle wechseln (siehe [Problembehandlung](troubleshooting.de.md#update-kanäle)).

Beim ersten Ausführen des Installationsprogramms wird wahrscheinlich eine SmartScreen-Warnung **„Windows hat Ihren PC geschützt"** angezeigt. Dies ist kein Zeichen für etwas Böswilliges — Glance ist einfach nicht codesigniert, da ein Signaturzertifikat Kosten verursacht, die sich ein kostenlos und allein entwickeltes Projekt nicht leisten kann. Klicken Sie auf **Weitere Informationen → Trotzdem ausführen**, um fortzufahren.

## Repository öffnen

Beim ersten Start zeigt Glance eine Liste **Recent Repositories** (anfangs leer) mit Optionen an:

- Ein vorhandenes lokales Repository **Open**
- Ein Repository von einer URL klonen (**Clone** – HTTPS oder SSH)

Sie können mehrere Repositories gleichzeitig offen haben und über den Repository-Switcher in der Seitenleiste zwischen ihnen wechseln. Das Klonen läuft im Hintergrund — Sie können einen Klon starten und in einem anderen Repository weiterarbeiten, während er abgeschlossen wird.

Wenn Sie über SSH klonen und einen Schlüssel noch nicht eingerichtet haben, lesen Sie [SSH-Setup](workflows.de.md#ssh-remotes) in Core Workflows.

<!-- TODO: screenshot — Recent Repositories / clone entry point -->

## Die Oberfläche erkunden

Die linke Seitenleiste hat fünf Registerkarten (von oben nach unten):

| Registerkarte | Anzeige |
|---|---|
| **Branches** | Commit-Verlaufsgraph, Refs (Branches/Remotes/Tags), Stashes |
| **Changes** | Arbeitsverzeichnis-Staging-Bereich (staged / unstaged / conflicts) |
| **File Explorer** | Vollständiger Repository-Dateibaum, unabhängig von Änderungen |
| **Timeline** | Chronologisches Reflog — jeder Ort, an dem HEAD war, mit Rückgängigmachen |
| **Settings** | Git-Konfiguration, Engine, Erscheinungsbild, Editor, Updates, SSH-Schlüssel, Lizenz |

Wenn Sie einen Commit, Branch oder eine Datei auswählen, werden Details im rechten Panel angezeigt — Commit-Metadaten und Diffs, Dateiinhalt oder ein Konfliktlösungs-Editor, je nach Kontext.

![Seitenleisten-Tab-Schiene](assets/screenshots/hero.png)

Nächstes: [Core Workflows](workflows.de.md) führt Sie durch die täglichen Arbeitsabläufe — Verlauf anzeigen, Staging, Branching, Synchronisierung mit Remotes und mehr.
