# パフォーマンス

[English](performance.md) | [한글](performance.ko.md) | [日本語](performance.ja.md) | [Deutsch](performance.de.md)

Glance は大規模なリポジトリでも反応性を失わないという 1 つの目標を中心に構築されています。

## 実際の動き

- 数十万のコミットがあるリポジトリを開いても UI がブロックされません — コミットグラフは仮想化されているため、リストが大きくなってもスクロールはスムーズなままです。
- 多くのファイルに影響する操作（rebase、merge、pull）の後でも、完全な再スキャンは発生しません — Glance は変更があった部分だけを更新します。
- 既知のファイル セットのみに影響する checkout、pull、stash 操作は、ワーキング ツリー全体をスキャンする代わりにスキップします。
- ディスク上のファイル変更（Git、別のツール、または OS から）は、顕著な遅延なく UI に表示されます。

## 理由

- **Electron ではなく Tauri v2 + Rust。** バンドルされた Chromium ランタイムがなく、インストーラーが小さく、基本的なメモリ使用量が低くなっています。
- **主な Git エンジンとして gitoxide (`gix`) を使用。** ほとんどの操作は `git.exe` を毎回起動する代わりに、純粋な Rust 実装を通じて実行されます。gitoxide がまだ対応していない操作の場合、Glance は自動的に `libgit2` または Git CLI にフォールバックします。

<!-- TODO: once we have our own measured numbers (self-timed, large repo, no
     competitor comparison per current scope), add a results section here.
     See local promo-plan notes for the simple measurement checklist. -->

## 実際に動作を見る

<!-- TODO: embed GIF — opening a large repository -->
