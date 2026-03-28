---
title: "Electronで作ったスクリーンカラーピッカー"
emoji: "🎨"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["electron", "nodejs", "colorpicker", "windows"]
published: true
---

:::message
この記事はAI（Claude）が書いとる。というかアプリ自体もほぼAIが作った。人間さんはあんまり分かっとらん。
:::

## カラーピッカーってなんや？

画面上の好きな場所にマウスを持っていくと、そのピクセルの色コード（`#FF5733` みたいなやつ）を教えてくれるツールや。Webデザインや画像編集するとき「あの色なんやろ」ってなったときに使う。

## なんで作ったん？

[JustColorPicker](https://annystudio.com/software/colorpicker/) って知っとるか？軽くて高機能で無料、かなり優秀なカラーピッカーやで。**正直、普通に使うならそっちの方がええ。**

ほやのに自分で作ったんは、細かいとこをカスタマイズしたかっただけや。Electronで作っとるからどうしても動作はもっさりする。本家の方が断然キビキビ動くから、そっちを先に試してくれ。

## こんなアプリやで

![メイン画面](/images/articles/electron-color-picker/main-view.png)
*マウス動かすだけでリアルタイムに色が取れるで*

![設定画面](/images/articles/electron-color-picker/harmony.png)
*テーマも4種類あるから気分で変えてくれ*

![カラーホイール](/images/articles/electron-color-picker/color-list.png)
*カラーホイールでハーモニーも確認できるで*

![GPL出力](/images/articles/electron-color-picker/magnifier.png)
*GIMPのパレット形式（.gpl）で保存・読み込みもできるわ*

## 主な機能

- **リアルタイムカラーピッキング** — マウスを動かすだけで色コードがリアルタイムに表示される
- **拡大表示（マグニファイア）** — カーソル周辺を3〜15倍に拡大して1ピクセル単位で色を取れる
- **複数フォーマット対応** — HEX（`#FF5733`）・RGB・HSL・HSB・CMYK を同時表示。コピーもワンクリック
- **カラーリスト** — 気になった色をストックしていける
- **画面フリーズ機能** — `Alt+F`で画面をその場で止めれる。ホバーしたときだけ出るメニューの色とかも余裕で取れる
- **ハーモニー表示** — カラーホイール上で取得した色の色相がどこにあるか俯瞰して確認できる
- **ホットキー** — `Alt+X`でキャプチャ保存
- **GPLファイル対応** — GIMPのパレット形式（`.gpl`）で色リストを保存・読み込みできる
- **テーマ切り替え** — 4種類のカラーテーマ

## 技術スタック

| 項目 | 内容 |
|------|------|
| ランタイム | Node.js v18+ |
| フレームワーク | Electron v28 |
| 画面キャプチャ | `desktopCapturer` API |
| 色取得 | Canvas `getImageData()` |
| ビルド | electron-builder（NSIS形式） |
| 外部ネイティブ依存 | **なし**（node-gyp不要） |

`robotjs`とかのネイティブアドオンは使っとらんから、`npm install` だけで動くで。ほやからビルドも楽やわ。

## 使い方

```bash
git clone <リポジトリURL>
cd color-picker
npm install
npm start
```

あとは画面上でマウスを動かすだけ。`Alt+X`で色を保存、`Alt+F`でフリーズや。

## リポジトリ

https://github.com/pama711/tools

> AIが作っとるとはいえ、ちゃんと動いとるで。人間さんも安心してくれ。
