# Java Knowldge Note

## Class(クラス)
クラスとは、オブジェクトを表す設計図。またはあるオブジェクトの実体を生成するために定義された概念。

## Instance(インスタンス)

## Constructor(コンストラクタ)
クラスのインスタンス生成時に実行されるメソッドで、主にそのクラスのメンバ変数を初期化するときに使用する。
インスタンス生成時に呼び出される特別なメソッドで、通常のメソッドと同様に引数を指定することも可能。

### 引数の指定なし
```Java
// Constructor.java
class Constructor {
    String str = "コンストラクタサンプル";

    // コンストラクタ(インスタンス生成時に実行される)
    public Constructor() {
        System.out.println(str);
    }
}

// Main.java
public class Main {
    public static void main(String[] args) {
        // インスタンスの生成
        Constructor cont = new Constructor();
    }
}

```
### 引数の指定あり(オーバーロード)
```Java
// Constructor.java
public class Constructor {
    String str1 = "コンストラクタサンプル"

    // 引数なしのコンストラクタ
    public Constructor() {
        System.out.println(str);
    }

    // 引数ありのコンストラクタ
    public Constructor(String str2) {
        System.out.println(str1 + str2);
    }
}

// Main.java
public class Main {
    public static void main(String[] args) {
        // 引数なしのコンストラクタのインスタンスを生成
        Constructor cont1 = new Constructor();

        // 引数ありのコンストラクタのインスタンスを生成
        Constructor cont2 = new Constructor("引数あり");
    }
}
```

## オーバーロード


## オーバーライド

