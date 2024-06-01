# Webview

## 1. FlutterでWebviewを利用する
- [webview_flutter](https://pub.dev/packages/webview_flutter)を利用する場合
- [flutter_inappwebview](https://pub.dev/packages/flutter_inappwebview)を利用する場合

`webview_flutter`または`flutter_inappwebview`パッケージを利用することで、Flutterアプリ内でWebviewを利用することができる。

### 1.1. インストール
下記コマンドを実行することで、`webview_flutter`パッケージをインストールすることができる。
```sh
flutter pub add webview_flutter
```
下記コマンドを実行することで、`flutter_inappwebview`パッケージをインストールすることができる。
```sh 
flutter pub add flutter_inappwebview
```

### 1.2. サンプルコード
下記プロジェクトでサンプルコードを作成

## Flutterで実現可能なWebViewの形式
- flutterのWebView
  - webview_flutterで実現可能なシンプルなWebView
- ネイティブなWebView
  - Android,iOSのWibViewを表示する
- Chrome、SafariのWebView
  - アプリ内で、iOSはSafari、AndroidはChromeでWebViewを表示する

| Package              | flutterのWebView | ネイティブなWebView	 | Chrome、SafariのWebView | 
| -------------------- | ---------------- | -------------------- | ----------------------- | 
| webview_flutter      | ○               | x                    | x                       | 
| flutter_inappwebview | ○               | ○                   | ○                      | 


## 参照パッケージ一覧
- [パッケージ一覧.md](Flutter/Webview.md)

## 参考記事
- [Flutter WebViewについてまとめてみた](https://zenn.dev/taku_zenn/articles/a7ef926c73ec3d)
  - 参考日：2024/02/25