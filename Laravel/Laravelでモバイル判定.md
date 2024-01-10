# Laravelでミドルウェアでモバイルの判定する方法

## モバイル判定のアンチパターン
コントローラーにモバイル判定の処理を書くのはアンチパターン

```php
<?php
//～略～
        $agent = app('agent');
        return view('index', [
            'isMobile' => $agent->isMobile(),
        ]);
```

## ミドルウェアでモバイル判定する方法
View::share で全てのビューで使うグローバル変数を定義して、さらに、その処理をBeforeミドルウェアを使って、リクエストがきたら行う共通処理にする。

まず、composerから、モバイルのエージェントの判定ができるライブラリをインストールする。
[jenssegers/agent](https://github.com/jenssegers/agent)

エージェント判定ライブラリのインストール
```
composer require jenssegers/agent
```

config/app.phpに、エージェント判定ライブラリのサービスプロバイダーを追加する。
```php
<?php
    'providers' => [
        Jenssegers\Agent\AgentServiceProvider::class, //追加
    ],
    'aliases' => [
        'Agent' => Jenssegers\Agent\Facades\Agent::class,  //追加
    ],
``` 

Middlewareを作成する。
```
php artisan make:Middleware GetIsMobile
```

Kernel.phpにMiddleware を追加
全てのリクエストで処理をするため、$middlewareプロパティに追加します。

App\Http\Kernel.php
```php
<?php
    protected $middleware = [
        \App\Http\Middleware\CheckForMaintenanceMode::class,
～略～
        \App\Http\Middleware\GetIsMobile::class, //<-追加
    ];

```
View::shareでグローバル変数を定義する
下記を記載することで、全てのビューで$isMobile変数が使えるようになる。
App/Http/Middleware/GetIsMobile.php
```php
<?php

namespace App\Http\Middleware;

use Closure;
use Agent;
use Illuminate\Http\Request;
use Illuminate\Support\Facades\View; //View::share用

class GetIsMobile
{
    public function handle($request, Closure $next)
    {
        $agent = app('agent');
        View::share(['isMobile' => $agent->isMobile()]);

        return $next($request);
    }
}
```

## 参考
- [Laravelでミドルウェアでモバイル判定処理をして、全てのViewでisMobile変数を呼べるようにする](https://awesome-programmer.hateblo.jp/entry/2019/07/03/154221)

