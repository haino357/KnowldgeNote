# Laravel Debug

## ログの保存設定
1. config/app.php に以下を追加する
```php
/*
	|--------------------------------------------------------------------------
	| Logging Configuration
	|--------------------------------------------------------------------------
	|
	| Here you may configure the log settings for your application. Out of
	| the box, Laravel uses the Monolog PHP logging library. This gives
	| you a variety of powerful log handlers / formatters to utilize.
	|
	| Available Settings: "single", "daily", "syslog", "errorlog"
	|
	*/
    'log' => env('APP_LOG', 'single'),
```
daily：
・ログをファイル出力する時に日別で出力する。
・dailyの記述は、config/logging.php に書かれている。
・ログは、 storage/log/laravel-YYYY-MM-DD.log に出力する。


2. .env に以下を追加する
```env
#LOG_CHANNEL=stack    //これをコメントアウトする。
LOG_CHANNEL=daily
```
※LOG_CHANNEL=dailyを記述しないと、ログが日別でファイル出力されない。

## ログの出力
〇〇.phpにログを出力するコードを記載する。
```php
// ログの出力
Log::debug($request);
Log::debug('デバッグログ');
Log::info('インフォログ');
Log::notice('ノーティスログ');
Log::warning('ワーニングログ');
Log::error('エラーログ');
Log::critical('クリティカルログ');
Log::alert('アラートログ');
Log::emergency('緊急ログ');
```
`storage/log/laravel-YYYY-MM-DD.log`を確認する。