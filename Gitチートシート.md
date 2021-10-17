# Gitチートシート
## Gitのユーザー名とメールアドレスを確認・登録する
### 確認コマンド
```
git config user.name  // ユーザー名
git config user.email  // メールアドレス
```
### 登録コマンド
```
git config --global user.name "Your Name"
git config --global user.email "email@～"
```

## 直前のコミットを取り消す方法
### ローカルリポジトリの場合は下記のみでOK
```
git reset --hard HEAD^
```
### リモートリポジトリにプッシュ済みの場合は上記でローカルを削除したのち下記を実行する。
```
// 強制的にPushする
git push -f origin master
```

## Git管理下でファイル名の変更する方法：git mvコマンド
```
git mv 変更前ファイル名 変更後ファイル名
```
ファイル名を直接変更した場合は別ファイル扱いになってしまう。だから、ファイル名の変更をGitの差分と認識させるためには上記のコマンドを使用する。