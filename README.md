# 学習ログ

> このリポジトリは学習ログアプリに育てるための土台として使います。

HTML/CSS/JavaScriptとlocalStorageだけで動く、毎日の学習内容と集中度を記録するアプリです。

日付ごとに「今日の集中度」と「学習メモ」を保存できます。たとえば「数学の二次関数を復習した」「英単語を10個覚えた」「読書で気になったことをメモした」のように、学習内容を短く記録できます。保存した記録はブラウザのlocalStorageに残るため、ページを閉じても同じブラウザで再度開けば学習記録を見返せます。

## 📱 デモ

🔗 [https://hamadashogo-droid.github.io/my-study-lig/](https://hamadashogo-droid.github.io/my-study-lig/)

![📷 image.png](image.png)

## デモの動かし方

`index.html` をブラウザで開くだけで使えます。ビルドやサーバー起動は不要です。

```text
tiny-diary/
├── index.html
├── styles.css
├── app.js
├── README.md
└── LICENSE
```

## 機能

- 今日の日付を自動セット
- 集中度を5種類から選択
- 今日の学習メモを保存
- 日付ごとに1件の記録として保存
- 同じ日付で保存すると上書き
- 過去ログの一覧表示
- 保存済みログの編集
- 保存済みログの削除
- 学習メモ検索
- 集中度フィルター
- 最近7件の集中度の変化を表示するグラフ

## 使用技術

- HTML
- CSS
- JavaScript
- localStorage

外部ライブラリは使っていません。

## localStorage

保存キーは `tiny-diary.entries.v1` です。

データは次のような配列で保存されます。

```json
[
  {
    "id": "example-id",
    "date": "2026-04-29",
    "mood": "happy",
    "note": "数学の二次関数を復習した",
    "createdAt": "2026-04-29T10:00:00.000Z",
    "updatedAt": "2026-04-29T10:00:00.000Z"
  }
]
```

## 集中度データ

集中度は次の5種類です。

| 値 | 表示 | スコア |
| --- | --- | --- |
| `happy` | よく集中 | 5 |
| `calm` | 集中できた | 4 |
| `normal` | ふつう | 3 |
| `tired` | 少し疲れた | 2 |
| `sad` | 休憩したい | 1 |

学習ペースのグラフでは、最近7件の記録をこのスコアに変換して、SVGの波形グラフとして表示します。

## 教材で説明しやすい流れ

1. フォームから値を受け取る
2. JavaScriptの配列に学習記録を追加する
3. `JSON.stringify` でlocalStorageへ保存する
4. `JSON.parse` でlocalStorageから読み込む
5. 配列をもとに学習記録の一覧と集中度グラフを再描画する

## ファイル構成

- `index.html`: 画面の構造
- `styles.css`: レイアウトと見た目
- `app.js`: 保存、表示、編集、削除、検索、集中度グラフの描画
- `README.md`: この説明ファイル
- `LICENSE`: MITライセンス

## ライセンス

MIT License
