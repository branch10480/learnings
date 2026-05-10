# learnings

> わからなかったことを HTML にして貯めておく、branch10480 個人の学習スナップショット書庫。

[![Pages](https://img.shields.io/badge/site-branch10480.github.io%2Flearnings-D97757)](https://branch10480.github.io/learnings/)

## これは何？

「これ、ちゃんと理解してなかったな」と思ったトピックを、Claude Code に頼んで HTML 形式の解説記事として作成し、ここに貯めていく場所です。

- **1 ファイル完結**: 各 entry は外部 CSS/JS に依存しない単体 HTML
- **統一デザイン**: ivory + clay の design-system（[castle/html-artifact](https://github.com/branch10480/castle) と同系統）
- **タグベース分類**: 各 HTML の `<head>` メタタグからタグを抽出
- **GitHub Pages で公開**: <https://branch10480.github.io/learnings/>

## ディレクトリ構成

```
learnings/
├── index.html          # 一覧ページ（タグフィルタ付き）
├── entries/            # 各 explainer の HTML
│   └── YYYY-MM-DD-slug.html
├── _data/              # メタデータの bundle（任意）
├── .github/workflows/  # Pages デプロイなど
└── README.md
```

## 各 entry のメタデータ仕様

各 HTML の `<head>` に以下を埋め込む。インデックス自動生成スキルがこれを scan します。

```html
<meta name="learning:title"   content="EPUB の仕様と内部構造">
<meta name="learning:date"    content="2026-05-11">
<meta name="learning:tags"    content="format, ebook, xml, web">
<meta name="learning:summary" content="一行サマリ（カード表示用）">
<meta name="learning:reading-time" content="20">
```

## 新しい entry を追加する

Claude Code で次のように言うだけ:

```
/learn EPUB の仕様について解説して
```

スキルが以下を自動でやります:

1. `entries/YYYY-MM-DD-slug.html` を生成（design-system テンプレート使用）
2. `<head>` に `learning:*` メタタグを埋め込み
3. `index.html` の `entries-data` JSON を再生成
4. `git add` & commit（push は手動）

## ローカルで確認する

```bash
open ~/Desktop/learnings/index.html
```

または簡易サーバを立てて:

```bash
cd ~/Desktop/learnings && python3 -m http.server 8080
# → http://localhost:8080/
```

## ライセンス

文章・コードは MIT。デザインシステムは castle/html-artifact 由来。
