# Grundlegende Arbeitsabläufe

[English](workflows.md) | [한글](workflows.ko.md) | [日本語](workflows.ja.md) | [Deutsch](workflows.de.md)

## Verlauf durchsuchen

Der Tab **Branches** zeigt den Commit-Graphen an — eine virtualisierte Liste, die auch bei Hunderttausenden Commits flüssig bleibt. Der Refs-Baum in der Seitenleiste listet Branches, Remotes, Tags und Stashes auf; wenn Sie einen auswählen, wird der Graph gefiltert oder springt zu dieser Position.

- `Ctrl+F` öffnet die Suche — Commits nach Nachricht, Autor oder Hash filtern
- Rechtsklick auf einen Commit für Aktionen: Checkout, Branch erstellen, Cherry-Pick, Reset, Vergleich, als Patch exportieren oder in neuem Fenster öffnen
- **All Branches** aktivieren, um den gesamten Verlauf als eine flache Liste anzuzeigen, anstatt nur der Ahnenreihe des aktuellen Branch
- Beim Hovern über einen Commit wird eine schnelle Vorschau angezeigt; Klicken öffnet die vollständigen Details (Tabs Info / Changes) im rechten Panel
- **In neuem Fenster öffnen** öffnet die Commit-Detailansicht in einem eigenen Fenster, sodass Sie im Hauptfenster weiterhin den Verlauf durchsuchen können, während Sie vergleichen

### Zurücksetzen

Rechtsklick auf einen Commit → **Reset to this commit**, um den aktuellen Branch dorthin zu verschieben:

- **Soft** — verschiebt nur den Branch-Zeiger; Ihr Arbeitsverzeichnis und die Staged-Änderungen bleiben unverändert
- **Mixed** — verschiebt den Zeiger und aktualisiert den Index, lässt aber die Dateien im Arbeitsverzeichnis unverändert
- **Hard** — verschiebt den Zeiger und schreibt Index und Arbeitsverzeichnis neu, um sie anzupassen (verwirft nicht committete Änderungen — nicht verfolgte Dateien bleiben unverändert)

