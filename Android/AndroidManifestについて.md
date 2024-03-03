# AndroidManifestについて

## AndroidManifestとは
AndroidManifest.xmlは、Androidアプリケーションの設定情報を記述するためのXMLファイルです。アプリケーションのパッケージ名、アプリケーションのアイコン、アプリケーションの権限、アプリケーションの構成などの情報を記述します。

## AndroidManifestの構成
AndroidManifest.xmlは、以下のような構成になっています。

```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.example.myapp"
    android:versionCode="1"
    android:versionName="1.0" >

    <uses-sdk
        android:minSdkVersion="8"
        android:targetSdkVersion="17" />

    <application
        android:allowBackup="true"
        android:icon="@drawable/ic_launcher"
        android:label="@string/app_name"
        android:theme="@style/AppTheme" >
        <activity
            android:name="com.example.myapp.MainActivity"
            android:label="@string/app_name" >
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>
</manifest>
```

## メインの要素
- `manifest`要素
  - `package`属性: アプリケーションのパッケージ名を指定します。
  - `android:versionCode`属性: アプリケーションのバージョンコードを指定します。
  - `android:versionName`属性: アプリケーションのバージョン名を指定します。
  - `uses-sdk`要素: アプリケーションが対象とするSDKバージョンを指定します。
  - `application`要素: アプリケーションの設定情報を記述します。
  - `activity`要素: アプリケーションのアクティビティを指定します。
  - `intent-filter`要素: アクティビティが受け取るインテントを指定します。
  - `action`要素: インテントのアクションを指定します。
  - `category`要素: インテントのカテゴリを指定します。
  - `data`要素: インテントのデータを指定します。
  - `service`要素: アプリケーションのサービスを指定します。
  - `receiver`要素: アプリケーションのブロードキャストレシーバを指定します。
  - `provider`要素: アプリケーションのコンテンツプロバイダを指定します。
  - `uses-library`要素: アプリケーションが使用するライブラリを指定します。
  - `instrumentation`要素: アプリケーションのテストを行うためのインストゥルメンテーションを指定します。
  - `permission`要素: アプリケーションが使用するパーミッションを指定します。
  - `permission-group`要素: アプリケーションが使用するパーミッショングループを指定します。
  - `permission-tree`要素: アプリケーションが使用するパーミッションツリーを指定します。
  - `uses-configuration`要素: アプリケーションが使用する構成を指定します。
  - `uses-feature`要素: アプリケーションが使用する機能を指定します。
  - `supports-screens`要素: アプリケーションがサポートする画面の情報を指定します。
  - `compatible-screens`要素: アプリケーションが互換性のある画面の情報を指定します。
  - `supports-gl-texture`要素: アプリケーションがサポートするOpenGLテクスチャの情報を指定します。
  - `uses-permission`要素: アプリケーションが使用するパーミッションを指定します。
  - `uses-configuration`要素: アプリケーションが使用する構成を指定します。
  - `uses-feature`要素: アプリケーションが使用する機能を指定します。
  - `supports-screens`要素: アプリケーションがサポートする画面の情報を指定します。
  - `compatible-screens`要素: アプリケーションが互換性のある画面の情報を指定します。
  - `supports-gl-texture`要素: アプリケーションがサポートするOpenGLテクスチャの情報を指定します。
  - `uses-permission`要素: アプリケーションが使用するパーミッションを指定します。
  
## アプリの権限を宣言する
アプリケーションが使用する権限を宣言するために、`<uses-permission>`要素を使用します。
追加する場所は、AndroidManifest.xmlの`<manifest>`要素の直下に記述します。

```xml
<uses-permission android:name="android.permission.INTERNET" />  // インターネットにアクセスする権限
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />  // ネットワークの状態を取得する権限
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />  // 外部ストレージに書き込む権限
<uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />  // 外部ストレージから読み込む権限
<uses-permission android:name="android.permission.CAMERA" />  // カメラを使用する権限
<uses-permission android:name="android.permission.RECORD_AUDIO" />  // 録音する権限
<uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />  // 精密な位置情報にアクセスする権限
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />  // おおまかな位置情報にアクセスする権限
<uses-permission android:name="android.permission.VIBRATE" />  // バイブレーションを使用する権限
<uses-permission android:name="android.permission.FLASHLIGHT" />  // フラッシュライトを使用する権限
<uses-permission android:name="android.permission.BLUETOOTH" />  // Bluetoothを使用する権限
<uses-permission android:name="android.permission.BLUETOOTH_ADMIN" />  // Bluetoothの管理をする権限
<uses-permission android:name="android.permission.RECEIVE_BOOT_COMPLETED" />  // デバイスの起動が完了したことを受信する権限
<uses-permission android:name="android.permission.WAKE_LOCK" />  // スリープを解除する権限
<uses-permission android:name="android.permission.GET_ACCOUNTS" />  // アカウントのリストを取得する権限
<uses-permission android:name="android.permission.USE_CREDENTIALS" />  // 認証情報を使用する権限
<uses-permission android:name="android.permission.READ_CONTACTS" />  // 連絡先を読み込む権限
<uses-permission android:name="android.permission.WRITE_CONTACTS" />  // 連絡先を書き込む権限
<uses-permission android:name="android.permission.READ_CALENDAR" />  // カレンダーを読み込む権限
<uses-permission android:name="android.permission.WRITE_CALENDAR" />  // カレンダーを書き込む権限
<uses-permission android:name="android.permission.READ_CALL_LOG" />  // 通話履歴を読み込む権限
<uses-permission android:name="android.permission.WRITE_CALL_LOG" />  // 通話履歴を書き込む権限
<uses-permission android:name="android.permission.CALL_PHONE" />  // 電話をかける権限
<uses-permission android:name="android.permission.READ_PHONE_STATE" />  // 電話の状態を読み込む権限
<uses-permission android:name="android.permission.READ_PHONE_NUMBERS" />  // 電話番号を読み込む権限
<uses-permission android:name="android.permission.ANSWER_PHONE_CALLS" />  // 電話を受ける権限
<uses-permission android:name="android.permission.ADD_VOICEMAIL" />  // ボイスメールを追加する権限
<uses-permission android:name="android.permission.USE_SIP" />  // SIPを使用する権限
<uses-permission android:name="android.permission.PROCESS_OUTGOING_CALLS" />  // 発信中の通話を処理する権限
<uses-permission android:name="android.permission.BODY_SENSORS" />  // ボディセンサーを使用する権限
<uses-permission android:name="android.permission.SEND_SMS" />  // SMSを送信する権限
<uses-permission android:name="android.permission.RECEIVE_SMS" />  // SMSを受信する権限
<uses-permission android:name="android.permission.READ_SMS" />  // SMSを読み込む権限
<uses-permission android:name="android.permission.RECEIVE_WAP_PUSH" />  // WAP PUSHを受信する権限
<uses-permission android:name="android.permission.RECEIVE_MMS" />  // MMSを受信する権限
```
### 参考
- [アプリの権限を宣言する](https://developer.android.com/training/permissions/declaring?hl=ja)