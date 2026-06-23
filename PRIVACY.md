# Privacy Policy

_Last updated: 2026-06-23_

[English](PRIVACY.md) | [한글](PRIVACY.ko.md)

Glance is a Windows desktop application, designed to collect as little as possible.

## What Glance sends

- **Update checks.** To offer updates, Glance asks `glance-api.onmcore.com` whether a
  newer version exists, sending only the **current version, operating system, and CPU
  architecture**. This is required to serve the correct update and is not used to
  identify you.

That is the only network request Glance makes on its own.

## What stays on your device

- Settings, window state, and the list of repositories you open are stored **locally
  only** and are never transmitted.
- Glance does **not** require an account, and collects **no** personal information,
  usage analytics, or telemetry.

## Your repositories

Glance reads and writes your local Git repositories on your machine. Their contents are
never sent anywhere by Glance. Network access to Git remotes (fetch / push / clone) goes
**directly to the remotes you configure**, exactly as Git itself would — Glance adds no
intermediary.

## Changes

If this policy changes, the updated version will be published in this repository.

## Contact

Questions: glance@onmcore.com
