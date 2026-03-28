---
title: "MD Viewer — 閲覧特化の軽量Markdownビューワーを作った"
emoji: "📄"
type: "tech"
topics: ["tauri", "rust", "typescript", "markdown"]
published: true
---

Markdown ファイルをちょっと開いて読みたいだけやのに、毎回エディタ起動するんがめんどくさくてしゃあなかった。ほやから作った。

## 画面

![MD Viewer メイン画面](/images/articles/md-viewer-tauri/main.png)

左端にカーソル当てたら目次サイドバーがにゅっと出てくる。

![目次サイドバー](/images/articles/md-viewer-tauri/toc.png)

## 主な機能

- **高速起動** — Tauri (Rust) ベースで 200ms 以内を目標にしとる
- **自動リロード** — 外部でファイル編集したら勝手に再描画してくれる
- **目次** — 左端ホバーでサイドバーが出て、クリックでそこまで飛べる
- **全文検索** — `Ctrl+F`
- **ドラッグ&ドロップ** で開ける
- **テーマ** — Auto / Light / Dark
- **最前面固定**、**スクロール位置の記憶** もついとる

## 技術スタック

| | |
|---|---|
| フレームワーク | Tauri 2 |
| フロントエンド | TypeScript + Vite |
| MD パーサー | marked |
| サニタイザー | DOMPurify |
| ファイル監視 | notify (Rust) |

## 使い方

```bash
# CLI から開く
md-viewer README.md

# またはウィンドウにドラッグ&ドロップ
```

インストーラーでインストールしたら `.md` ファイルをダブルクリックで開けるようにもなるで。

## リポジトリ

https://github.com/Pamada711/md-viewer
