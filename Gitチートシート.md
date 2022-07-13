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

## コミットを元に戻す方法
### ローカルリポジトリの場合は下記のみでOK
```
git reset --hard HEAD^
```
- `--hard`：コミット取り消した上でワークディレクトリの内容も書き換えたい場合に使用。
- `--soft`：ワークディレクトリの内容はそのままでコミットだけを取り消したい場合に使用。
  - 細かくローカルcommitをしているとこのコマンドは多用するようになる。
- `HEAD^`：直前のコミットを意味する。
- `HEAD~{n}` ：n個前のコミットを意味する。
  - `HEAD^`や`HEAD~{n}`の代わりにコミットのハッシュ値を書いても良い。
  - gitのv1.8.5からは、`HEAD`のエイリアスとして`＠`が用意されている。
    - `HEAD~`と`HEAD^`と`@^`は同じ意味。
    - `HEAD^^^`と`HEAD~3`と`HEAD~~~`と`HEAD~{3}`と`@^^^`は同じ意味。

## コミットログを残して上書きする方法
作業ツリーを指定したコミット時点の状態にまで戻し、コミットを行う（コミットをなかったことにはせず、逆向きのコミットをすることで履歴を残す）ためには下記コマンドを叩く。
```
git revert コミットのハッシュ値
```

## コミットの上書きする方法
直前のコミットに上書きするには、下記コマンドを叩く。
```
git commit --amend -m "コミットメッセージ"
```
- コミットメッセージを変更したい時よく使う。
- 「git rebase失敗した時、コンフリクトを避けるためにコミットを上書きする」という使い方もよくする。

## commitせずに変更を待避する【git stash】
　あるブランチで作業中に、別ブランチですぐに変更したい内容があった場合、現在の作業をコミットすることなく待避させる。
**作業を待避する**
```
$ git stash -u
```
　コミットしていない変更がある状態で上記のコマンドを実行すると、変更した部分が退避され、ワーキングディレクトリ上は差分がない状態になる。
　「コミットしていない変更」とは、addしたものもaddしていないものもどちらも含まれる。
　`-u`は`--include-untracked`の略。新規作成ファイル(追跡対象に含まれていないファイル)も退避することができる。

**退避した作業の一覧を見る**
```
$ git stash list
stash@{0}: WIP on test: xxxx
stash@{1}: WIP on commit-sample: xxxx
```
- `stash@{n}`から始まる1行が1回分の`stash`になる。
- `WIP on`のあとはブランチ名。
- `xxxx`は`stash`をしたときのHEADのコミットハッシュとコミットメッセージになる。

**退避した作業を戻す**
```
$ git stash apply stash@{0}
```
- `stash@{0}`の作業をもとに戻す。
- 上記コマンドでは指定しているブランチにスタッシュした作業が戻る。
- スタッシュ名を指定しない場合は直近のスタッシュが戻る。
- 上記コマンドでは`add`していたものも`add`する前の状態で戻る。`add`した状態で戻す場合は下記コマンドを使用する。
```
$ git stash apply stash@{0} --index
```

**待避した作業を戻して消す**
```
$ git stash pop stash@{1}
```

**退避した作業を消す**
- stashを使用して退避した作業を元に戻しても、退避した情報は残ったまま。
- `git stash list`を実行すると、退避した情報はそのまま残っている.そのため、退避した作業を消すには、以下のコマンドを使用する。
```
$ git stash drop stash@{0}
```

**作業を退避するときにメッセージを付ける**
```
$ git stash save "stash message"

$ git stash list
stash@{0}: On test: stash message
```

**退避した変更の詳細をみる**
```
$ git stash show stash@{0}
```
上記コマンドより、変更ファイルの一覧を見ることができる。
また、-pオプションをつけることで、変更内容の詳細をみることもできる。
```
$ git stash show stash@{0} -p
```

**addした変更以外を退避させる**
オプションを何もつけない場合、addした変更もaddしていない変更も退避される(新規追加ファイルは例外)。`-k(もしくは--keep-index)`をつけて実行すると、addした変更は退避されません。
```
$ git stash -k
```

**退避した作業をすべて消す**
```
$ git stash clear
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

## GitHubのリポジトリの種類変更
1. 変更したいリポジトリ画面を開きSettingボタンを押下する
   1. <img src="Picture/ScreenShot/GitHub%20repositoryの種類変更①.png" width="600">
2. `Danger Zone`の`Change repository visibility`のボタンを押下する
   1. <img src="Picture/ScreenShot/GitHub%20repositoryの種類変更②.png" width="600">
3. 変更したい種類に変更し、リポジトリの名前を記入し決定する
   1. <img src="Picture/ScreenShot/GitHub%20repositoryの種類変更③.png" width="600">

## branch削除
```
git branch -d ブランチ名
git branch --delete ブランチ名
```
- このコマンドではマージ済のブランチを削除できる
  - マージされていなかったり作業中のブランチを削除しようとするとエラーが発生する
  - 下記がエラーメッセージ
```
# 作業中
error: Cannot delete branch '削除するブランチ名' checked out at '作業フォルダパス'
# マージされていない
error: Cannot delete the branch 'ブランチ名' which you are currently on
```
- 作業中のブランチを削除する場合は下記コマンドを使用することでどんなローカルブランチも削除できる
```
git branch -D ブランチ名
```
- 削除したいブランチを選択していると削除できない


## Merge
branchAにbrunchBをmergeする場合のコマンド
branchAを選択した状態で下記コマンドを実行する
```
git merge branchB
```
<img src="Picture/git-merge.png" width="600">

## パスワード求められたが、パスワードでは対応できない場合
### Mac
1. ターミナルでパスワードを求められる操作を行うと下記のようにパスワードを求められる。ここでコロン以下にGitHubのTokenを入力する。
```
Password for 'https://mht-takayuki-shoji@github.com': Tokenを入力
```

## ブランチ名の変更
```
git branch -m <古いブランチ名> <新しいブランチ名>
```
選択しているブランチの名前を変更する場合
```
git branch -m 新しいブランチ名
```

## Git LFS (Large File Storage)
Gitは大きなファイルやバイナリファイルを扱うのが苦手なので、欠点を補うためにGitHubが開発したのがGit LFS(Large File Storage)という拡張機能。

### インストールとセットアップ
今回の対応ではMacを使用する前提で記載する。
**インストール**
まずはGit LFSクライアントをインストールする。Git LFSはあくまで Gitの拡張機能という位置づけになっている。そのため、利用するにはまず拡張機能を含むソフトウェアを入れる必要がある。

macOS であれば Homebrew を使って`git-lfs`をインストールする。
```
$ brew install git-lfs
```
Git LFSのバージョン確認
```
$ git lfs version

// 実行結果
git-lfs/3.1.2 (GitHub; darwin amd64; go 1.17.6)
```
下記コマンドを実行して Git LFS クライアントの初期設定をする。
```
$ git lfs install

// 実行結果
Git LFS initialized.
```
下記コマンドを実行すると Git クライアントの設定ファイルである `~/.gitconfig`にGit LFS用の設定が入る。
```
$ grep -A 4 lfs ~/.gitconfig

// 実行結果
[filter "lfs"]
	clean = git-lfs clean -- %f
	smudge = git-lfs smudge -- %f
	process = git-lfs filter-process
	required = true
```