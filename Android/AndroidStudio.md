# AndroidStudio

## ショートカットキー
### Maca版
- コードの整形：command + option + L
- 検索機能：shift2回押し
- 真下にコピー：command + D

### Windows
- コードの整形：Ctrl + Alt + L
- 検索機能：shift2回押し
- 真下にコピー：Ctrl + D

## エミュレーター
### エラー対応
#### INSTALL_FAILED_INSUFFICIENT_STORAGE
**事象**
エミュレーターに対してアプリのインストールに失敗した時に表示される。
**原因**
エミュレーターの内部ストレージ(`/data配下`)がいっぱいになっている際に発生。
**解決策**
エミュレータを再度作り直すことで対応できる。この時にストレージサイズを調整する。

#### emulator: ERROR: Running multiple emulators with the same AVD is an experimental feature. Please use -read-only flag to enable this feature.
**事象**
エミュレータが開いている状態になっている。そのために新たにエミュレータを作ることができない。
**原因**
`/Users/ユーザー名/.android/avd/端末名.avd`の中にある下記3つファイルが原因
```
cache.img
hardware-qemu.ini.lock 
multiinstance.lock  
```
**解決策**
`/Users/ユーザー名/.android/avd/端末名.avd`の中にある下記3つファイルを削除する
```
cache.img
hardware-qemu.ini.lock 
multiinstance.lock  
```

### M1 Macでのタイムアウト対応
- 現象：エミュレータの起動は問題ないが、アプリを走らせようとすると実行できずにタイムアウトしてしまう。
- 対応策
  - 現状理由も対応策もなし

## キャッシュ削除の方法
`File ＞Invalidate Caches/Restart` ： キャッシュを削除して再起動

## APKの作り方
`Build > Generate Signed Bundle or APK`と実行すると下記ウインドウが開く。
<img src="/Picture/ScreenShot/Generate%20Signed%20Bundle%20or%20APK.png" width="600">
APKを選択し、Nextを押下すると下記画面に遷移する。
<img src="/Picture/ScreenShot/Generate%20Signed%20Bundle%20or%20APK2.png" width="600">
`Key store path`がない場合は上記画像の赤枠部分`Create new...`を謳歌すると下記画像が出てくる。
<img src="/Picture/ScreenShot/New%20Key%20Store.png" width="600">
<img src="/Picture/ScreenShot/keystorepath.jpeg" width="600">
上記をクリックして、Key.jksの保存先を決定する。
<img src="/Picture/ScreenShot/keystorepath02.jpeg" width="600">

`Key.jks`を保存後、以下に記載する項目を設定する。
- Password & Confirm：キーストアのパスワード。署名設定時に必要。6文字以上必要。
- Alias：キーを識別する任意の名前。画像はデフォルト
- KeyのなかのPassword & Confirm：キーのパスワード。署名設定時に必要
- Certificate：証明書の所有者に関する情報。どれか一つは入力が必要。6文字以上必要

<img src="/Picture/ScreenShot/Generate APK.png" width="600">

上記画像の赤枠部分を入力後 `Next` ボタンを押下し、下記の画面へ遷移する。

<img src="/Picture/ScreenShot/Generate APK02.png" width="600">

上記画像から、APKの状態を選択し、`Finish`ボタンを押下し、完了。

## Scratchファイル
　Kotlinなどの実行可能なコードを保存するファイルで、デフォルトではプロジェクト外に保存されます。 プロジェクト内にあるファイルと違う点は、あらかじめプロジェクトをビルドしておけば、Scratchファイルのビルドだけで実行可能なため、実行までの時間が速いこと。
　これは、IntelliJのIDE機能の一つ。

**Scratchファイルの作成**

<img src="/Picture/ScreenShot/Scratchファイルを作成.png" width="600">

**コード記載と実行のイメージ**

<img src="/Picture/ScreenShot/Scratchファイルを実行.png" width="600">

## ローカルリポジトリの作成
AndroidStudioの上部メニューの`VCS` > `Enable Version Control Integration...` を選択する。
画面がひょうじされるので、`Git`を選択し、OKボタンを押下する。