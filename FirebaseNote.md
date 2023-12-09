# [Firebase](https://console.firebase.google.com/u/0/?hl=ja)

## Google Analytics
Google アナリティクスは、アプリの使用状況や動作に関するデータを収集する。このSDKは主に下記の2種類の情報を記録する。

- イベント: ユーザーの操作、システム イベント、エラーなど、アプリで起こっていること。
- ユーザープロパティ: 言語や地域など、ユーザー層を示す属性。自由に定義できる。

アナリティクスでは、一部のイベントとユーザープロパティが自動的にログに記録される。これらのログ記録を有効にするコードを追加する必要はない。
### Android
#### [AndroidプロジェクトにFirebaseを追加する](https://firebase.google.com/docs/android/setup?hl=ja)
**前提条件**
- Android Studioの最新バージョンをインストールするか、更新する。
- プロジェクトが次の要件を満たしていることを確認する。
  - ターゲットがAPIレベル 19（KitKat）以上であること
  - Android 4.4 以上を使用していること
  - Jetpack（AndroidX）を使用していること。次のバージョン要件を満たしている必要がある。
    - `com.android.tools.build:gradle` v3.2.1 以降
    - `compileSdkVersion` 28 以降

#### [Firebase コンソールを使用して Firebase を追加する](https://firebase.google.com/docs/android/setup?hl=ja#console)
**前提**
Firebaseのプロジェクトはすでに作成されているとする。

**手順**
プロジェクト概要画面で、アプリの追加ボタンを押下する。
iOS,Adroid,Web,Unityのプラットフォーム選択にて、Androidを選択する。

