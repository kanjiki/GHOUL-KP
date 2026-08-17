# GHOUL KP STYLE TEST

GHOUL KP STYLE TEST の独立リポジトリです。GitHub Pages 版フロントエンドと、回答保存用 Google Apps Script を管理します。

## 公開URL

`https://kanjiki.github.io/GHOUL-KP/`

## 構成

- `index.html` — GitHub Pages 用エントリーポイント
- `assets/` — スタイル、診断データ、採点・画面・共有ロジック
- `apps-script/Code.gs` — 回答保存API + 旧GAS URLからGitHub Pagesへの転送
- `apps-script/appsscript.json` — Apps Script manifest

## データ保存

回答は既存の Google Apps Script Web App へ `POST` し、既存の `GHOUL KP STYLE TEST 回答集計` スプレッドシートへ保存します。

既存 Web App endpoint:
`https://script.google.com/macros/s/AKfycbzdIcT7AkIuF1qyQTAEcIqgrFuiwJZdcsiZY7TPo9KKNziWKR1R1DYkUyTAkRdqZQXaeA/exec`

## 旧URLからの移行

- 旧GAS URL → `https://kanjiki.github.io/GHOUL-KP/` へ転送
- 旧 `kanjiki-HP/ghoul-kp-style/` → 新repoへ転送予定
- Apps Script Web App の `POST` は回答保存APIとして継続

## v1.2 calibration

2026-08-17 時点の128回答（詳細96 / クイック32）の再解析をもとに調整しています。

- 厳格度を `-100〜+100` の指数へ正規化
- Q3 / Q8 / Q17 の厳格度寄与を縮小
- Q19、Q2、Q6、Q17、Q18、Q11 の理由文を識別しやすく修正
- Q1 / Q5 / Q13 の頻出自由裁定を選択肢へ反映
- Q12 に「クリティカルチケット自体を採用していない」を採点対象外として追加
- 回答に厳格度指数・診断バージョン・設問セットバージョンを保存

G/H/O/U/L の軸の重み自体は変更していません。
