# Glance マニュアル

[English](README.md) | [한글](README.ko.md) | [日本語](README.ja.md) | [Deutsch](README.de.md)

![Glance の概要：サイドバー、コミットグラフ、詳細パネル](assets/screenshots/hero.png)

Glance の使い方を簡潔で実践的にまとめたガイドです。Git GUI を使ったことがあれば、数分で慣れるでしょう — このマニュアルでは主に、機能がどこにあるか、そして何が違うかを説明します。

## 目次

1. [はじめに](getting-started.ja.md) — インストール、リポジトリを開く・クローンする、インターフェースの概要
2. [パフォーマンス](performance.ja.md) — Glance が大規模なリポジトリでも高速である理由とベンチマーク
3. [コアワークフロー](workflows.ja.md) — 履歴、ステージング、ブランチ、リモート、SSH、diff、Timeline
4. [キーボードショートカット](shortcuts.ja.md)
5. [トラブルシューティング](troubleshooting.ja.md) — アップデートチャンネル、組み込み復旧機能、バグ報告

## インターフェースの概要

左側のサイドバーには 5 つのタブがあります：**Branches**（コミット履歴とグラフ）、**Changes**（ステージング領域）、**File Explorer**（リポジトリファイルツリー）、**Timeline**（reflog ベースの履歴と取り消し）、そして下部の **Settings** です。コミット、ブランチ、またはファイルを選択すると、右側のパネルに詳細が表示されます。

ここに載っていない内容については、メインの [README](../../README.ja.md) を参照するか、不足・誤りがあれば [issue を開いて](https://github.com/onmcore/glance-releases/issues/new) 知らせてください。
