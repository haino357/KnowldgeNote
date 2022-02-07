# INBOX
* [ ] split 文字列を分割:https://itsakura.com/kotlin-split
* [ ] spinner
  * [ ] 中身のアイテムの作り方をまとめる
* [ ] ViewPager2
* [ ] [選択ツール](https://developer.android.com/guide/topics/ui/controls/pickers?hl=ja)
* [ ] webviewの使い方
* [ ] base64

# companion object
## companion object参考URL
- [Kotlinのcompanion objectとは](https://qiita.com/tkhs0604/items/261e94a42b7097dfd204)

# シールドクラス(Sealed Class)
## シールドクラス参考URL
- [Kotlin-シールドクラス](https://blog.y-yuki.net/entry/2019/05/24/090000)

# 内部クラス
## 内部クラス参考URL 
- [Kotlin内部クラスを理解する](https://qiita.com/kaleidot725/items/f2c6611648b04f7f41db)

# 関数
## プログラムの実行可否を判断する関数
Kotlinには、引数のBoolean型でプログラムの実行を判断する関数がある。
- require
- check
- assert

### require関数
表明が満たされない場合は`IllegalArgumentException`が発生する。この例外は関数の引数が不正であることを示す。  
require 関数は、関数の引数に対する表明として用いるのが適切である。  
require 関数の使用例は以下の通り。関数の引数である変数 count に対する表明を定義している。
```
fun getIndices(count: Int): List<Int> {
    require(count >= 0) { "Count must be non-negative, was $count" }
    // ...
    return List(count) { it + 1 }
}
```
ソースコードの引用元： [require - Kotlin Programming Language](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/require.html)  
  
ちなみにエラーメッセージ `{ "Count must be non-negative, was $count" }` の部分はなくてもよい。その場合は`IllegalArgumentException`のデフォルトのメッセージが設定される。独自のエラーメッセージを表示させることにより、どこがエラーなのかわかりやすくする。

念のため説明しておくと`{ "Count must be non-negative, was $count" }` というのは
`fun require(value: Boolean, lazyMessage: () -> Any)` の第二引数`lazyMessage`に対応している。Kotlinでは最後の引数が関数であるとき、中括弧 `{ }` でくくったラムダ式を引数の外に出せる。  
つまり、上記のソースコード中の  
```
require(count >= 0) { "Count must be non-negative, was $count" }
```
は下記と同じ意味である。
```
require(count >= 0, { "Count must be non-negative, was $count" })
```
### check関数
表明が満たされない場合`IllegalStateException `が発生する。この例外は、リクエストされた処理を実行するために適切な状態になっていないことを示す。  
関数の引数のチェックは`require関数`を用いるとして、それ以外のチェックを`check関数`で行うような使い方になる。  
check 関数の使用例は以下の通り。引数でない変数 state に対する表明を定義している。
```
var someState: String? = null
fun getStateValue(): String {
    val state = checkNotNull(someState) { "State must be set beforehand" }
    check(state.isNotEmpty()) { "State must be non-empty" }
    // ...
    return state
}
```
ソースコードの引用元： [check - Kotlin Programming Language](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/check.html)
### assert関数
プログラムの実行時の VM 引数として -ea (-enableassertions) を与えたときのみ有効になる。Java の assert キーワードと同様に、表明が満たされない場合は AssertionError を発生させる。Java の assert と同じ立場を取るなら、どんな種類の表明に用いてもよいと言える。  
  
ドキュメント：[assert - Kotlin Programming Language](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/assert.html)
  
ソースコードの例としては、上記のソースコードの require 関数や check 関数を assert 関数に置換したものを考えればよい。

### まとめ
| 関数    | 用途                                                                            | 
| ------- | ------------------------------------------------------------------------------- | 
| require | 関数の引数のチェックに使う。                                                    | 
| check   | 関数の引数以外のチェックに使う。                                                | 
| assert  | どこに使ってもよい。<br>実行時の VM 引数として -ea (-enableassertions) が必要。 | 
## "表明"という概念
プログラミングの重要な概念に「表明(assertion)」という考え方がある。表明とは、プログラムの実行時に変数が満たすべき条件をコードとして表現すること。例として、「変数`i`が負でない」などのように常に満たすべき条件をプログラムの一部として書く。この条件が満たせない場合はエラーとして実行が中止されため、以降の処理を安心して書くことができる。  
デバッグの用途のために使用すると、バグの原因の切り分けが容易になる。また、ソースコード中に暗黙の前提を残さないために、処理の節目には表明を入れるとよい。


## ダブルクォーテーションをエスケープする方法
```
val json = "\"Hello, world!!!\""
println(json)
```

# 参考サイト
- [Kotlin の require, check, assert 関数の使い分け](https://t-keita.hatenadiary.jp/entry/2020/12/05/223942)
  - 関数の項目の下記項目の参考
    - プログラムの実行可否を判断する関数
    - "表明"という概念