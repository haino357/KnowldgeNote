# JDK
## [OpenJDK](https://openjdk.java.net/)
### Mac
JDKのバージョンを確認する方法
```zsh
java -version

openjdk 17.0.13 2024-10-15
OpenJDK Runtime Environment Homebrew (build 17.0.13+0)
OpenJDK 64-Bit Server VM Homebrew (build 17.0.13+0, mixed mode, sharing)
```
インストール可能なJDKのバージョンを確認する方法
```zsh
brew search openjdk
```
パッケージ情報を確認
```zsh
brew info openjdk
```

HomebrewでOpenJDKをインストールする方法
```zsh
brew install openjdk
```
特定のバージョンをインストールする場合
```zsh
brew install openjdk@11
```
インストールされているJDKのバージョンを確認する方法
```zsh
ls /Library/Java/JavaVirtualMachines
```
パスを通す方法
zshrcに以下を追加
```zsh
export PATH="/usr/local/opt/openjdk@17/bin:$PATH"
```



macOSでインストールされているJavaのバージョンを一覧表示するコマンド
```zsh
/usr/libexec/java_home -V

atching Java Virtual Machines (1):
    17.0.13 (x86_64) "Microsoft" - "OpenJDK 17.0.13" /Library/Java/JavaVirtualMachines/microsoft-17.jdk/Contents/Home
/Library/Java/JavaVirtualMachines/microsoft-17.jdk/Contents/Home
```


## 参考サイト
- [Mac上でOpenJDKをインストール](https://zenn.dev/hayato94087/articles/c0345e6c2c53e7)
- []()