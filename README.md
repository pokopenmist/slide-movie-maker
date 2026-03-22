# Slide Movie Maker

PDFスライドと音声ファイルを組み合わせて、WebM動画を生成するブラウザアプリです。インストール不要で、GitHub Pagesなどの静的ホスティングで即座に利用できます。

## デモ

**https://pokopenmist.github.io/slide-movie-maker/**

## 機能

- **PDFアップロード** — PDF をページごとにスライド画像へ変換
- **音声同期** — 再生しながらスペースキー/ボタンでスライドの切り替えタイミングを記録
- **手動編集** — 各スライドの開始時刻（秒）を直接入力して微調整
- **高速エクスポート** — WebCodecs API と WebM Muxer により、ブラウザ内でリアルタイムより高速にエンコード
- **出力形式** — VP9映像 + Opus音声の `.webm` ファイル

## 使い方

1. **ステップ 1 — アップロード**
   - PDFファイルと音声ファイル（MP3, WAV, M4A など）をアップロード
   - 「PDFを読み込む」ボタンでスライドを生成

2. **ステップ 2 — タイミング同期**
   - 音声を再生し、スライドを切り替えたいタイミングで「次のスライドへ」ボタンをクリック（または `Space` キー）
   - 右パネルで各スライドの開始時刻を手動修正も可能

3. **ステップ 3 — エクスポート**
   - 「動画を書き出す」ボタンで `.webm` ファイルを生成・ダウンロード

## ブラウザ対応

| ブラウザ | 対応状況 |
|---|---|
| Chrome (最新) | ✅ |
| Edge (最新) | ✅ |
| Safari 17+ | ✅ |
| Firefox | ⚠️ WebCodecs API 非対応（エクスポート不可）|

> **注意:** エクスポート機能は [WebCodecs API](https://developer.mozilla.org/docs/Web/API/WebCodecs_API) を使用します。

## 技術スタック

| ライブラリ | 用途 |
|---|---|
| [React 18](https://react.dev/) | UI フレームワーク |
| [Tailwind CSS](https://tailwindcss.com/) | スタイリング |
| [PDF.js](https://mozilla.github.io/pdf.js/) | PDF レンダリング |
| [WebM Muxer](https://github.com/Vanilagy/webm-muxer) | WebM コンテナ生成 |
| [WebCodecs API](https://developer.mozilla.org/docs/Web/API/WebCodecs_API) | 映像・音声エンコード |
| [Lucide React](https://lucide.dev/) | アイコン |

すべてビルドステップなしでブラウザから直接読み込んでいます。

## ローカルで動かす

```bash
# リポジトリをクローン
git clone https://github.com/pokopenmist/slide-movie-maker.git
cd slide-movie-maker

# 静的サーバーで開く（ローカルファイル直接は PDF.js の CORS 制限あり）
npx serve .
# または
python3 -m http.server 8000
```

ブラウザで `http://localhost:8000` にアクセスしてください。

## デプロイ（GitHub Pages）

`main` ブランチにプッシュすると、GitHub Actions が自動でデプロイします。

```
.github/workflows/pages.yml  ← デプロイワークフロー
index.html                   ← アプリ本体（単一ファイル）
```

設定は `Settings → Pages → Source: GitHub Actions` を選択してください。

## ライセンス

MIT
