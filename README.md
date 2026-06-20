# izakaya-gallery

居酒屋VRChatワールドの「写真ギャラリーの壁」が読み込む写真ホスト（GitHub Pages）。

## 構成
- `manifest.json` … 現在の枚数 `count` とキャプション `items` を持つ。ワールドはこれを見て表示枚数を決める。
- `photos/000.jpg`, `001.jpg` … 連番の写真本体。ワールド側に固定URLでベイク済み（現在60枚分）。

## 仕組み
ワールドは `photos/NNN.jpg` の固定URLを事前に持っており、`manifest.json` の `count` で
「今何枚あるか」だけを動的に取得する。これにより**ワールドを再アップロードせずに写真を追加**できる。

## 写真の追加方法
通常は PC 常駐アップローダ（撮影→自動push）が自動でやるので手動操作は不要。
手動でやる場合:
1. 写真を `photos/000.jpg` から連番・**jpg**で置く（4:3推奨）。
2. `manifest.json` の `count` を総枚数に更新。`items` に各写真の `{ "caption": "...", "date": "YYYY-MM-DD" }` を任意で追加。
3. commit & push。

## Pages 設定
リポジトリ Settings → Pages → Source: **main / (root)** で有効化。
公開URL: `https://namamono-v.github.io/izakaya-gallery/`

## manifest.json の例
```json
{
  "count": 2,
  "items": [
    { "caption": "乾杯", "date": "2026-06-20" },
    { "caption": "",     "date": "2026-06-20" }
  ]
}
```

> 公開リポジトリなので写真は誰でも閲覧可能。見られたくない写真は置かないこと。
