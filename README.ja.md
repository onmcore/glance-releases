# Glance

Windows用 超高性能 Git GUI。

[![Download for Windows](https://img.shields.io/github/v/release/onmcore/glance-releases?label=Download%20for%20Windows&color=2f6feb)](https://github.com/onmcore/glance-releases/releases/latest)

[English](README.md) | [한글](README.ko.md) | [日本語](README.ja.md) | [Deutsch](README.de.md)

![Glance で Linux カーネルリポジトリを閲覧する様子 — コミットグラフ、コミット詳細、diff ステージング](docs/manual/assets/gifs/repo-open.gif)

このリポジトリは Glance の公式バイナリリリースとリリースノートをホストしています。

## Glance について

Glance は一つの執着を持って一から作られた Git GUI です：**速度**。数百万のコミット、数十万のファイルを含むリポジトリでも素早く反応し、メモリ使用量も少なく保ちます。

Glance は**今すぐ個人・商用問わず完全に無料**で使えます — 試用期限なし、機能ロックなし、アカウント登録不要。（将来のバージョンで有料の商用ライセンスを導入予定ですが、すでに入手したバージョンには影響しません。）

一人で開発しています — 本業は C++ ゲーム開発ですが、このプロジェクトでは Rust、Tauri、Solid.js を学びながら、AI ペアリングを活用して開発しています。

### ハイライト

- **他のツールが遅くなる場面で高速** — エンタープライズ規模のモノレポで即座に応答 — [実際に見てみる](docs/manual/performance.ja.md)
- **軽いメモリフットプリント** — ギガバイト級の使用量ではありません
- **Tauri ランタイム** — 小さいインストーラ、Electron 並みのフットプリントではなく、Windows タスクバーの進行状況表示など、ネイティブなディテールまで
- **完全な Git ワークフロー** — branch、merge、rebase、stash、cherry-pick、blame、履歴可視化
- **組み込みの競合解決** — merge・rebase・cherry-pick 中の競合に対応する、ビジュアルな 3-way [マージエディタ](docs/manual/workflows.ja.md#競合を解決)
- **Interactive Rebase、ターミナル不要** — 履歴ログでドラッグして並べ替え・squash、または専用エディタで pick/reword/fixup/drop; [Interactive Rebase](docs/manual/workflows.ja.md#interactive-rebase) を参照
- **ネイティブな Worktree（タブ形式）** — 現在のブランチに影響を与えずに別のブランチを独立したフォルダにチェックアウトでき、メニューをもぐることなくタブストリップで切り替え可能 — [Worktrees](docs/manual/workflows.ja.md#ワークツリー) を参照
- **ネイティブな Git LFS（ファイルロック機能付き）** — 純 Rust クライアント、外部の `git-lfs` バイナリ不要 — ファイル単位ではなくバッチ処理でダウンロードしてインラインプレビューもサポート、さらに組み込みファイルロック機能と、容量がどこに消えたか一目でわかる[ストレージ分析・ワンクリック整理](docs/manual/workflows.ja.md#lfs-ストレージ整理)も付属（ほとんどの Git GUI はロックも整理も CLI に任せている） — [Git LFS](docs/manual/workflows.ja.md#ファイルを探索) を参照

### こんな人向け

- 大型リポジトリで Git GUI が遅くなるのにうんざりしている開発者
- ブラウザを変装した道具よりも、ネイティブで集中できるツールが好きな人
- Windows で通常のツール以外の現代的な選択肢を探している人

## ダウンロード

最新のインストーラは [Releases](../../releases) ページから入手してください。

### リリースチャネル

| チャネル | 説明 | 入手場所 |
|---|---|---|
| **Stable** | 検証済みの安定版リリース。日常使用推奨。 | [Latest release](../../releases/latest) |
| **Preview** | 次期機能、ほぼ安定版。 | [Pre-releases](../../releases) (*Pre-release* 表記) |

自動アップデートが組み込まれています — **Settings → Update** でチャネルを選択してください。

## マニュアル

Glance が初めてですか？ [マニュアル](docs/manual/README.ja.md) では、始め方、コアワークフロー、キーボードショートカット、トラブルシューティングを扱っています。

## Glance を支援する

Glance は今、商用利用を含めて誰にでも無条件に無料です。役に立ったのであれば、[小さな寄付を検討してください](https://onmcore.github.io/glance-releases/sponsor.html) — 全く強制ではなく、開発継続に大きな力になります。

## バグ報告 & フィードバック

- バグを見つけたら [Issue を開く](https://github.com/onmcore/glance-releases/issues/new)
- 機能のアイデアがあれば [Discussion を始める](https://github.com/onmcore/glance-releases/discussions)

Glance は私一人で開発しており、すべてのレポートを自分で読んでいます。そのため返信に1、2日かかることがあります。

## ライセンス

Glance は現在、商用利用を含め誰でも無料で使用できます — ライセンスキーや支払いは不要です。自発的な寄付は歓迎しますが任意です。将来のバージョンで有料の商用ライセンスが導入される可能性がありますが、すでにこの契約の下でリリースされたバージョンには影響しません。

無修正の再配布は許可されていますが、リバースエンジニアリング、修正、再パッケージングは禁止されています（詳細は [LICENSE](./LICENSE) を参照）。保証なし。

サードパーティコンポーネントとそのライセンスは [THIRD_PARTY_LICENSES.md](./THIRD_PARTY_LICENSES.md) に記載されています。

---

**Glance** © 2026 onmcore
