# デザイン
## アプリ表示名の変更
アプリの表示名を変更するためには下記を変更する。
ios/Runner/Info.plist
```xml
<key>CFBundleName</key>
<string>アプリ名</string>
```
android/app/src/main/AndroidManifest.xml
```xml
<application
    android:label="アプリ名"
    android:icon="@mipmap/ic_launcher">
```

## マテリアルデザイン
マテリアルデザインのアプリを作成するために、MaterialAppを使用する。そのためには下記をimportする。
Android風のデザインを作成するために、MaterialAppを使用する。
```dart
import 'package:flutter/material.dart';
```
MaterialBottomNavigationのように、タブを切り替えるたびにページがビルドされるとなると、APIで情報を取得して表示しているページの場合、切り替えるたびにAPIリクエストを行い、ページを生成することになる。
情報の鮮度が高く保てますがその分APIの待ちなどで画面が生成できるまでユーザーに待ちの時間を作る可能性も発生

## カッパチーノデザイン
クパチーノデザインのアプリを作成するために、CupertinoAppを使用する。そのためには下記をimportする。
iOS風のデザインを作成するために、CupertinoAppを使用する。
```dart
import 'package:flutter/cupertino.dart';
```
CupertinoBottomNavigationの場合だと、他に画面更新のトリガーを入れない限り、最初に取得した情報のままになっている。
その場合には、pull_to_refresh などで行えるように画面を構築するのも良い。
