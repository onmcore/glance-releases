# Fehlerbehebung

[English](troubleshooting.md) | [한글](troubleshooting.ko.md) | [日本語](troubleshooting.ja.md) | [Deutsch](troubleshooting.de.md)

## Update-Kanäle

Glance aktualisiert sich automatisch im Hintergrund. Wählen Sie einen Kanal unter **Settings → Updates**:

| Kanal | Beschreibung |
|---|---|
| **Stable** | Getestete Veröffentlichungen. Empfohlen für die tägliche Nutzung. |
| **Preview** | Kommende Funktionen, größtenteils stabil, häufiger veröffentlicht. |

Sie können auch die Überprüfung des Preview-Kanals aus einer Stable-Installation aktivieren, ohne vollständig zu wechseln. Der Kanalwechsel wird beim nächsten Update-Check wirksam.

## Integrierte Wiederherstellung

Einige Dinge werden automatisch ausgeführt, damit ein schlechter Moment nicht zu einem verlorenen Repository führt:

- **Index/HEAD-Beschädigungserkennung und -reparatur** — Wenn der Index oder HEAD von `.git` in einen fehlerhaften Zustand gerät (z. B. nach einem Absturz während des Schreibens), erkennt Glance dies und repariert es, anstatt stillschweigend fehlzuschlagen
- **Watcher-Ausfallsicherheit** — Der Hintergrund-Datei-Watcher, der die Echtzeiterkennung von Änderungen ermöglicht, ist vor Abstürzen isoliert und startet sich selbst neu, wenn er ausfällt, sodass die Benutzeroberfläche nicht einfach ihre Aktualisierung einstellt
- **[Timeline](workflows.de.md#timeline)** — Wenn Sie einen Fehler gemacht haben (falscher Reset, falsches Löschen von Branches usw.), kann die Reflog-Ansicht von Timeline Sie normalerweise auf den Stand zurückbringen, an dem Sie waren, sogar außerhalb dessen, was Glance selbst verfolgt hat
- **Detached HEAD-Warnung** — Das Auschecken eines Tags oder eines bestimmten Commits (oder ein Rebase, das in der Mitte pausiert) lässt HEAD auf einen Commit statt auf einen Branch zeigen. Glance zeigt in diesem Fall ein bernsteinfarbenes Abzeichen an; klicken Sie es, um einen Branch an Ihrer aktuellen Position zu erstellen und wieder auf normalen Fuß zu kommen. Push/Pull sind im Detached-Status deaktiviert, da es keinen Branch zum Verfolgen gibt

## Etwas ist immer noch falsch

- [Öffnen Sie ein Problem](https://github.com/onmcore/glance-releases/issues/new) mit dem, was Sie taten, was Sie erwartet haben, und was stattdessen geschah
- [Beginnen Sie eine Diskussion](https://github.com/onmcore/glance-releases/discussions) für alles, das weniger fehlerförmig ist — Funktionsideen, Fragen, Feedback

Alle Berichte werden direkt vom Entwickler gelesen; die Reaktionszeit ist unterschiedlich.
