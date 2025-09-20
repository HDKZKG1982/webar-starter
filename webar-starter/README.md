# WebAR Starter (MindAR + Three.js)

## 使い方（最短）
1. このフォルダを GitHub にアップロード → リポジトリの Settings → Pages で公開（main / root）
2. `assets/sample-target.jpg` を A4で印刷（ターゲット画像）。
3. スマホで公開URLを開き、印刷したターゲットにカメラを向けると ARが出ます。
4. 右上「画像選択」からその場でオーバーレイ画像を差し替え可能。📸でスナップショット保存。

## イベント名やロゴを変える
- `assets/events.json` にイベントを追記：
```json
{
  "default": {"title": "EVENT TITLE", "logo": "assets/logo.png"},
  "seabass2025": {"title": "シーバスフェスタ 2025", "logo": "assets/logo.png"}
}
```
- 本番URLに `?event=seabass2025` を付与してタイトルとロゴを切替。
- 画像を固定したい場合は `?img=画像URL` を追加。

例：
```
https://your-pages.github.io/webar-starter/?event=seabass2025&img=https://example.com/overlay.png
```

## ターゲット（.mind）を作る
- 今入っている `assets/targets.mind` は空のプレースホルダです。
- 実運用には MindAR CLI で生成してください：
```
npm i -g mind-ar-cli
mindar-image target --image assets/sample-target.jpg --output assets/targets.mind
```
- 複数ターゲットは `--image` を複数指定。ディテールの多い画像（角・模様・高コントラスト）が安定。

## 無料で公開する
- GitHub Pages / Netlify / Cloudflare Pages（HTTPS対応）

## トラブルシューティング
- 何も出ない → HTTPSか、カメラ許可、`.mind` が空でないか。
- 追従が不安定 → ターゲット画像の見直し（特徴点・照明・距離）。
- 画像が出ない → 外部URLはCORS制約に注意（同一オリジンかDataURLを使用）。
