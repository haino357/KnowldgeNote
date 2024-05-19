## モジュール分割

レイヤードアーキテクチャでモジュールを分割する場合、以下のような構成になる。
```
packages
├── app
│   ├── assets
│   └── lib
│       ├── component
│       ├── page
│       ├── route
│       ├── theme
│       └── main.dart
├── domain
│   └── lib
│       ├── src
│       │   └── usecase
│       ├── domain.dart
│       └── usecase.dart
├── data
│   └── lib
│       ├── src
│       │   ├── internal
│       │   │   ├── api
│       │   │   ├── json
│       │   │   └── proto
│       │   ├── model
│       │   └── repository
│       ├── data.dart
│       ├── model.dart
│       └── repository.dart
└── foundation
    └── lib
        ├── src
        │   ├── environment
        │   └── extension
        ├── environment.dart
        ├── extension.dart
        └── foundation.dart
```

## 参照サイト
- [エンジニアの認知負荷を下げるためにFlutterのプロジェクト構成で考えたこと](https://developers.cyberagent.co.jp/blog/archives/47783/)