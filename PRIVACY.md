# Privacy Policy

_Last updated: 2026-07-12_

[English](PRIVACY.md) | [한글](PRIVACY.ko.md) | [日本語](PRIVACY.ja.md) | [Deutsch](PRIVACY.de.md)

Glance is a Windows desktop application, designed to collect as little as possible.

## What Glance sends automatically

- **Update checks.** To offer updates, Glance asks `glance-api.onmcore.com` whether a
  newer version exists, sending only the **current version, operating system, and CPU
  architecture**. This is required to serve the correct update and is not used to
  identify you.
- **Git version check.** Opening Settings asks GitHub's public API for the latest Git
  version, so Glance can tell you if yours is outdated. No personal data is sent.

That is the extent of what Glance sends **without you taking an action**.

## What you can choose to send

- **Crash reports (Stable and Preview channels only).** Glance never sends a crash
  report automatically — there is no background telemetry and no setting that turns
  one on. If Glance crashes, or if the app window hits an unexpected error, it always
  shows a popup asking whether to send a diagnostic report to our error-tracking
  provider, [Sentry](https://sentry.io) (hosted in the United States), **before**
  anything is sent. A report can include: the error message and stack trace, your OS
  and app version, a pseudonymous device identifier, and — because Glance is a
  developer tool — **file paths and Git branch names that were open at the time**.
  Your Windows username is removed before sending; other paths and names are not.
  Declining sends nothing; the next crash asks again independently.
- **Bug reports.** If you use the in-app "Report a Bug" feature (Help menu, or the
  "Report" button on some error messages), Glance sends what you typed, plus — only if
  you leave the checkboxes on — a recent log excerpt and a screenshot of the app
  window. You always see a preview of exactly what will be sent **before** you submit.
  This goes through our Cloudflare Worker to a **private** GitHub repository that only
  the developer can read; it is not published automatically.

## What stays on your device

- Settings, window state, and the list of repositories you open are stored **locally
  only** and are never transmitted.
- Glance does **not** require an account and does not collect general usage analytics.

## Your repositories

Glance reads and writes your local Git repositories on your machine. Their contents
are never sent anywhere by Glance (crash reports may include file *paths* and branch
*names*, as noted above, but not file contents). Network access to Git remotes
(fetch / push / clone) goes **directly to the remotes you configure**, exactly as Git
itself would — Glance adds no intermediary.

## Third parties

- **Sentry, Inc.** (United States) — processes crash reports as described above.
- **Cloudflare** — proxies bug-report submissions and update checks.
- **GitHub** — hosts the private repository bug reports are filed to, and its public
  API is queried for the latest Git version.

## Changes

If this policy changes, the updated version will be published in this repository.

## Contact

Questions: glance@onmcore.com
