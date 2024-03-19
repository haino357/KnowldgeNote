## Apple Developer Program
- [Apple Developer Program](https://developer.apple.com/programs/)

## 更新項目
### Apple Developer Program Membership
Appleの開発者プログラムに参加するための有料メンバーシップ。有効期限は1年間で有効期限が切れると、開発者プログラムへのアクセスや証明書の更新ができなくなる。また、アプリはダウンロードできなくなり、すでにインストールまたはダウンロードしたユーザーも、そのアプリを使用できなくなる。

####　 更新方法
1. developer.apple.comにログインし、Accountをクリック
2. Membershipのタブを選択し、更新するアカウントを選択
3. Renew Membershipをクリックし、支払い情報を更新
4. 支払い情報を更新し、更新内容を確認してからRenewをクリック
5. アカウントが更新されると、新しい期間が表示される

### Development/Production Certificate
開発や配信に使用する証明書で、1年間の有効期限がある。有効期限がきれると、アプリのビルドや配信に影響が出る。更新日前には確実に更新が必要。よって、更新日の確認を実施する。

####　 更新方法
1. Apple Developer Accountにログイン
2. 左側のメニューから「Certificates, IDs & Profiles」を選択
3. 「Certificates」をクリックし、更新する証明書を選択
4. 「Edit」ボタンをクリックし、新しい証明書をアップロード
5. 証明書が更新されたことを確認し、必要に応じてProvisioning Profileを更新
6. Xcodeで、新しいProvisioning Profileをダウンロードして、プロジェクトに適用

### Provisioning Profile
開発や配信洋に必要なプロファイルで、1年間の有効期限がある。有効期限がきれると、アプリのビルドや配信に影響が出る。更新日前には確実に更新が必要。よって、更新日の確認を実施する。

####　 更新方法1
1. Xcodeを開く
2. 左上の「Xcode」をクリックして、「Preferences」を選択
3. 「Accounts」タブをクリックし、Provisioning Profilesの一覧から更新したいプロファイルを選択
4. 右下の「Refresh」ボタンをクリック
5. 更新されたプロファイルがリストに表示されたら、必要なものを選択して「Download」ボタンをクリック
6. ダウンロードが完了したら、Xcodeが自動的に更新される

####　 更新方法2
1. Apple Developerサイトにログイン
2. 左側のメニューから「Certificates, IDs & Profiles」を選択
3. 「Provisioning Profiles」をクリックし、更新したいプロファイルを選択
4. 「Edit」ボタンをクリックして、プロファイルを更新
5. 変更を保存し、プロファイルをダウンロード
6. ダウンロードしたファイルをXcodeにドラッグ＆ドロップして、Provisioning Profileを更新


### Push Notification Certificate
プッシュ通知に使用する証明書で、1年間の有効期限がある。有効期限がきれると、プッシュ通知ができなくなる。更新日前には確実に更新が必要。よって、更新日の確認を実施する。

####　 更新方法
1. Apple Developer Centerにログインし、Certificates, Identifiers & Profilesのページにアクセス
2. 既存のPush Notification Certificateの一覧が表示されますので、更新したい証明書を選択し、「Edit」をクリック
3. 有効期限の切れたPush Notification Certificateを更新する場合は、「Reset」をクリックして新しい証明書を生成
4. 証明書を再発行する場合は、「Revoke」をクリックして古い証明書を取り消し、新しい証明書を生成
5. 新しいPush Notification Certificateを生成すると、証明書ファイルが自動的にダウンロードされる
6. ファイルを開いて、Xcodeにインポートすることで、アプリケーションのPush通知を更新できる

### 参考サイト
- [Apple Developerが忘れがちな4つの更新項目](https://qiita.com/sauna1137/items/320c35e9b4e50d19d915)


## Warningと対応
1. SDK version issue
日付：2024/3/14(木)
```
SDK version issue. This app was built with the iOS 16.4 SDK. Starting April 29, 2024, all iOS and iPadOS apps must be built with the iOS 17 SDK or later, included in Xcode 15 or later, in order to be uploaded to App Store Connect or submitted for distribution.

SDKのバージョンの問題。 このアプリは iOS 16.4 SDK を使用して構築されました。 2024 年 4 月 29 日以降、すべての iOS アプリと iPadOS アプリは、App Store Connect にアップロードしたり配布用に送信したりするには、Xcode 15 以降に含まれる iOS 17 SDK 以降を使用して構築する必要があります。
```
**対処法**
- 2024/3/14(木)までに、iOS 17 SDK 以降を使用してアプリをビルドする必要がある
- 対応方法：Xcode 15 以降を使用してアプリをビルドする