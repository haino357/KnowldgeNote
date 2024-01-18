# VSCode Notes
## 基本操作
- コマンド操作：ctrl + Shift + p
- ターミナル起動
  - ctrl + Shift + @(JISキーボードの場合)
  - ctrl + `(USキーボードの場合)

## 設定
1. 設定画面の開き方
ショートカットキーcommand + ,(Windows: Ctrl + ,)<br>
メニューバーの`Code > 基本設定 > 設定`を押下

2. `setting.josn`の開き方
開いた設定画面の右上の下記画像のアイコンをクリックする
<img src="/Picture/ScreenShot/VSCodeのsetting.jsonの開き方.png" width="400">

3. `setting.json`の変更方法
- 背景色や文字色を変更する
  - 上部ウインドウバー
  - 左部アクティビティバー
  - 下部ステータスバー
  - タブ
  - エディタの背景色
```
// 色を変える
"workbench.colorCustomizations": {
    "titleBar.activeBackground": "#0095ff", // タイトルバーの背景色を変える
    "titleBar.activeForeground": "#080606", // タイトルバーの文字色を変える
    "activityBar.activeBackground": "#ff0000", // アクティビティバーの背景色を変える
    // "activityBar.foreground": "#ff0000", // アクティビティバーの文字色を変える
    "statusBar.background": "#0000ff", // ステータスバーの背景色を変える
    // "statusBar.foreground": "#0000ff", // ステータスバーの文字色を変える
    // "activityBarBadge.background": "#ffff00", // アクティビティバーのバッチ背景色
    // "activityBarBadge.foreground": "#000000", // アクティビティバーのバッチ文字色
    // "tab.activeBackground": "#bce7d2",   // 表示されているタブの背景色
    // "tab.activeForeground": "#000000",   // 表示されているタブの文字色
    // "tab.inactiveBackground": "#000000", // 表示されていないタブの背景色
    // "tab.inactiveForeground": "#ffffff"  // 表示されていないタブの文字色
    // "editor.background": "#f8f8ff", // エディタの背景色
}
```

## VSCode拡張機能
- [Swagger Viewer](https://marketplace.visualstudio.com/items?itemName=Arjun.swagger-viewer)
- [Marp for VS Code](https://marketplace.visualstudio.com/items?itemName=marp-team.marp-vscode)
  - 公式サイト:https://marp.app/
  - スライドをMrakdownで作成できる？
- [テキスト校正くん](https://marketplace.visualstudio.com/items?itemName=ICS.japanese-proofreading)
  - [文章作成・メール作成に役立つ！VS Codeの拡張機能「テキスト校正くん」を公開](https://ics.media/entry/18859/)

## 使用中VSCode拡張機能
- [Japanese Language Pack for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=MS-CEINTL.vscode-language-pack-ja)
  - 日本語に変換する拡張機能
- [Bracket Pair Colorizer](https://marketplace.visualstudio.com/items?itemName=CoenraadS.bracket-pair-colorizer)
  - 対応する括弧をわかりやすくする拡張機能
- Angular Language Service
- Java
  - Debugger for Java
  - Extension Pack for Java
  - Project Manager for Java
  - Test Runner for Java
- Git関連
  - [GitHub Pull Requests and Issues](https://marketplace.visualstudio.com/items?itemName=GitHub.vscode-pull-request-github)
  - [Git Graph](https://marketplace.visualstudio.com/items?itemName=mhutchie.git-graph)
  - Git History
  - GitLens — Git supercharged
  - Language Support for Java(TM) by Red Hat
- Kotlin
  - Kotlin Language
- Markdown
  - Markdown All in One
  - Markdown Checkbox
  - [Markdown Preview Enhanced](https://shd101wyy.github.io/markdown-preview-enhanced/#/)
    - Markdown記法でフローチャートなどを作成する拡張機能
  - [PlantUML](https://marketplace.visualstudio.com/items?itemName=jebbs.plantuml)
    - UMLの作図をMarkdown形式で作ることができるようになる機能
- Maven
  - Maven for Java
- Paste Image
- Prettier - Code formatter
- REST Client
- Test Runner for Java
- TSLint
- Visual Studio IntelliCode
- [vscode-icons](https://marketplace.visualstudio.com/items?itemName=vscode-icons-team.vscode-icons)

### ブランチの変更
- ウインドウ左下に現在のブランチの表示があり、それをクリックすることで変更可能
  - 同様に新規ブランチの作成なども可能