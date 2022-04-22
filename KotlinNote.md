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

# 構文
## when文
Javaでの`switch文`や`if-else文`としても使用できる。  
Javaの`switch文`はAndroidStudioでは`when文`に変換される。
```
val value = 2

when (value) {
    0 -> {// valueが0の場合の処理}
    1 -> {// valueが1の場合の処理}
    2 -> {// valueが2の場合の処理(今回はここに入る)}
    else -> {// 上記のcase文に入らなかった場合の処理}
}
```
条件を複雑にすると下記のように記載できる。  
条件式でOR/ANDを書きたい場合には、`,`と`&&`を使用する
```
val value = 2

when {
    value != null && value == 0 -> {// valueがnullではなく、0の場合の処理}
    value == 1, value == 2 -> {// valueが1か2の場合の処理}
    els
```

# 関数
## 文字列の置換(replace関数)
1. 指定した文字を置換する
```
// 書式
変数.replace("置換前の文字","置換後の文字")
```
文字列 “abc” の “b” を、大文字の “B” に置換する
```
val str = "abc"

val str1 = str.replace("b","B")
println(str1); // aBc
```
2. 指定した正規表現に該当する文字を置換する
```
// 書式
変数.replace(Regex("正規表現"),"置換後の文字")
```
文字列 “a1b2c3” の中の数値（1、2、3）を空文字に置換する
```
val str = "a1b2c3"

val str1 = str.replace(Regex("[1-3]"),"")
println(str1) // abc
```
文字列 “a1b2c3” の中の数値（1、2、3）を、壱・弐・参 に置換する
```
val str = "a1b2c3"

val str1 = str.replace(Regex("[1-3]")){
    when(it.value){
        "1" -> "壱"
        "2" -> "弐"
        "3" -> "参"
        else -> it.value
    }
}
println(str1) // a壱b弐c参
```

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

## オンラインのPDFファイルをURLからダウンロードせずに表示する
### 外部アプリを起動してPDFを表示する
```
private fun openPdfFromUrl(url: String) {
    Intent(Intent.ACTION_VIEW).apply {
        setDataAndType(Uri.parse(url), "application/pdf")
    }.also { intent ->
        openPdfFromIntent(intent)
    }
}

private fun openPdfFromIntent(intent: Intent) {
    intent.resolveActivity(packageManager)?.run {
        startActivity(intent)
    } ?: Toast.makeText(
        context,
        "No Application found to open the PDF",
        Toast.LENGTH_LONG
    ).show()
}
```
### WEBブラウザでPDFを表示する
この方法は、WEBブラウザを経由して、最終的にGoogleドライブでGoogle ドキュメントととして表示する。
```
private fun openPdfByGoogleDrive(url: String) {
    Intent(Intent.ACTION_VIEW).apply {
        data = Uri.parse("http://docs.google.com/viewer?url=$url")
    }.also { intent ->
        openPdfFromIntent(intent)
    }
}
```
### 参考サイト
- [オンラインの PDF ファイルを URL から表示する（ダウンロードせずに）｜Android Kotlin 実践勉強会](https://note.com/suinaan/n/n9aba130caf08)

# 変換

## 文字列に変換する
```
Int.toString()
```
## 文字列からの変換
| String型変換関数     | 変換後の型 | 
| ------------------ | ---------- | 
| String.toBoolean() | Boolean    | 
| String.toByte()    | Byte       | 
| String.toDouble()  | Double     | 
| String.toFloat()   | Float      | 
| String.toInt()     | Int        | 
| String.toLong()    | Long       | 
| String.toShort()   | Short      | 
| String.toChar()    | Char       | 

文字列を数値に変換できなかった場合は、NumberFormatExceptionが発生する。

## 日付文字列⇄日付
日付型を文字列に変換する`date`を`Stirng`にする。
```
val df = SimpleDateFormat("yyyy/MM/dd HH:mm:ss")
val date = Date()
println(df.format(date))
```

# 演算子
## Null合体演算子（エルビス演算子）
**概要**
Null合体演算子`?:`を使うと、変数が`null`だった時のデフォルト値を指定できる。
**サンプル**
```
var s:String? = null
println(s ?: "Default") // Default

s = "test"
println(s ?: "Default") // test
```
`null`の際に例外をスローすることもできる。
```
var s1: String? = null
println(s1 ?: throw NullPointerException())
```
`null`の際に無名関数を実行することもできる。
```
var n = 10
var s1:String? = null
var s2 = s1 ?: {
    val s = (1..n).joinToString(",")
    s  // 戻り値(return不要)
}()
println(s2) // 1,2,3,4,5,6,7,8,9,10
```
# 参考サイト
- [Kotlin の require, check, assert 関数の使い分け](https://t-keita.hatenadiary.jp/entry/2020/12/05/223942)
  - 関数の項目の下記項目の参考
    - プログラムの実行可否を判断する関数
    - "表明"という概念