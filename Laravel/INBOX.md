# INBOX
Laravelのメモを書き留める。必要に応じて他のファイルに移動する。

## array_key_exists()
配列のキーが存在するかどうか調べるにはarray_key_exists()を使う。
```php
bool array_key_exists(キー, 配列)
```
この関数は指定したキーが配列内に存在している場合はTRUEを返し、存在しない場合はFALSEを返す。

```php
<?php
$array = ['key' => 'value'];
if (array_key_exists('key', $array)) {
    echo 'キーが存在します';
}
?>
```

## isset()
変数がセットされているかどうか調べるにはisset()を使う。
```php
bool isset(変数)
```
配列にキーが存在している場合はTRUE、存在しない場合はFALSEを返す。ただし、指定したキーの要素がNULLの場合はFLASEを返すので注意が必要。

```php
<?php
$value = 'value';
if (isset($value)) {
    echo '変数がセットされています';
}
?>
```
