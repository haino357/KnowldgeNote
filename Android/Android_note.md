# [アプリの基礎](https://developer.android.com/guide/components/fundamentals?hl=ja)
## Androidの使用言語
AndroidアプリはKotlinやJava、C++言語を使用して記述できます。
- Kotlin
- Java
- C++

## Android SDK
コードをデータやリソースファイルと一緒に**APK(Androidパッケージ)**にコンパイルします。  
これは`.apk`という接尾語の付いたアーカイブファイルです。1つのAPKファイルにAndroidアプリのすべてのコンテンツが含まれており、  
Android端末はアプリをインストールする際にこのファイルを使用します。

書くAndroidアプリはそれぞれのセキュリティサンドボックス内で動作し、以下のAndroidのセキュリティ機能により保護されています。
- 

## LifeCycle
---


## Explore Android Studio
---
Android Studioのソースコードが入っている場所はウインドウの左側にあるProjectタブにある。  
![ProjectTab](../Picture/ScreenShot/ProjectTab.png) 
  


## アプリのコンポーネント
---



## マニュフェストファイル
---


## アプリのリソース
---



## アーキテクチャ
---
アーキテクチャを直訳すると「建築」や「構造」などの意味があります。  
アプリ開発においてはアプリの設計手法のことを表し、いくつかのパターンがあります。  
これらは先人のエンジニアがよりよいアプリ設計を目指して確立されてきたもので、  
アーキテクチャを適切に導入することで、洗練されたアプリを開発できるようになります。
これより、開発者、ユーザー双方にメリットがあります。

### アーキテクチャの基本概念
1. 関心の分離：役割分担
2. UIをモデルで操作する

#### 1. 関心の分離：役割分担

#### 2. UIをモデルで操作する

### MVP
### MVC
### MVVM
### クリーンアーキテクチャ
### オニオンアーキテクチャ


## UI
---
### Activity
### Fragment
### XML




## memo
---
### 不明単語
- [ ] セキュリティサンドボックス



## INBOX
- [ ] EditTextの内容をクリアにする方法
```Java
EditText editText = findViewById<EditText>(R.id.edit_text_view);
editText.getEditableText().clear();
```
```Kotlin
val editText = findViewById<EditText>(R.id.edit_text_view)
editText.editableText.clear()
```

- [ ] ScrollView  
mainにScrollViewを使うとエラーが発生する

- [ ] Dagger
  - [ ] DIコンテナ

- [ ] DI(Dependency Injection)


### AppCompatActivity
Activityのサブクラス。古いバージョンのAndroidとの下位互換性を提供しながら、最新のAndroidの機能をサポートする。  
可能な限り多くのデバイスとユーザーがアプリを使用するために、常にAppCompatActivityを利用する。

### setContentView() method
実際には整数参照であるR.layout.activity_mainを使用してレイアウトを参照する。

### R class
Rクラスには、resディレクトリのコンテンツを含むすべてのアプリのアセットが含まれる。

## ActionBar
### タイトルを中央揃えにする方法

## BottomNavigationView

## Navigation

## [RecyclerView](https://developer.android.com/guide/topics/ui/layout/recyclerview?hl=ja)
[RecyclerViewのリファレンス](https://developer.android.com/reference/kotlin/androidx/recyclerview/widget/RecyclerView?hl=ja)

依存関係(バージョンはドキュメントを確認)
```build.gradle
dependencies {
    implementation 'androidx.recyclerview:recyclerview:1.1.0'
}
```
  


## [Android Jetpack](https://developer.android.com/jetpack?hl=ja)

## ターミナルにadbのパスを通す(Mac)
### Android SDK locationを調べる
- Android Studioを起動しSDK Locationを調べる
- 大体、`/Users/ユーザ名/Library/Android/sdk`が初期設定から変更しない場合ある。
  - 現在使用中のMacbookAirの場合は`/Users/takayukishoji/Library/Android/sdk`にある。

### adbコマンドのファイルパスを通す
adbコマンドはsdkフォルダのplatform-toolsにあるので、ファイルパスを通すために下記コマンドを実行する。
```
export PATH=$PATH:/Users/ユーザ名/Library/Android/sdk/platform-tools
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

## ソフトキーボードがビューを押し上げないようにする
`AndroidMainfest.xml`に下記を追加する。
```
<activity
   ...
   android:windowSoftInputMode="adjustPan"> 
</activity>
```

## プルダウンの実装
### xmlファイルでSpinnerを実装
```
<Spinner
    android:id="@+id/spinner"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:layout_marginStart="100dp"
    android:layout_marginTop="10dp" />
```
### クラスファイルを実装
シンプルにアダプターを利用し、Spinnerでプルダウンを実装すると下記のように記載する。
```
val adapter = ArrayAdapter<String>(this, android.R.layout.simple_spinner_item)
        adapter.setDropDownViewResource(android.R.layout.simple_spinner_dropdown_item)
        adapter.add("A型")
        adapter.add("B型")
        adapter.add("AB型")
        adapter.add("O型")
        val spinner = findViewById(R.id.spinner) as Spinner
        spinner.adapter = adapter
```
アダプターを作る際に`this`を利用しているが、これは`Activity`の場合使える。`Fragment`の場合は`requireContext()`を使用する。
```
val adapter = ArrayAdapter<String>(requireContext(), android.R.layout.simple_spinner_item)
        adapter.setDropDownViewResource(android.R.layout.simple_spinner_dropdown_item)
        adapter.add("A型")
        adapter.add("B型")
        adapter.add("AB型")
        adapter.add("O型")
        val spinner = findViewById(R.id.spinner) as Spinner
        spinner.adapter = adapter
```
Androidのリソースを利用し、プルダウンの選択肢を追加する場合は下記の場所に`arrays.xml`ファイルを作成し、利用する。
```
res > values > arrays.xml
```
```
val serviceUseCountAdapter = ArrayAdapter.createFromResource(this,
            R.array.spinner_array_items, android.R.layout.simple_spinner_dropdown_item)
        val spinner = findViewById(R.id.spinner) as Spinner
        spinner.adapter = adapter
```

## 画面遷移
### Activity

### Fragment
#### Fragment間で値を受け渡す
Fragmentaa間で値を受け渡すための方法には下記がある。
- Bundleを使う
  - 【応用】SafeArgsを使用する
- ActivityのスコープでViewModelを使用する
- navGraphViewModelsを使用する
- setFragmentResultを使用する

上記の方法の具体的方法を下記に記載していく。

##### Bundleを使用する
一番オーソドックスな方法。遷移先のFragmentを生成する際に値をargumentsとして渡す。

受け渡し側の
```Kotlin
val title = "タイトル"
// Bundleインスタンスを作成
val bundle = Bundle()
// putXXXXで値をセットする
bundle.putString("BUNDLE_KEY_TITLE", title)
// Fragmentに値をセットする
val fragment = SecondFragment()
fragment.arguments = bundle
// 遷移処理
parentFragmentManager.beginTransaction()
        .add(R.id.container, fragment)
        .commit()
```

##### ActivityのスコープでViewModelを使用する
##### navGraphViewModelsを使用する
##### setFragmentResultを使用する
