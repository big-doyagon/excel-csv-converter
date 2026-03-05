# Excel → CSV コンバーター（社内配布版）

## フォルダ構成

```
excel-csv-converter/
├── converter.html          ← メインのHTMLファイル（ブラウザで開く）
├── lib/
│   └── xlsx.full.min.js    ← SheetJS ライブラリ本体（※手動で配置）
└── README.md               ← このファイル
```

## セットアップ手順

### 1. SheetJS ライブラリを取得する

以下のURLから **バージョンを固定して** ダウンロードしてください：

```
https://cdn.sheetjs.com/xlsx-0.20.3/package/dist/xlsx.full.min.js
```

> ⚠ `xlsx-latest` ではなく、必ず特定のバージョン番号を指定してください。
> 最新のバージョン番号は https://git.sheetjs.com/sheetjs/sheetjs で確認できます。

### 2. ダウンロードしたファイルを配置する

`lib/` フォルダに `xlsx.full.min.js` として保存します。

### 3. 動作確認

`converter.html` をブラウザで直接開いて、Excelファイルを読み込めれば完了です。

---

## 変更履歴（オリジナルからの差分）

| 項目 | 変更内容 |
|------|----------|
| SheetJS 読み込み | 外部CDN → `./lib/xlsx.full.min.js`（ローカル参照） |
| CSP メタタグ | `script-src 'self' 'unsafe-inline'` を追加 |
| .xlsm 警告 | マクロ有効ブックを読み込んだ際に注意メッセージを表示 |

## 社内Webサーバーで配信する場合

HTTPヘッダーでCSPを設定するとより安全です：

```
Content-Security-Policy: default-src 'self'; script-src 'self' 'unsafe-inline'; style-src 'self' 'unsafe-inline'
```

## ライブラリ更新手順

1. 新バージョンの `xlsx.full.min.js` を公式サイトからダウンロード
2. `lib/xlsx.full.min.js` を差し替え
3. `converter.html` 内のバージョンコメントを更新
4. 動作確認