Wenn ein Hard-Reset fehlschlägt, können Sie mit [Timeline](#timeline) normalerweise alles wiederherstellen.

![Commit-Graph mit Refs-Seitenleiste](assets/screenshots/hero.png)

## Staging & Committing

Der Tab **Changes** ist Ihr Staging-Bereich des Arbeitsverzeichnisses, aufgeteilt in **Staged**, **Unstaged** und (falls vorhanden) **Conflicts** Abschnitte. Wechseln Sie zwischen den Layouts Flat, Grouped und Tree, je nachdem, wie Sie eine große Änderungsmenge durchsuchen möchten.

- Aktivieren Sie ein Kontrollkästchen für eine Datei oder einen Ordner, um sie zu stage/unstage — Kontrollkästchen unterstützen `Ctrl`/`Shift` Mehrfachauswahl
- Öffnen Sie den Diff einer Datei, um einzelne Hunks oder Zeilen zu stage oder zu verwerfen, nicht nur ganze Dateien
- Verwerfen ist auf Datei- oder Hunk-Ebene verfügbar
- Schreiben Sie Ihre Commit-Nachricht im Panel unten und senden Sie sie mit `Ctrl+Enter` ab
- Der Diff-Header zeigt die Kodierung jeder Datei (UTF-8, EUC-KR usw.) und Zeilenenden (LF/CRLF) an; für nicht-gestaffelte Arbeitskopie-Dateien können Sie durch Klicken auf einen Chip die Konvertierung durchführen

Änderungen werden von einem File Watcher in Echtzeit erkannt — keine manuelle Aktualisierung erforderlich.

### Co-Autoren und Signierung

Das Zahnradsymbol (⚙) über der Commit-Nachricht ermöglicht:

- **Co-authors** — öffnet ein Modal, um Mitwirkende nach Name/E-Mail hinzuzufügen (mit Autovervollständigung von kürzlichen Mitwirkenden); Sie werden beim Commit als `Co-authored-by`-Trailer angehängt
- **Sign commit** — signiert mit Ihrem konfigurierten Git-Signaturschlüssel (SSH oder GPG). Unverschlüsselte/passwortlose SSH-Schlüssel werden prozessintern signiert; GPG- oder passwortgeschützte Schlüssel nutzen das `git`/`gpg-agent`-Setup Ihres Systems

### Amending

Aktivieren Sie **Amend** im Commit-Panel, um Ihre gestaffelten Änderungen in den vorherigen Commit zu falten, anstatt einen neuen zu erstellen. Die Nachricht und der Autor werden aus diesem Commit vorgefüllt, und der Abschnitt Staged zeigt, was der geänderte Commit enthält — Zeilen, die bereits in `HEAD` sind, sind schreibgeschützt, und das Unstagen einer Datei entfernt sie aus dem Amend.

![Changes-Panel mit Hunk-Level-Staging](assets/screenshots/staging.png)

## Branching & Merging

Erstellen, checken Sie aus, benennen Sie um und löschen Sie Branches aus der Seitenleiste oder dem Branch-Menü. Checkout zeigt den Fortschritt für große Repos und berührt nur die Pfade, die sich tatsächlich geändert haben.

- **Merge** einen Branch in den aktuellen (Fast-Forward oder echter Merge-Commit); wenn Konflikte auftreten, wird der Merge Editor geöffnet
- **Rebase onto** einen Branch oder Commit — der Fortschritt wird phasenweise angezeigt (Checkout, Commit-Replay usw.)
- **Cherry-pick** einen Commit aus seinem Kontextmenü auf den aktuellen Branch
- **Tags** können einzeln erstellt, gelöscht und gepusht werden; mit Anmerkungen versehene Tag-Nachrichten sind inline sichtbar

### Stashing

Lagern Sie unverdrahtete Änderungen vom Branch-Menü (**Stash Changes...**) ein, optional mit Beibehaltung von gestaffelten Änderungen im Arbeitsbaum. Stashes erscheinen im Abschnitt Stashes der Seitenleiste und im Commit-Graphen. Jeder Stash unterstützt:

- **Pop** — Anwendung und Entfernung
- **Apply** — Anwendung aber Stash beibehalten
- **Drop** — Löschen ohne Anwendung

### Konflikte lösen

Wenn bei einem Merge, Rebase oder Cherry-Pick ein Konflikt auftritt, öffnet Glance den **Merge Editor** — eine dreigliedrige Ansicht (Ours / Base / Theirs) mit `[` / `]` um zwischen Konflikten zu wechseln. Lösen Sie dann auf und setzen Sie fort oder brechen Sie den Vorgang aus derselben Ansicht ab.

Wenn Sie lieber ein externes Tool verwenden möchten (Beyond Compare, WinMerge, KDiff3 und ähnliche), konfigurieren Sie es in den Einstellungen — Glance bietet an, Diffs und Konflikte darin statt in der integrierten Ansicht zu öffnen.

![Merge Editor dreigliedrige Ansicht](assets/screenshots/merge-editor.png)

## Remote-Synchronisierung

Fügen Sie Remotes aus der Seitenleiste hinzu, bearbeiten oder entfernen Sie diese. Fetch wird bei Bedarf ausgeführt oder läuft automatisch im Hintergrund (standardmäßig alle 3 Minuten — anpassbar in den Einstellungen). Push unterstützt Force und Force-with-Lease. Pull kann Merge durchführen (Fast-Forward oder Three-Way, mit Konfliktauflösung) oder Rebase.

### SSH-Remotes

Für SSH-basiertes Clone/Fetch/Push richten Sie einen Schlüssel unter **Settings → SSH Keys** ein:

1. **Schlüssel generieren** — wählen Sie einen Algorithmus (Ed25519 empfohlen), geben Sie einen Namen ein und erstellen
2. Kopieren Sie den öffentlichen Schlüssel in Ihren Git-Host (GitHub/GitLab/etc.)
3. Unter **Host configuration** fügen Sie einen Host-Eintrag hinzu (HostName, User, Port, IdentityFile) — dies bearbeitet Ihre echte `~/.ssh/config`, daher werden vorhandene Einträge und Direktiven, die Glance nicht kennt, beibehalten
4. Wenn Sie sich zum ersten Mal mit einem neuen Host verbinden, fordert Glance Sie auf, seinen SSH-Hostschlüssel unter **Known hosts** zu vertrauen (TOFU) — dieselbe Idee wie die erste Verbindungsaufforderung von `ssh`

![SSH Keys Einstellungsbereich](assets/screenshots/ssh-keys.png)

## Erweitert

### Worktrees

Rechtsklick auf den Repository-Header → **New worktree**, um einen anderen Branch in seinen eigenen Ordner auszuchecken, ohne den aktuellen zu beeinträchtigen — hilfreich, um gleichzeitig an zwei Dingen zu arbeiten. Wählen Sie einen Starting-Branch, einen Zielpath und einen Namen. Wechseln Sie zwischen Worktrees über die Worktree-Auswahl in der Seitenleiste; löschen Sie eine mit dem × neben ihrem Namen (der Worktree, in dem Sie sich derzeit befinden, kann nicht gelöscht werden).

### Submodules

Submodule werden in der Seitenleiste angezeigt. Nicht initialisierte haben einen **Init**-Button; initialisierte öffnen sich als eigenes Repository, wenn darauf geklickt wird, und können von ihrem Kontextmenü aus aktualisiert werden.

### Patches

Um Änderungen ohne gemeinsames Remote freizugeben, rechtsklicken Sie auf einen Commit (oder ziehen Sie einen Bereich aus) → **Export as patch**. Wenden Sie einen später über das Menü **Apply patch** des Repository-Menüs an. Beachten Sie, dass dies näher an `git apply` als an `git am` liegt — es aktualisiert Ihren Arbeitsbaum, daher müssen Sie das Ergebnis selbst stagieren und committen.

### Diff-Algorithmus

Wenn ein bestimmter Diff nicht wie erwartet dargestellt wird, können Sie mit **Settings → Editor** den Diff-Algorithmus zwischen Histogram (Standard), Myers und Minimal wechseln.

## Refs vergleichen

Rechtsklicken Sie auf einen Commit, Branch oder Tag für **Compare** — zeigen Sie das Datei-Level-Diff zwischen zwei beliebigen Refs an, unabhängig von Ihrem aktuellen Checkout. Wechseln Sie zwischen zwei-Punkt (`a..b`) und drei-Punkt (`a...b`, Merge-Base) Vergleich, und tauschen Sie die Seiten aus.

## Dateien erkunden

Der Tab **File Explorer** durchsucht den vollständigen Repository-Baum (nicht nur geänderte Dateien) in den Layouts Flat, Grouped oder Tree. Das Öffnen einer Datei zeigt ihren Inhalt mit Syntaxhervorhebung an; Markdown-Dateien können zwischen Raw und gerenderte Vorschau umschalten, und CSV/TSV-Dateien zwischen Raw-Text und einer sortierbaren Tabelle mit anklickbarem Header.

Aus dem Kontextmenü einer Datei können Sie auch deren **Verlauf** anzeigen (jeden Commit, der sie berührt hat) oder dessen **Blame** (Zeile-für-Zeile Autoren-/Commit-Anmerkungen).

Dateien, die mit Git LFS verfolgt werden, zeigen ein Badge im Baum und werden bei Bedarf heruntergeladen — über die `filter=lfs`-Einstellung in `.gitattributes` ist keine separate Einrichtung erforderlich.

## Timeline

Der Tab **Timeline** ist ein chronologischer Feed Ihres Repository-Reflog — jeder Platz, auf den HEAD gezeigt hat, über Checkouts, Commits, Merges, Rebases, Resets und Pulls. Es ist ein Sicherheitsnetz unabhängig von Ihrem sichtbaren Branch-Verlauf. Von jedem Eintrag können Sie:

- direkt zu diesem Punkt **Checkout**
- von ihm einen **neuen Branch** erstellen
- seinen Commit auf Ihren aktuellen Branch **Cherry-Pick**
- den aktuellen Branch zu ihm **Zurücksetzen**
- die letzte Wiederherstellungsaktion **Rückgängig machen**, falls Sie gerade die Timeline zur Behebung eines Fehlers verwendet haben

![Timeline Reflog Feed](assets/screenshots/timeline.png)

---

Nächstes: [Tastenkombinationen](shortcuts.de.md)
