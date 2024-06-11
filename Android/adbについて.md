# adb
## ターミナルにadbのパスを通す(Mac)
ADBとは、「Android Debug Bridge」の略で、Android端末とやりとりするための多用途なコマンドである。アプリのインストールやアンインストール、クラッシュログの出力など、さまざまな操作が行える。
### Android SDK locationを調べる
- Android Studioを起動しSDK Locationを調べる
- 大体、`/Users/ユーザ名/Library/Android/sdk`が初期設定から変更しない場合ある。

### adbコマンドのファイルパスを通す
adbコマンドはsdkフォルダのplatform-toolsにあるので、ファイルパスを通すために下記を追記する。
```
export PATH=$PATH:/Users/ユーザ名/Library/Android/sdk/platform-tools
```
上記を追加する場所は下記コマンドを実行して、設定ファイルを開く。
```
$ open ~/.zshrc
$ vim ~/.zshrc
  または
$ open ~/.bash_profile
$ vim ~/.bash_profile
```
- テキストエディタを選択する場合: open
- vimを選択する場合：vim
  - vimを利用する場合は[vimチートコード](../vimチートコード.md)を参照する。

上記コマンドどちらを選択するかは、下記コマンドを実行しシェルの種類を確認する。
```
echo $SHELL

// 実行結果
/bin/zsh
```

bashの編集後は下記コマンドを実行し、編集内容を反映させる。
```
$ source .zshrc
$ source .bash_profile
$ source .bashrc
```

次に、USBデバッグを有効にした上でUSBケーブルでスマホをつなぎ、下記コマンドを実行するとデバイスがつながっているかを確認できる。
```
$adb devices
```
### adbコマンドでapkをインストールする
```
adb install xxx.apk
```
xxx.apkはapkファイルまでのパスを入れる

### adbコマンドでエミュレータをキルする
`adb devices`コマンドで起動しているエミュレータを調べる<br>
```
% adb devices
List of devices attached
emulator-5558	device
emulator-5556	device
emulator-5554	device
```
下記のコマンドで指定のエミュレータをキルする
```
adb -s emulator-5554 emu kill
```

### adbでServiceを実行する
```
adb shell am startservice -n <アプリのパッケージ名>/<Serviceクラスのパッケージ名>.<Serviceクラス名>
```
#### 参考サイト
- [adbを使ってAndroidアプリのServiceを実行する方法](https://tech.pepabo.com/2024/05/28/android-start-service-from-cli/)

### AndroidデバイスでFirebaseDebugViewモードを有効にする方法
ターミナルで`cdコマンド`で下記に移動する。
```
/Users/takayukishoji/Library/Android/sdk/platform-tools
```

下記コマンドを実行することでデバッグモードが有効になる。
```
adb shell setprop debug.firebase.analytics.app <package_name>
```

下記サイトのように記載はされているが、コマンドの実行場所が記載がないため、ぬまる原因になった。2つめのサイトでその原因を知ることになった。
- [イベントのデバッグ](https://firebase.google.com/docs/analytics/debugview?hl=ja)
- [Enable Firebase DebugView mode on an Android device](https://write.agrevolution.in/enable-firebase-debugview-mode-on-an-android-device-a6aa108acb56)