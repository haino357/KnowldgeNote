# アプリケーションID
- すべてのAndroidアプリには、「com.example.myapp」など、Javaパッケージ名に似た一意のアプリケーションIDがある。
- このIDによってアプリがデバイスとGoogle Playストアで一意に識別される。
- アプリの新しいバージョンをアップロードする場合、アプリケーションIDおよび署名に使用する証明書は元のアーティファクトと一致しなければならない。
- アプリケーションIDを変更すると、Google Playストアで全く別の新しいアプリとして扱われる。よってアプリを公開したら、**絶対にアプリケーションIDを変更してはならない**。
<br>
アプリケーションIDは、アプリの`build.gradle`ファイルの`applicationId`プロパティで定義される。
```gradle
android {
    defaultConfig {
        applicationId "com.example.myapp"
        minSdkVersion 15
        targetSdkVersion 28
        versionCode 1
        versionName "1.0"
    }
    ...
}
```

- Android Studioで新しいプロジェクトを作成すると、`build.gradle`ファイルには、`applicationId`プロパティの値として、`com.example.myapp`が自動的に設定される。
  - 上記は新規プロジェクト作成時に設定されるデフォルトのアプリケーションIDである。
  - よって、初期に変更可能。
- アプリケーションIDとパッケージ名(コード名前空間)がある。
  - 新規でプロジェクト作成時は、アプリケーションIDとパッケージ名は同じになる。
  - アプリケーションIDとパッケージ名は同一である必要はない。
  - ただし、アプリケーションIDは、アプリ公開後に変更すると別アプリ扱いになるため、変更してはならない。
- アプリケーションIDの命名規則
  - 2つ以上のセグメント(1つ以上のドット)に分割される必要がある。
  - 各セグメントは文字で始まる必要がある。
  - 使用できる文字は英数字とアンダースコアのみ。（a～z、A～Z、0～9、_）
- [アプリへの署名](https://developer.android.com/studio/publish/app-signing?hl=ja)


## ビルドバリアント向けにアプリケーションIDを変更する
- アプリのAPKまたはAABをビルドすると、ビルドツールは`build.gradle`ファイルの`defaultConfig`ブロックの`applicationId`プロパティの値を使用して、アプリケーションIDを決定する。
- ただし、アプリのさまざまなバージョン（無料版の「free」やプロフェッショナル版の「pro」など）を作成し、Google Play ストアで別々の掲載情報として表示したい場合は、アプリケーションIDがそれぞれ異なるビルドバリアントを定義する必要がある。
- この場合、ビルドバリアントはそれぞれ別のプロダクトフレーバーとして定義する必要がある。
  - `productFlavors`ブロック内のフレーバーごとに、`applicationId`プロパティを再定義するか、`applicationIdSuffix`を使用してデフォルトのアプリケーションIDの末尾にセグメントを付加することができる。
  - 下記の例によりfree」プロダクト フレーバーのアプリケーション ID は「com.example.myapp.free」となる。

```gradle
android {
    ...
    defaultConfig {
        applicationId "com.example.myapp"
        minSdkVersion 15
        targetSdkVersion 28
        versionCode 1
        versionName "1.0"
    }

    productFlavors {
        free {
            applicationIdSuffix ".free"
        }
        pro {
            applicationIdSuffix ".pro"
        }
    }
}
```

- Gradleではプロダクトフレーバーの後にビルドタイプの設定を適用するため、「free debug」ビルドバリアンとのアプリケーションIDは「com.example.myapp.free.debug」となる。2つのアプリで同じアプリケーションIDを使用することができないため。この方法でデバッグビルドとリリースビルドの両方を同じデバイスに組み込みたい場合に便利。
- [ビルド バリアントを設定する](https://developer.android.com/studio/build/build-variants?hl=ja)

## テスト用にアプリケーションIDを変更する
- デフォルトでは、ビルドツールは指定されたビルドバリアントのアプリケーションIDの末尾に`.test`を付加したものを使用して、[インストルメンテーションテスト](https://developer.android.com/training/testing/unit-testing/instrumented-unit-tests?hl=ja)用のAPKにアプリケーションIDを適用する。
- たとえば、`com.example.myapp.free`ビルドバリアントのテストAPKでは、アプリケーションIDは`com.example.myapp.free.test`となる。
- 必須ではないが、`defaultConfig`または`productFlavor`ブロックで `testApplicationId`プロパティを定義することにより、アプリケーションIDを変更できる。

## パッケージ名を変更する
- プロジェクトのパッケージ名は、デフォルトでアプリケーションIDと同じになる。
- 変更する場合は、下記二点で一致する必要がある。
  - `AndroidManifest.xml`ファイルの`package`属性
  - プロジェクトのディレクトリ構造で定義されているパッケージ名

```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.example.myapp"
    android:versionCode="1"
    android:versionName="1.0" >
```

- Androidビルドツールは、次の2つの目的で`package`属性を使用する。
  - アプリの生成された`R.java`クラスの名前空間として使用する。
    - たとえば、上記のマニフェストでは、`R`クラスは`com.example.myapp.R`という名前空間になる。
  - マニフェストファイルで宣言されたすべての相対クラス名を解決する。
    - たとえば、上記のマニフェストでは、`<activity android:name=".MainActivity">`として宣言されたアクティビティは`com.example.myapp.MainActivity`に解決される。

## 参考サイト
- [アプリケーション ID を設定する](https://developer.android.com/studio/build/application-id?hl=ja)