# マシン環境
- マシン
  - M1 MacbookAir 2020
- OS
  - macOS Ventura Ver.13.0.1
- シェル
  - zsh 5.8 (x86_64-apple-darwin20.0)

## 時間環境設定
iOSのシミュレータはMacのシステム時間と同期している。そのためシステム時間を変更することでシミュレータの時間設定も変更できる
**システム環境設定から変更する**
`システム環境設定 > 一般 > 日付と時刻`


# ショートカットキー
## メニューバーを操作する
- `control + fn + F2`：メニューバーを操作する
## スクリーンショット
- 画像ファイルが生成する
  - `Shift + Command + 3`：全画面を撮影する。
  - `Shift + Command + 4`：指定した範囲を撮影する。画像ファイルが生成される。
  - `Shift + Command + 4` → Space：指定したウインドウを撮影する。
- クリップボードに保持する。
  - `Shift + Command + control + 3`：全画面を撮影する。
  - `Shift + Command + control + 4`：指定した範囲を撮影する。
  - `Shift + Command + control + 4` → Space：指定したウインドウを撮影する。

## Finder関連ショートカットキー
- `command + N` : 新規Finderウィンドウを開く
- `command + shift + N` : 新規フォルダ作成
- `command + T` : 新規Finderタブを開く
- `command + O` : Finderを開く

## Finderで隠しファイル、隠しフォルダの表示／非表示
`command + shift + .（コマンド + シフト ＋ ピリオド）`
- 隠しファイルやフォルダの表示と非表示の設定が切り替える。

## Finderでファイルパスを表示
- `option + command + p`

## Finderでファイルパスをコピーする
- `option + command + c`

## Finderでファイルパスで検索する
- `command + shift + G`

## [MacでAppを強制的に終了する方法](https://support.apple.com/ja-jp/HT201276)
`option + command + esc`

- Home：`fn + ←`
- End：`fn + →`
- PageUp：`fn + ↑`
- PageDown：`fn + ↓`
- ブラウザ更新：`command + R`
- Finderの検索を表示する：`option + command + space`
- デスクトップを表示する：`fn + F11`
- 強制終了のためのウインドウを開く：`option + command + esc`
- 日本語と英語の入力変換
  - `fn`
  - `control + Space`

## Macの画面をロックする
- `command + control + q`

## Spotlighte検索ウインドウを開く/閉じる
- `command + space`

## 画像をFinderから確認する方法(クイックルック)
- 見たい画像を選択して、`space`キーを押す

## ウインドウを最小化する
- `command + M`
- `command + option + M`：全てのウインドウを最小化する
- `command + H`：アクティブなウインドウを非表示にする
- `Command + Tabでアプリを選択した後、Optionキーを押してCommandキーを離す`：最小化したウインドウを表示する

# brew(Homebrew)
brew(Homebrew)とは、macOS用パッケージマネージャー

## インストール
インストール前の状態でターミナルで `$ berw` コマンドを使用すると下記が表示される。
```
zsh: command not found: brew
```
インストールするには、ターミナル上で以下のコマンドを実行する。
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```
インストールの確認方法
```
brew -v

// 実行結果
Homebrew 3.4.1
Homebrew/homebrew-core (git revision 743a3e4c909; last commit 2022-03-09)
```


**M1プロセッサ搭載のMacの場合の対応**
M1プロセッサ搭載の場合は`Rosseta`を使用しインストールを行う。
ターミナルの設定を「Rossetaを使用して開く」に変更するためには下記を実施する。
1. Finderの検索で`ターミナル`と検索をかける
2. ターミナルを右クリックして、「情報を見る」をクリック
3. 「Rosseta使用して開く」（またはRosseta2）左横のチェックボックスにチェックを入れる。
4. ターミナルを再起動する。
<img src="Picture/ScreenShot/ターミナルの情報を見る方法.png" width="600">
<img src="Picture/ScreenShot/ターミナルの情報.png" width="600">

