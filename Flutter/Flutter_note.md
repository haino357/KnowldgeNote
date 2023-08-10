# Flutter Note

## Flutter環境構築
[公式ドキュメント(Mac)](https://docs.flutter.dev/get-started/install/macos)

下記の参考資料がまとまっていて、わかりやすい。
- [Flutterの環境構築(Mac編)](https://zenn.dev/kboy/books/ca6a9c93fd23f3/viewer/5232dc)

## Flutter Hands Onの参考
- [dictionary_hands_on_hinagata](https://github.com/YujiOnishi/dictionary_hands_on_hinagata)
- [flutter_dictionary_hands_on_hand_out](https://github.com/YujiOnishi/flutter_dictionary_hands_on_hand_out/blob/master/%E3%83%8F%E3%83%B3%E3%82%BA%E3%82%AA%E3%83%B3%E3%83%AC%E3%82%B8%E3%83%A5%E3%83%A1.pdf)
- [flutter_dictionary_hands_on_hand_out](https://github.com/YujiOnishi/flutter_dictionary_hands_on_hand_out)

## Flutterコマンド
### $ flutter precache
FlutterのSDK内部では必要なデータをGoogleのインフラサーバーから必要なタイミングでダウンロードしている。それを意図的に行うためのコマンド。普通のユーザは基本的に利用する必要ない。

### $ flutter doctor
インストールバージョンやインストールされてないものが無いかなど、Flutter環境診断をする。<br>
Flutter実行出来なくなったなど、困ったらまずこれをやってみると良い。<br>
さらに`-v`オプションをつける事で詳細情報を確認できる。
```
flutter doctor -v
```

### $ flutter --version
現在のSDKバージョンを確認するときに利用する。`flutter doctor`は時間がかかるので、バージョンだけ調べたいときはこれを使う。

### $ flutter upgrade
Flutterのバージョンをアップデートする時に利用する。

### $ flutter downgrade
Flutterのバージョンを一つ前にダウングレードする時に利用する。

### $ flutter channel
現在利用しているFlutter SDKのチャンネルを確認する。
```
$ flutter channel                                 

Flutter channels:
  master
  beta
* stable
```
| チャンネル名 | 内容                                                                                                               | 
| ------------ | ------------------------------------------------------------------------------------------------------------------ | 
| master       | githubのマスターブランチ。不安定な可能性がありますが、最新を使う場合はこれ                                         | 
| dev          | masterに対して自動テスト等をパスした一定品質が担保されているもの (α版相当, Windows/macOS/Linux版はここに含まれる) | 
| beta         | ベータ版機能が有効になったもの                                                                                     | 
| stable       | 正式リリースのステーブル版。普通の開発者はこれを利用                                                               | 

### $ flutter channel チャンネル名
オプションで指定したチャンネルに変更される。
```
$ flutter channel beta
```

### $ flutter devices
Flutterアプリとして実行可能なデバイス一覧を確認できます。<br>
Android/iOSエミュレータの場合は、事前に立ち上げた状態でなければ表示されない。
```
=> % flutter devices
3 connected devices:

Pixel 3a XL (mobile) • 9A2AX0KYUB • android-arm64  • Android 12 (API 32)
macOS (desktop)      • macos      • darwin-arm64   • macOS 11.3.1 20E241 darwin-arm
Chrome (web)         • chrome     • web-javascript • Google Chrome 105.0.5195.125

```

### $ flutter config
`~/.flutter_settings`に設定ファイルがあり、これを更新するコマンド。ファイルを直接編集も可能。一度設定したらその後はほぼ触る事が無いと思われる。<br>
※Windows/Linux/macOSを有効にしておくと、新規プロジェクト作成時にそれら向けのディレクトリが作成されます。
#### Flutter-Webを有効化する
```
$ flutter config --enable-web
```
#### Flutter-Desktop-Linuxを有効化する
```
$ flutter config --enable-linux-desktop
```
#### Flutter-Desktop-macOSを有効化する
```
$ flutter config --enable-macos-desktop
```
#### Flutter-Desktop-Windowsを有効化する
```
$ flutter config --enable-windows-desktop
```

### $ flutter create
Flutterプロジェクト新規作成時に利用する。オプションの最後に出力先のディレクトリ名を指定する。
| オプション             | 内容                                                                                          | 
| ---------------------- | --------------------------------------------------------------------------------------------- | 
| -t, --template=        | app, module, package, pluginのいずれかを指定。デフォルトはapp                                 | 
| --org                  | オーガナイゼーションを指定。デフォルトはcom.example                                           | 
| --project-name         | Flutterプロジェクト名を指定                                                                   | 
| -i, --ios-language     | iOS向けプラットフォーム側のコードの言語でobjc, swiftのいずれかを指定。デフォルトはswift       | 
| -a, --android-language | Android向けプラットフォーム側のコードの言語でjava, kotlinのいずれかを指定。デフォルトはkotlin | 
| --description          | プロジェクト説明文。デフォルトは"A new Flutter project."                                      | 

サンプルコマンド
```
$ flutter create -t app --org com.hoge --project-name ¥
                 example -i swift -a kotlin ¥
                 --description "Example Flutter project." ¥
                 ./example_app
```
一度プロジェクトを作成後、そのプロジェクトディレクトリで`$flutter create .`を実行する事で、現在有効なプラットフォーム`andoid/, linux/など`、足りていないのテンプレートだけ生成してくれる。

### $ flutter clean
ビルド時に生成されるファイル群のクリーン (削除) 時に利用する。`build`と`.dart_toolディレクトリ`を削除してくれます。

### $ flutter pub get
pubspec.yamlを更新したら実行するもの。プラグインのライブラリなどを取得したり更新する。

### $ flutter pub deps
ライブラリの依存関係をツリーで表示してくれる。

### $ flutter build xxx
ターゲット環境 (xxx) を指定してビルドだけ行う。成果物は`./build/xxx`以下に生成される。デフォルトはリリースモードでのビルドになる。
| オプション    | 内容                                                                                                 | 
| ------------- | ---------------------------------------------------------------------------------------------------- | 
| aar           |                                                                                                      | 
| apk           | Android APKファイル                                                                                  | 
| appbundle     | Android App Bundleファイル                                                                           | 
| bundle        | Flutterのフォントや画像等のバンドルのビルド(flutter_assetsディレクトリ以下, DartのJIT用バイトコード) | 
| iso           | iOS向けビルド                                                                                        | 
| ios-framework | .framework向けビルド                                                                                 | 
| web           | Webアプリ向け                                                                                        | 
| macos         | macOSデスクトップ向け(デフォルトはリリースモードでのビルド)                                          | 
| linux         | Linuxデスクトップ向け(デフォルトはリリースモードでのビルド)                                          | 
| windows       | Windowsデスクトップ向け(デフォルトはリリースモードでのビルド)                                        | 

#### --target-platformオプション
ターゲットアーキテクチャを指定してビルドすることが可能。
```
$ flutter build apk --target-platform=android-arm64
```

#### --analyze-sizeオプション
`--analyze-size`オプションを付けることで、ビルド成果物のサイズ情報を確認することができる。
```
$ flutter build macos --analyze-size
Building macOS application...                                           
▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  sample.app                                                               35 MB
  sample.app/
    Contents/
      _CodeSignature                                                        9 KB
      MacOS                                                                66 KB
      Resources                                                           246 KB
      Frameworks                                                           34 MB
      Dart AOT symbols accounted decompressed size                          3 MB
        package:flutter                                                     2 MB
        dart:core                                                         306 KB
        dart:typed_data                                                   221 KB
        dart:ui                                                           191 KB
        dart:async                                                        115 KB
        dart:collection                                                   110 KB
        dart:convert                                                       58 KB
        dart:isolate                                                       40 KB
        dart:io                                                            38 KB
        package:vector_math                                                33 KB
        dart:developer                                                     10 KB
        package:typed_data/
          src/
            typed_buffer.dart                                               7 KB
        package:collection/
          src/
            priority_queue.dart                                             5 KB
        dart:math                                                           4 KB
        dart:ffi                                                            4 KB
        package:sample/
          main.dart                                                         3 KB
        dart:vmservice_io                                                   2 KB
        dart:mirrors                                                       668 B
        dart:nativewrappers                                                382 B
        Never                                                               63 B
      Info.plist                                                            2 KB
▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒
A summary of your macOS bundle analysis can be found at: /Users/kurun/.flutter-devtools/macos-code-size-analysis_01.json

To analyze your app size in Dart DevTools, run the following command:
flutter pub global activate devtools; flutter pub global run devtools --appSizeBase=macos-code-size-analysis_01.json
```

### $ flutter run
プロジェクトのディレクトリ直下で実行するとdevicesに見えているターゲット (Android/iOS優先） 向けにpub getやビルト、インストールまで一連の作業を実行する。

#### $ flutter run --release
リリースモードで実行する。

#### $ flutter run --debug
デバッグモードで実行する。

#### $ flutter run -d xxx
ターゲットデバイスを指定する場合には-dオプションを利用する。flutter devicesで表示されているデバイスのIDを指定する。
```
$ flutter run -d macOS
```

#### $ flutter run --verbose
flutter runコマンド実行中の詳細ログを表示する。

### $ flutter install
ビルド済みのインストールパッケージをデバイスにインストールする。

### $ flutter test
プロジェクト直下のtestディレクトリのユニットテストを実行する。

### $ flutter drive
Flutterアプリのインテグレーションテスト実行コマンド。
```
$ flutter drive --target=test_driver/sample_perf.dart
```

### $ flutter screenshot
現在接続しているデバイスのスクリーンショットを取得する。出力先を指定する場合は、--outオプション (ファイル名も指定必要) を利用する。

### $ flutter --help
ヘルプメッセージを表示する。Flutterコマンドの良いところは、以下のように必要なオプションの後に--helpを付けるとそのオプションに対するヘルプを表示してくれる点。
```
$ flutter --help
$ flutter run --help
```

## Dartファイルの新規作成
`Project > lib > New > Dart File`で新規Dartファイルを作成できる。

<img src="/Picture/Flutter/新規Dartファイル作成.jpeg" width="600">

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

## 変数宣言
**通常の変数宣言**
```
String text = `test`;
```
**private変数の宣言**
変数の前に`_`アンダースコアを追加することでprivate変数にと認識する
```
String _text = `test`;
```

## ライブラリ
### ライブラリの導入方法
- ライブラリは公式サイト：[pub.dev](https://pub.dev/)を利用して検索する
- ライブラリは`pubspec.yaml`に追記することで追加することができる
- ライブラリの最新バージョンをインストールする場合はバージョンを指定しなくてもいい
- バージョンを指定する場合は記載する
- `pubspec.yaml`にライブラリを追加する場合に`dependencies`と`dev_dependencies`の二箇所追加する場所がある。
  - `dependencies`はこのプロジェクトのパッケージで必要なライブラリを設定する場合に記載する
  - `dev_dependencies`は開発段階において必要なライブラリを追加する場合に記載する

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
  - [http](https://pub.dev/packages/http)
- 音楽系
  - [just_audio](https://pub.dev/packages/just_audio)
  - [soundpool](https://pub.dev/packages/soundpool)
- 状態管理
  - [flutter_riverpod](https://pub.dev/packages/flutter_riverpod)
- 環境設定ファイルの管理
  - [flutter_config](https://pub.dev/packages/flutter_config)
  - [dotenv](https://pub.dev/packages/dotenv/example)
  - [flutter_dotenv](https://pub.dev/packages/flutter_dotenv)
    - Publisherが無名なので使う時は注意が必要

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


## Widget
WidgetとはFlutterのUIを構築しているパーツのこと。<br>
さまざまなWidgetを組み合わせることで複雑なUIを構築する。
### Text
#### 長い文字列を省略する
```
Text(
  'あいうえおかきくけこさしすせそたちつてとなにぬねのはひふへほまみむめもやゆよらりるれろ',
  overflow: TextOverflow.ellipsis, // はみ出したことを示すために省略記号を使用
),
```
#### 文字列の行数を指定する
```
Text(
  'あいうえおかきくけこさしすせそたちつてとなにぬねのはひふへほまみむめもやゆよらりるれろ',
  maxLines: 2, // 表示する文字列の行数を指定する
),
```
### Card
#### 背景色を透明にする方法
```
Card(
  color: Colors.transparent,
  elevation: 0,
)
```
### ListView
#### スクロールを無効にする方法
```
ListView(
  physics: const NeverScrollableScrollPhysics(), // 左記を追加する
  children: [~~],
)
``` 
### Container
とても使い勝手が良いWidgetである。<br>
しかし、調整できるプロパティが豊富であるため、使用する意図が一目で理解できない問題がある。<br>
また、豊富なプロパティを内包するがゆえに、重くなりパフォーマンスに影響が出る可能性がある。<br>
Widgetの意図を明確にするために、`Container`の代わりに下記Widgetを利用することを推奨
- `Padding`：パディングを調整するWIdget
- `Align`：子要素の配置を指定するWidget
- `ColoredBox`：内部の色を指定するWidget
- `SizeBox`：高さや幅のサイズを指定するWidget
- `DecoratedBox`：デコレーションを調整するWidget
```
Container(
  height: 50, // 縦幅
  width: 300, // 横幅
  padding: const EdgeInsets.all(8), // 内側の余白(padding)
  margin: const EdgeInsets.all(8), // 外側の余白(margin)
  decoration: BoxDecoration(
    // 枠線の色や太さ設定の指定
    border: Border.all(
      color: Colors.blue,),
    // 枠線の角丸設定
    borderRadius: BorderRadius.circular(8),
    color: Colors.red,
    width: 6,
  ),
  // color: Colors.red,  // 背景色の指定をする、ただし、BoxDecorationがある場合は同時に使えない
  child: const Text(
    'あいうえおかきくけこさしすせそたちつてとなにぬねのはひふへほまみむめもやゆよらりるれろ',
    overflow: TextOverflow.ellipsis, // はみ出したことを示すために省略記号を使用
    style: TextStyle(
      color: Colors.white,
    ),
  ),
),
```
#### 角丸の指定方法
**全体的に角丸**
```
Container(
  width: 100,
  height: 100,
  decoration: BoxDecoration(
    color: Colors.red,
    borderRadius: BorderRadius.circular(10), // ここが指定箇所
  ),
),
```
**一部に角丸**
```
Container(
  width: 100,
  height: 100,
  decoration: BoxDecoration(
    color: Colors.red,
    borderRadius: const BorderRadius.only(
      topLeft: Radius.circular(50), // 左上を丸める
      topRight: Radius.circular(50), // 右上を丸める
      bottomLeft: Radius.circular(50), // 左下を丸める
      bottomRight: Radius.circular(50), // 右下を丸める
    ), // ここが指定箇所
  ),
),
```
**円**
```
Container(
  width: 100,
  height: 100,
  decoration: const BoxDecoration(
    color: Colors.red,
    shape: BoxShape.circle,
  ),
)
```
### Colum & Row
Colum：Widgetを縦に並べるために使用する。
Row：Widgetを横に並べるために使用する。

```
Colum(
  mainAxisAlignment: MainAxisAlignment.start,
  children: <Widget>[],
),
```
#### MainAxisAlignment
start：使用するWidgetの開始位置から配置する<br>
<img src="/Picture/Flutter/MainAxisAlignment_start.png" width="200"><br>
end：使用するWidgetの終了位置から配置する<br>
<img src="/Picture/Flutter/MainAxisAlignment_end.png" width="200"><br>
center：使用するWidgetの中央位置から配置する<br>
<img src="/Picture/Flutter/MainAxisAlignment_center.png" width="200"><br>
spaceBetween：使用するWidgetの中身を均等なスペースをおいて配置する<br>
<img src="/Picture/Flutter/MainAxisAlignment_spaceBetween.png" width="200"><br>
spaceAround：使用するWidgetの中身の両端を均等なスペースをおいて配置する<br>
<img src="/Picture/Flutter/MainAxisAlignment_spaceAround.png" width="200"><br>
spaceEvenly：使用するWidgetの中身を開始、終了、子の間に空きスペースを均等に配置する<br>
<img src="/Picture/Flutter/MainAxisAlignment_spaceEvenly.png" width="200"><br>

### SingleChildScrollView
スクロールビューの際に使用する

### Visibility
Widgetの表示と非表示を切り替えるために使用する
- 表示：`visible: true,`
- 非表示：`visible: false,`
```
Visibility(
  visible: true, 
  child: const Text('Visibilityテスト'),
),
```

### 比率で表示する
```
AspectRatio(
  aspectRatio: 3 / 2, /* 横幅 / 高さ */
  child: Container(),
),
```

## 状態管理
まず、状態とはUIを構築する上で必要なデータのこと。データを元にUIを作る仕組みのことを状態を持つと呼ぶ。<br>
アプリのUIを様々なデータを元に作っている。この様々なデータのことをアプリの状態と呼び、その状態を扱いやすく管理する仕組みを状態管理と言う。<br>

### [Riverpod](https://pub.dev/packages/flutter_riverpod)
複雑になる状態を管理する仕組みの一つ


## フォントやアイコンの情報
- [Google Fonts](https://fonts.google.com/)
  - このサイトにフォントやアイコンの情報を調べることができる
## 参考URL
- [Flutter公式ドキュメント](https://docs.flutter.dev/)
- [Flutterの効率良い学び方](https://medium.com/flutter-jp/flutter-learning-c5640c5f05b9)
- 