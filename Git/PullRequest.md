# PullRequest
## チェックリスト
- 最新ブランチから作成されているか
- ブランチ名が適切か
- 対応内容を満たしているか
- コードのレビューを行ったか
- テストを実施したか
- 一つのコミットが大きくなりすぎていないか
- パッケージの追加は独立したコミット
- 

## PullRequestTemplate
```markdown
## 目的
- 
## 関連チケット
- チケットリンク：
- デザインリンク：
- ブランチリンク：
## 変更内容
## 影響範囲
## スクリーンショット
## その他
```

## Conventional Commits
コミットメッセージのフォーマットを統一するための規約

- `fix`: バグ修正
- `feat`: 新機能の追加や変更
- `docs`: ドキュメントのみの変更
- `test`: テストコードの追加や変更
- `refactor`: リファクタリング
- `style`: コードの意味に影響を与えない変更（空白、フォーマット、セミコロンの欠落など）  インデントの変更やフォーマッターの適用など
- `perf`: パフォーマンスを向上させるコードの変更
- `ci`: CIの設定やスクリプトの変更
- `chore`: その他の変更（ビルドスクリプトの変更など）

## 参考サイト
- [レビューが爆速になる！レビュアーに優しいPull Requestの極意](https://zenn.dev/tenchijin/articles/20250206_reviewer_friendly_pull_request_secrets)
- [Conventional Commits](https://www.conventionalcommits.org/ja/v1.0.0/)
- []()