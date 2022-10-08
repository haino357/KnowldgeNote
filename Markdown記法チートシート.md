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

## 表・テーブル
表・テーブルの作成ツール：https://notepm.jp/markdown-table-tool

## Markdownを用いたVSCodeの拡張機能
- [Markdown Preview Enhanced](https://shd101wyy.github.io/markdown-preview-enhanced/#/)
  - Markdown記法でフローチャートなどを作成する拡張機能

## `detailsタグ`を利用した折りたたみ
```
<details>
<summary>testテスト</summary>
testtestテスト
</details>
```
下記実際の動作
<details>
<summary>testテスト</summary>
testtestテスト
</details>