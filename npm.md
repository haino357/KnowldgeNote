## npmとは
npmの正式名称は、`Node Package Manager` の略で、Node.jsのパッケージ管理ツール。
npmを使うことで、Node.jsのパッケージをインストールしたり、アップデートしたり、削除したりすることができる。


## npmのインストール
Node.jsをインストールすると、npmも一緒にインストールされる。

## npmコマンド
オプションの`-g`または `--global`は、グローバルインストールを意味する。
```zsh
// パッケージのインストール
npm install <package-name>

// グローバルインストールの場合は、root権限が必要になる
sudo npm install -g <package-name>

// パッケージのアンインストール
npm uninstall <package-name>

// グローバルインストーしたツールをアンインストール
npm uninstall -g <package-name>

// パッケージのアップデート
npm update <package-name>

// パッケージの検索
npm search <package-name>

// パッケージの情報を表示
npm info <package-name>

// インストールしたモジュールを一覧で表示する
npm ls <package-name>

// インストール済みのパッケージを一覧表示
npm list -g

// テストを実行
npm test

// npmを最新にする
npm --version
npm install -g npm
npm rebuild

// グローバルインストールされたパッケージの場所を表示
npm root -g
npm config get prefix
```


## npmのパッケージ
- [Express](https://expressjs.com/)
- [promise](https://www.npmjs.com/package/promise)
- [async](https://www.npmjs.com/package/async)
- [socket.io](https://socket.io/)