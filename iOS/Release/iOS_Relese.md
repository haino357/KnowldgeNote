# iOSアプリRelease手順

## リリースアプリの準備

### リリース用の証明書を作成する

#### 1. Apple Developer Programに登録する
- 登録料は年間99米ドル
- 2ファクタ認証が有効になっているAppleID
- 個人情報
- クレジットカード情報
- D-U-N-S番号(法人のみ)
  - こちらの情報を登録が必要になる
    - D-U-N-S番号の申請後、D&Bから番号を受け取るまで最大5営業日
    - D-U-N-S番号の交付後、組織の情報がD&BからAppleに送信されるまで最大2営業日かかります。この期間が経過すると、Apple Developer Programで企業／組織として登録できるようになります。

#### 2. プロビジョニングプロファイルを作成する

#### 3. リリース用の証明書を作成する

#### 4. リリース用の証明書をダウンロードする

### リリース用の証明書を作成する

## App Store Connectにアプリを登録するワークフロー
App Store Connect は、App Store への App の提出、App の管理、TestFlight 経由での App ベータ版の配信、法的契約の承諾、税金および口座情報の入力、トレンドと財務レポートの表示などができるプラットフォーム。
最初は、Account Holder (Apple Developer Program の申請者) のみが、Apple Developer Program のメンバーシップに紐付けられている Apple ID を使用して Apple Store Connect にサインインできる。その後、Account Holder は、App Store Connect に追加のユーザを招待することができる。
1. 契約書に同意して税金と銀行口座情報を入力する。
2. ユーザを追加して役割を割り当てる
3. App を追加してビルドをアップロードする
4. App をテストして審査に提出する
5. App のステータス、使用状況、販売状況を確認する


## 公式サイト
- [Apple Developer Program](https://developer.apple.com/programs/)
- [Apple Dtore Connect](https://appstoreconnect.apple.com/)

## 参考サイト
- [iOSアプリをAppStoreで公開する手順まとめ](https://zenn.dev/moutend/articles/feebf0120dce6e6426fa)
