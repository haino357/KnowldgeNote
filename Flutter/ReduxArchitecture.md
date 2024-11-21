# Redux Architecture
## Introduction
- 状態管理のためのアーキテクチャ
- FacebookによってReactを使用した状態管理アーキテクチャとして考案
  - Brian Egan氏が開発
  - 初版リリースは2017年08月
- アプリ全体を1つのクラスに全ての状態を集約する管理手法

## Flutterで使用するためのパッケージ
- [flutter_redux](https://pub.dev/packages/flutter_redux)

## Reduxとは
Facebookが考案した状態管理手法で以下の3つの原則に基づいている。
1. Single source of truth
   - 単一の状態管理クラス
   - アプリケーション全体の状態は1つのストアに集約される
2. State is read-only
    - 状態は読み取り専用
3. Changes are made with pure functions
   - 状態の変更は純粋関数によって行われる

アプリ全体の状態値を1つのクラスに集約し、関数によって読み取り専用のimmutableな状態を変更することで、状態管理を行う。
また、データは「単一方向に流れる」

## Reduxの構成要素
1. `Store`：アプリケーション全体の状態を保持するクラス
2. `View`：状態値を活用するUI
3. `Action`：UIからStoreへ状態値の変更を行うためのオブジェクト
4. `Reducer`：状態値の変更し、UIに反映するための関数
5. `Middleware`：ActionとReducerの間で外部API連携などの処理を行うための関数

<img alt="" src="/Flutter/picture/Reduxのフロー図.png" width="600">

### クラスやメソッド
- `Store`クラス：状態管理クラス
- `StoreProvider`クラス：Widgetツリーに沿って状態管理クラスへ依存関係を注入するクラス
- `StoreConnector`クラス：ラップしたWidgetにStoreへのアクセスを提供するクラス
- `dispatch`メソッド：ActionをStoreに送信するメソッド

## 参考サイト
- [Redux公式](https://redux.js.org/)
- [【Flutter】色んな状態管理で作ってみよう ③Redux編](https://zenn.dev/heyhey1028/articles/099573a75c1088)
- []()