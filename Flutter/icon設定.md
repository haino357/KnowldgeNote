# iconの設定
最初に下記パッケージをインストールする。
[flutter_launcher_icons](https://pub.dev/packages/flutter_launcher_icons)
```
flutter pub add flutter_launcher_icons
```
下記のように画像の格納場所を設定する
```
assets
└── images
    ├── icon.png
    └── icon_adaptive_foreground.png
```
pubspec.yamlに下記を追加する
```yaml
dev_dependencies:
  flutter_launcher_icons: ^0.9.2

＃ 下記に設定を追加する
flutter_launcher_icons:
  android: "launcher_icon"
  ios: true
  image_path: "assets/images/takabata_icon.png"
  min_sdk_android: 28 # android min sdk min:16, default 21
  web:
    generate: true
    image_path: "path/to/image.png"
    background_color: "#hexcode"
    theme_color: "#hexcode"
  windows:
    generate: false
    image_path: "path/to/image.png"
    icon_size: 48 # min:48, max:256, default: 48
  macos:
    generate: false
    image_path: "path/to/image.png"
```
下記コマンドを実行する
```
flutter pub get
flutter pub run flutter_launcher_icons:main
```