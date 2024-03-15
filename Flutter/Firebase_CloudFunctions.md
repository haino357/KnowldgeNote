## CloudFunctionsとは
サーバー内に関数を保存して、必要なタイミングで呼び出すことができるサービス。
FirebaseのCloudFunctionsは、サーバーレスアーキテクチャを採用しているため、サーバーの設定や管理が不要で、簡単にサーバーサイドの処理を実装することができる。
例として下記がある。
- データを処理する
- Push通知を送る
- Firebaseを監視して、特定の条件に合致したら処理を実行する

## FunctionsをFlutterで使用する方法
1. Firebaseプロジェクトを作成し、Firebase CLIをインストールする。
2. Flutterプロジェクトを作成し、Firebaseプロジェクトと紐付ける。
3. FirebaseプロジェクトにFunctionsを追加する。
4. FlutterプロジェクトでFunctionsを呼び出す。
5. Functionsを実行する。

### 使用するパッケージ
- [firebase_core](https://pub.dev/packages/firebase_core)
- [cloud_functions](https://pub.dev/packages/cloud_functions)


### Functionsのセットアップ
firebase-toolsをプロジェクトファイルにインストール
```
npm install -g firebase-tools
```
Functionsと必要なツールをプロジェクトファイルに追加
```
firebase init functions
```
上記を実行すると、下記質問が表示される。
> ? What language would you like to use to write Cloud Functions? (Use arrow keys)
これは何の言語でFunctionsを書くかを選択する質問で、JavaScriptかTypeScript、Pythonのいずれかを選択する。

> ? Do you want to use ESLint to catch probable bugs and enforce style? (y/N)
これはESLintを使うかどうかを選択する質問で、yを選択するとESLintを使うことになる。

上記が完了すると、Flutterのプロジェクトファイルにいくつか新しいファイルが生成される。
重要なものを下記に示す。
| path                   | 説明                                          | 
| ---------------------- | --------------------------------------------- | 
| functions/index.js     | ここに関数を書いていきます                    | 
| functions/package.json | Flutterでいうpubspec.yamlのようなもの         | 
| firebase.json          | 作った関数をFunctionsにデプロイするために使う | 
| .firebaserc            | Firebaseのプロジェクトを指定するために使用    | 

### Functionsを実行する
`index.js`を編集し、実行する関数を追加する。
```js
const functions = require("firebase-functions");

exports.helloWorld = functions.https.onRequest((request, response) => {
  response.send("Hello from Firebase!");
});
```
上記の関数は、`https://<your-project-id>.cloudfunctions.net/helloWorld`にアクセスすると、`Hello from Firebase!`というレスポンスが返ってくる。
また、`exports.`の後の部分が関数名になる。

Functionsをデプロイするためには、下記コマンドを実行する。
```
firebase deploy --only functions
```
`--only functions`をつけることでfunctionsのみデプロイすることがでる。
ここでのfunctionsは`firebase.json`で名前を指定されている。
