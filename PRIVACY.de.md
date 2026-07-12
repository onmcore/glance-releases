# Datenschutzrichtlinie

_Zuletzt aktualisiert: 2026-07-12_

[English](PRIVACY.md) | [한글](PRIVACY.ko.md) | [日本語](PRIVACY.ja.md) | [Deutsch](PRIVACY.de.md)

Glance ist eine Windows-Desktop-Anwendung, die darauf ausgelegt ist, möglichst wenige Daten zu erfassen.

## Was Glance automatisch sendet

- **Updateprüfungen.** Um Updates anbieten zu können, fragt Glance bei `glance-api.onmcore.com` ab, ob eine neuere Version vorhanden ist, und sendet dabei nur die **aktuelle Version, das Betriebssystem und die CPU-Architektur**. Dies ist erforderlich, um das korrekte Update bereitzustellen, und wird nicht verwendet, um Sie zu identifizieren.
- **Git-Versionsprüfung.** Beim Öffnen der Einstellungen fragt Glance die öffentliche API von GitHub ab, um die neueste Git-Version zu erhalten, damit Sie darüber informiert werden können, wenn Ihre Version veraltet ist. Es werden keine persönlichen Daten gesendet.

Dies ist das Ausmaß dessen, was Glance **ohne Ihr Zutun** sendet.

## Was Sie optional senden können

- **Absturzberichte (nur Stable- und Preview-Kanäle).** Glance sendet Absturzberichte nicht automatisch — es gibt keine Hintergrundtelemetrie und keine Einstellung, um diese zu aktivieren. Falls Glance abstürzt oder das Anwendungsfenster auf einen unerwarteten Fehler stößt, wird immer ein Popup angezeigt, das Sie fragt, ob Sie einen Diagnosebericht an unseren Fehlererfassungsanbieter [Sentry](https://sentry.io) (in den USA gehostet) senden möchten, **bevor** etwas gesendet wird. Ein Bericht kann enthalten: die Fehlermeldung und Stack-Trace, Ihr Betriebssystem und Ihre App-Version, eine pseudonyme Gerätekennung, und — da Glance ein Entwicklerwerkzeug ist — **die Dateipfade und Git-Branchennamen, die zu diesem Zeitpunkt offen waren**. Ihr Windows-Benutzername wird vor dem Senden entfernt; andere Pfade und Namen werden nicht entfernt. Das Ablehnen sendet nichts; beim nächsten Absturz wird erneut danach gefragt.
- **Fehlerberichte.** Wenn Sie die Funktion „Fehler melden" in der App verwenden (Hilfemenü oder die Schaltfläche „Melden" bei einigen Fehlermeldungen), sendet Glance das, was Sie eingegeben haben, plus — nur wenn Sie die Kontrollkästchen aktiviert lassen — einen aktuellen Auszug aus den Protokollen und einen Screenshot des Anwendungsfensters. Sie sehen immer eine Vorschau von genau dem, was gesendet wird, **bevor** Sie absenden. Dies wird über einen Cloudflare Worker an ein **privates** GitHub-Repository gesendet, das nur der Entwickler einsehen kann; es wird nicht automatisch veröffentlicht.

## Was auf Ihrem Gerät verbleibt

- Einstellungen, Fenster-Status und die Liste der von Ihnen geöffneten Repositories werden **nur lokal** gespeichert und nie übertragen.
- Glance benötigt **kein Konto** und erfasst keine allgemeine Nutzungsanalytik.

## Ihre Repositories

Glance liest und schreibt in Ihre lokalen Git-Repositories auf Ihrem Computer. Deren Inhalte werden nie von Glance an andere Orte gesendet (Absturzberichte können wie oben erwähnt Dateipfade und *Branchennamen* enthalten, aber nicht den Inhalt der Dateien). Der Netzwerkzugriff auf Git-Remote-Repositories (fetch / push / clone) erfolgt **direkt zu den von Ihnen konfigurierten Remotes**, genau wie Git selbst — Glance schaltet sich nicht dazwischen.

## Dritte

- **Sentry, Inc.** (Vereinigte Staaten) — verarbeitet Absturzberichte wie oben beschrieben.
- **Cloudflare** — leitet die Übermittlung von Fehlerberichten und Updateprüfungen weiter.
- **GitHub** — hostet das private Repository, an das Fehlerberichte gesendet werden, und stellt die öffentliche API bereit, die für die neueste Git-Versionsprüfung abgefragt wird.

## Änderungen

Falls diese Richtlinie geändert wird, wird die aktualisierte Version in diesem Repository veröffentlicht.

## Kontakt

Fragen: glance@onmcore.com
