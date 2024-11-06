## Gatekeeperとは
macOSのゲートキーパー（Gatekeeper）は、信頼できないアプリケーションの実行を防ぐセキュリティ機能

## Gatekeeper機能のOn/Offを切り替えるコマンド
```zsh
sudo spctl --master-enable  # Gatekeeperを有効にする
sudo spctl --master-disable # Gatekeeperを無効にする
```
GUIで設定する場合は、システム環境設定 > セキュリティとプライバシー > 一般 から設定可能

## Gatekeeperの設定を確認するコマンド
```zsh
spctl --status  # Gatekeeperの状態を確認する
```

## 特定のアプリケーションをGatekeeperで許可する
```zsh
sudo spctl --add /path/to/application.app  # 特定のアプリケーションをGatekeeperで許可する
```

## Gatekeeperで許可したアプリケーションを削除する
```zsh
sudo spctl --remove /path/to/application.app  # Gatekeeperで許可したアプリケーションを削除する
```

## Gatekeeperで許可したアプリケーションの一覧を表示する
```zsh
spctl --list  # Gatekeeperで許可したアプリケーションの一覧を表示する
```