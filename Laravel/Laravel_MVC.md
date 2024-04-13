# MVC
## MVCとは
MVC(Model View Controller)は、ソフトウェア設計パターンの一つで、アプリケーションを3つの部分に分割することで、それぞれの役割を明確にすることができる。
- Model: データベースとのやり取りを担当する部分
- View: ユーザーに表示される部分
- Controller: ユーザーからの入力を受け取り、ModelとViewを制御する部分
- Router: URLリクエストを適切なコントローラーのアクションにマッピングする
- Middleware: リクエストとレスポンスの処理の間に介在し、認証やログ記録などの処理を行う
<br>
ソフトウェア開発における設計手法のひとつ。PHPは簡単で自由がゆえに、開発者ごとにコーディング規約や設計方針が異なる。そのため全体おおよそので設計手法を統一するときに使われる考え方の一つがMVCである。

<img alt="LaravelのMVCモデル図" src="/Laravel/picture/LaravelのMVCモデル図.png" width="500">

<img alt="LaravelのMVCモデル図参考" src="/Laravel/picture/LaravelのMVCモデル図参考.png" width="500">
