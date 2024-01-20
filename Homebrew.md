# Homebrew
## インストール
下記コマンドを実行する。
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

## 用語
### formula
Homebrewでインストールするパッケージのこと
### keg
formulaのインストール先のこと
### Cellar
インストールしたformulaの実体は `/usr/local/Cellar` に格納される。
`/usr/local/bin`や`/usr/local/lib`には、`/usr/local/Cellar`に格納されたformulaのシンボリックリンクが作成される。

### cask
Homebrewでインストールするアプリケーションのこと
### tap
Homebrewでインストールするformulaやcaskのリポジトリのこと



## コマンド
### インストール済みのformulaを一覧表示する
```
brew list
```
### formulaをインストールする
```
brew install formula名
```
### formulaをアンインストールする
```
brew uninstall formula名
```
### formulaをアップデートする
```
brew upgrade formula名
```
### formulaを検索する
```
brew search formula名
```
### formulaの情報を表示する
```
brew info formula名
```
### formulaの依存関係を表示する
```
brew deps formula名
// インストールされているformulaの依存関係ツリー表示する
brew deps --tree formula名
// インストールされているformulaの依存関係を逆順に表示する
brew deps --installed --reverse formula名
// インストールされている特定のformulaの依存関係を表示する
brew deps --installed formula名
```
### 更新可能なformulaの表示する
```
brew outdated
```
### formulaのバージョンを切り替える
```
brew switch formula名 バージョン
```
### formulaのバージョンを表示する
```
brew versions formula名
```
### formulaのバージョンを古い順に表示する
```
brew versions --desc formula名
```
### formulaのバージョンを最新にする
```
brew pin formula名
```
### formulaのバージョンを固定する
```
brew unpin formula名
```
### formulaのバージョンを固定を解除する
```
brew tap formula名
```
### formulaのリポジトリを追加する
```
brew untap formula名
```
### システムチェック
```
brew doctor
```
### キャッシュを削除する
formula や cask のキャッシュを削除する。
また、インストールされているformulaの古いバージョンを削除する。
デフォルトでは120日以上前のダウンロードをすべて削除する。
この期間は `HOMEBREW_CLEANUP_MAX_AGE_DAYS` で変更できる。
```
brew cleanup
// 指定のformulaのキャッシュを削除する
brew cleanup formula名
```
### autoremove
インストールされているformulaの依存関係にないformulaを削除する。
HOMEBREW_AUTOREMOVEを設定するとbrew cleanup, brew uninstall を実行した際にbrew autoremoveが自動実行される。
ただしHOMEBREW_NO_INSTALL_CLEANUP が設定されている場合にはbrew cleanupが定期実行されないため自動実行されない。
```
brew autoremove
```



## 公式サイト
- [Homebrew](https://brew.sh/ja/)
- [GitHub](https://github.com/Homebrew)
  - 
