# Javaのバージョン違いが発生した場合の対応
Javaのバージョン違いが発生した場合の対応について記載します。
## 対処法
### インストールされているJavaの一覧を表示
```zsh
/usr/libexec/java_home -V
```
### flutterで使用するJavaのバージョンを指定
```zsh
flutter config --jdk-dir="/Library/Java/JavaVirtualMachines/amazon-corretto-17.jdk/Contents/Home"
```

## 参考サイト
- [FlutterのAndroid ビルド時にUnsupported class file major version 65](https://zenn.dev/yu1ro/articles/761812f0985cc6)
- []()