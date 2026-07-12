# Leistung

[English](performance.md) | [한글](performance.ko.md) | [日本語](performance.ja.md) | [Deutsch](performance.de.md)

Glance wurde mit einem einzigen Ziel entwickelt: In großen Repositorys reaktionsschnell zu bleiben.

## So funktioniert es

- Das Öffnen eines Repositorys mit Hunderttausenden von Commits blockiert die UI nicht — der Commit-Graph ist virtualisiert, sodass das Scrollen reibungslos bleibt, anstatt ruckelnd zu werden, wenn die Liste wächst.
- Operationen, die viele Dateien betreffen (rebase, merge, pull), führen danach nicht zu einem vollständigen Rescan — Glance aktualisiert nur, was sich geändert hat.
- Checkout-, Pull- und Stash-Operationen, die nur bekannte Dateien betreffen, durchsuchen den Rest des Arbeitsverzeichnisses nicht, sondern überspringen ihn.
- Dateiänderungen auf der Festplatte (von Git, anderen Tools oder dem Betriebssystem) werden in der UI ohne spürbare Verzögerung angezeigt.

## Warum

- **Tauri v2 + Rust, nicht Electron.** Keine gebündelte Chromium-Laufzeit — kleineres Installationsprogramm, niedrigerer Grundspeicherbedarf.
- **gitoxide (`gix`) als primäres Git-Engine.** Die meisten Operationen laufen durch eine reine Rust-Implementierung, anstatt immer `git.exe` zu starten. Wenn gitoxide eine Operation noch nicht unterstützt, wechselt Glance automatisch auf `libgit2` oder die Git-CLI.

<!-- TODO: once we have our own measured numbers (self-timed, large repo, no
     competitor comparison per current scope), add a results section here.
     See local promo-plan notes for the simple measurement checklist. -->

## Sehen Sie es in Aktion

![Glance beim Durchsuchen des Linux-Kernel-Repositories — Commit-Graph, Commit-Details und Diff-Staging](assets/gifs/repo-open.gif)
