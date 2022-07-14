# Flutter Note

## Flutter環境構築
[公式ドキュメント(Mac)](https://docs.flutter.dev/get-started/install/macos)

下記の参考資料がまとまっていて、わかりやすい。
- [Flutterの環境構築(Mac編)](https://zenn.dev/kboy/books/ca6a9c93fd23f3/viewer/5232dc)

## Flutter Hands Onの参考
- [dictionary_hands_on_hinagata](https://github.com/YujiOnishi/dictionary_hands_on_hinagata)
- [flutter_dictionary_hands_on_hand_out](https://github.com/YujiOnishi/flutter_dictionary_hands_on_hand_out/blob/master/%E3%83%8F%E3%83%B3%E3%82%BA%E3%82%AA%E3%83%B3%E3%83%AC%E3%82%B8%E3%83%A5%E3%83%A1.pdf)
- [flutter_dictionary_hands_on_hand_out](https://github.com/YujiOnishi/flutter_dictionary_hands_on_hand_out)

## Dartファイルの新規作成
`Project > lib > New > Dart File`で新規Dartファイルを作成できる。

<img src="/Picture/ScreenShot/新規Dartファイル作成.jpeg" width="600">

## Dartの型
**型の種類**
```
// 数値
num numValue = 123;
// 整数 (numのサブタイプ)
int intValue = 234;
// 浮動小数点数 (numのサブタイプ)
double doubleValue = 345.678;
// 真偽値
bool boolValue = true;
// 文字列
String stringValue = 'Hello, World!';
// リスト
List listValue = [1, 2, 3];
// マップ
Map mapValue = {'key1', 1, 'key2': 2};
```
**型付け**
- Dartは静的型付け
- 型推論により型アノテーションがオプショナル
- 特定の型を期待しない場合は`dynamic`を型アノテーションとして付ける
```
// 型推論により型アノテーションがオプショナル
int value1 = 123; // 👉 型アノテーションあり
var value2 = 234.567; // 👉 型アノテーションなしでも型推論により型が決まる

// 特定の型を期待しない場合は dynamic を型アノテーションとして付ける
dynamic value3 = 'Hello, World!';
value3 = 345;

// コレクションの型推論
var list1 = [123, 234, 345];    // 👉 List<int>型
var list2 = [];                 // 👉 List<dynamic>型
var list3 = [123, 23.4, 567];   // 👉 List<num>型
var list4 = [123, 23.4, '567']; // 👉 List<Object>型

var map1 = {'key1': 123, 'key2': 234};   // 👉 Map<String, int>型 
var map2 = {};                           // 👉 Map<dynamic, dynamic>型
var map3 = {'key1': 123, 'key2': 23.4};  // 👉 Map<String, num>型 
var map3 = {'key1': 123, 'key2': '567'}; // 👉 Map<String, Object>型
```
**型のキャスト**
```
dynamic value = 123;

// as によるキャスト
value as int;    // 👉 OK
value as String; // 👉 TypeError: 123: type 'JSInt' is not a subtype of type 'String'

// コレクションの要素のキャスト
List<dynamic> list = [123, 23.4];
list.cast<num>(); // 👉 OK
list.cast<int>(); // 👉 TypeError: 23.4: type 'JSDouble' is not a subtype of type 'int'
```
**nullオブジェクトの操作**
- `null`はNullクラスの唯一のオブジェクト
- NullクラスはObjectクラスのサブタイプ
- `null`を特定の型にキャストしても`null`のまま
```
final dynamic value = null;

// 特定の型にキャストしても null のまま
value as int; // 👉 null

// NullクラスもObjectのサブタイプ
value.hashCode;   // 👉 0
value.toString(); // 👉 null

// Nullクラスにない操作は例外が発生する。
value + 1; // 👉 NoSuchMethodError: method not found: '$add' on null
```
**数値の型変換**
- int, double への変換用メソッドで行う
- doubleからintへの変換は常に小数点以下を切り捨て
```
123.toDouble();  // 👉 123
123.456.toInt(); // 👉 123
123.999.toInt(); // 👉 123 
```
**文字列から数値に変換**
```
int.parse('123');            // 👉 123
int.parse('123.456');        // 👉 FormatException: 123.456
int.parse('1.23e+2');        // 👉 FormatException: 1.23e+2
int.parse('Hello, World!');  // 👉 FormatException: Hello, World!

double.parse('123');           // 👉 123
double.parse('123.456');       // 👉 123.456
double.parse('1.23e+2');       // 👉 123
double.parse('Hello, World!'); // 👉 FormatException: Invalid double\nHello, World!
```
**数値から文字列に変換**
- String への変換用メソッドで行う
```
const value = 123.456789;

value.toString();               // 👉 '123.456789'
value.toStringAsExponential(2); // 👉 '1.23e+2'
value.toStringAsFixed(2);       // 👉 '123.46'
value.toStringAsPrecision(2);   // 👉 '1.2e+2'
```
**文字列補間**
- 文字列中に $object と記述する
- そのオブジェクトの toString() で文字列化したもので補間
```
var myName = 'Tom';
var yourAge = 20; 
"I'm $myName. You are $yourAge years old."; // "I'm Tom. You are 20 years old."
```
### 文字列型<=>日付型
**ライブラリ設定**
```
pubspec.yamlに下記を記載する

flutter:
    sdk: flutter
flutter_localizations:
    sdk: flutter
```
**文字列型から日付型に変換する**
```
// String から DateTime に変換
DateTime.parse('2020-09-30 12:30:50'); 
```

## ライブラリ
### ライブラリの導入方法
- ライブラリは公式サイト：[pub.dev](https://pub.dev/)を利用して検索する
- ライブラリは`pubspec.yaml`に追記することで追加することができる
- ライブラリの最新バージョンをインストールする場合はバージョンを指定しなくてもいい
- バージョンを指定する場合は記載する

### ライブラリ情報一覧
- 画面のロック
  - [secure_application](https://pub.dev/packages/secure_application)
- スクリーンショット・画面録画禁止
  - [screen_protector](https://pub.dev/packages/screen_protector)
- スプラッシュ画面
  - [flutter_native_splash](https://pub.dev/packages/flutter_native_splash)
- Webview
  - [webview_flutter](https://pub.dev/packages/webview_flutter)
  - [flutter_inappwebview](https://pub.dev/packages/flutter_inappwebview)
- Jsonパース
  - [json_annotation](https://pub.dev/packages/json_annotation)
  - [build_runner](https://pub.dev/packages/build_runner)
  - [json_serializable](https://pub.dev/packages/json_serializable)
- API通信
  - [retrofit](https://pub.dev/packages/retrofit)
  - [dio](https://pub.dev/packages/dio)
  - [retrofit_generator](https://pub.dev/packages/retrofit_generator)
  - [freezed](https://pub.dev/packages/freezed)
- 音楽系
  - [just_audio](https://pub.dev/packages/just_audio)
  - [soundpool](https://pub.dev/packages/soundpool)

## FlutterでOSを判断する
Flutteでのアプリ開発において、iOSとAndroidを判別したい場合には下記コードを書く。
```
import 'dart.io'

// OS名を取得、自分で対応したい場合
string os = Platform.operatingSystem;

// OSごとに判定するプロパティを利用する場合
bool isAndroid = Platform.isAndroid;
bool isAndroid = Platform.isIOS;
bool isAndroid = Platform.isLinux;
bool isAndroid = Platform.isMacOS;
bool isAndroid = Platform.isWindows;
```

## 処理を一時的に止める方法
```
//インポートするライブラリ
import 'dart:async';

//処理を待つメソッド
await Future.delayed(Duration(seconds: 3));

//awaitが無くても大丈夫です
Future.delayed(Duration(seconds: 3));

//secondsの所は下記の値でも指定可能
days //日
hours //時
minutes　//分
seconds　//秒
milliseconds　//ミリ秒
microseconds　//マイクロ秒
```
インポートライブラリ：[dart:async library](https://api.flutter.dev/flutter/dart-async/dart-async-library.html)


## 参考URL
- [Flutter公式ドキュメント](https://docs.flutter.dev/)
- [Flutterの効率良い学び方](https://medium.com/flutter-jp/flutter-learning-c5640c5f05b9)
- 