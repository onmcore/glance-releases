# Glance

Windows用 超高性能 Git GUI。

[![Download for Windows](https://img.shields.io/github/v/release/onmcore/glance-releases?label=Download%20for%20Windows&color=2f6feb)](https://github.com/onmcore/glance-releases/releases/latest)

[English](README.md) | [한글](README.ko.md) | [日本語](README.ja.md) | [Deutsch](README.de.md)

![Glance で Linux カーネルリポジトリを閲覧する様子 — コミットグラフ、コミット詳細、diff ステージング](docs/manual/assets/gifs/repo-open.gif)

このリポジトリは Glance の公式バイナリリリースとリリースノートをホストしています。

## Glance について

Glance は一つの執着を持って一から作られた Git GUI です：**速度**。数百万のコミット、数十万のファイルを含むリポジトリでも素早く反応し、メモリ使用量も少なく保ちます。

Glance は**個人・非商用利用であれば完全に無料**です — 試用期限なし、機能ロックなし、アカウント登録不要。

一人で開発しています — 本業は C++ ゲーム開発ですが、このプロジェクトでは Rust、Tauri、Solid.js を学びながら、AI ペアリングを活用して開発しています。

### ハイライト

- **他のツールが遅くなる場面で高速** — エンタープライズ規模のモノレポで即座に応答
- **軽いメモリフットプリント** — ギガバイト級の使用量ではありません
- **Tauri ランタイム** — 小さいインストーラ、Electron 並みのフットプリントではなし
- **完全な Git ワークフロー** — branch、merge、rebase、stash、cherry-pick、blame、履歴可視化

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

Glance は個人・非商用利用であれば完全に無料です。役に立ったのであれば、[小さな寄付を検討してください](https://onmcore.github.io/glance-releases/sponsor.html) — 全く強制ではなく、開発継続に大きな力になります。

## バグ報告 & フィードバック

- バグを見つけたら [Issue を開く](https://github.com/onmcore/glance-releases/issues/new)
- 機能のアイデアがあれば [Discussion を始める](https://github.com/onmcore/glance-releases/discussions)

Glance は私一人で開発しており、すべてのレポートを自分で読んでいます。そのため返信に1、2日かかることがあります。

## ライセンス

Glance は個人・非商用利用であれば無料で使用できます。自発的な寄付は歓迎しますが、強制ではありません。

無修正の再配布は許可されていますが、リバースエンジニアリング、修正、再パッケージングは禁止されています（詳細は [LICENSE](./LICENSE) を参照）。保証なし。

サードパーティコンポーネントとそのライセンスは [THIRD_PARTY_LICENSES.md](./THIRD_PARTY_LICENSES.md) に記載されています。

---

**Glance** © 2026 onmcore
