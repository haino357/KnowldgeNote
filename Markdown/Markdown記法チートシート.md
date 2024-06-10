# Markdown記法チートシート

## 太字・強調
****

## コードの挿入
```
```

## 画像挿入
画像自体の保管場所は個人的にはGit管理しているディレクトリの一番上に`Pictureフォルダ`を作成しそこに保存し活用する。
```
![](画像のURL)
<img src="画像のURL" width="サイズを入力">
```
参考としてサイズは"600"がちょうど良い感じ

### 画像を並べる
**横並び**
```
![](画像のURL)![](画像のURL)
<img src="画像URL"><img src="画像URL">
```
スペースを開ける
```
![](画像のURL) ![](画像のURL)
<img src="画像URL"> <img src="画像URL">
```

## 表・テーブル
表・テーブルの作成ツール：https://notepm.jp/markdown-table-tool

## Markdownを用いたVSCodeの拡張機能
- [Markdown Preview Enhanced](https://shd101wyy.github.io/markdown-preview-enhanced/#/)
  - Markdown記法でフローチャートなどを作成する拡張機能

## `detailsタグ`を利用した折りたたみ
```
<details>
<summary>testテスト</summary><div>
testtestテスト
</div></details>
```
`<div>`を追加しないとレンダリングが崩れる

下記実際の動作
<details>
<summary>testテスト</summary><div>
testtestテスト
</div></details>

## Alerts
重要な情報を強調する際に使用できるブロッククォート構文に基づいたMarkdown拡張
```
> [!NOTE]
> Useful information that users should know, even when skimming content.

> [!TIP]
> Helpful advice for doing things better or more easily.

> [!IMPORTANT]
> Key information users need to know to achieve their goal.

> [!WARNING]
> Urgent info that needs immediate user attention to avoid problems.

> [!CAUTION]
> Advises about risks or negative outcomes of certain actions.
```
<img alt="" src="/Picture/markdown-alerts-rendered.webp" width="500">

## Label
GitHub公式の機能ではないが、下記リンクを参考にしてREADMEなどにバッジをつけることができる。
[Shields.io](https://shields.io/)

![must](https://img.shields.io/badge/review-must-critical.svg)
修正してほしい項目がある場合に使用する。
```
![must](https://img.shields.io/badge/review-must-critical.svg)
```
![ask](https://img.shields.io/badge/review-ask-9b71ae.svg)
質問をして回答をもらいたいコメントをするときに使用する。
```
![ask](https://img.shields.io/badge/review-ask-9b71ae.svg)
```
![imo](https://img.shields.io/badge/review-imo-yellow.svg)
`In my opinion(私の意見では)` の略で私ならこう書くかもという意見。取り入れるかはレビュワー次第でokくらいのニュアンス
```
![imo](https://img.shields.io/badge/review-imo-yellow.svg)
```
![nits](https://img.shields.io/badge/review-nits-inactive.svg)
nitpick(些細な指摘) typoや改行してないとか余計なスペースがあるとか。Approveするけど細かい部分を言いたい時に使用する。特段返事も要らないよって時に使用する。
```
![nits](https://img.shields.io/badge/review-nits-inactive.svg)
```
![good](https://img.shields.io/badge/review-good-success.svg)
良かった部分があったら積極的に利用する。
```
![good](https://img.shields.io/badge/review-good-success.svg)
```
![tweet](https://img.shields.io/badge/review-tweet-9cf.svg)
ツイート、つぶやき。お気持ち表明したい時などに使用する。
```
![tweet](https://img.shields.io/badge/review-tweet-9cf.svg)
```