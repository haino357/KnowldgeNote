# PHP　Tips

## 文字列の結合
### 結合演算子を使用する
```php
<?php
// 文字列の結合
$greeting = 'Hello';
$name = 'World';
echo $greeting . ' ' . $name;

// 実行結果
// Hello World
```

### 結合代入演算子を使用する
```php
<?php
// 文字列の結合
$greeting = 'Hello';
$name = 'World';
$greeting .= ' ' . $name;
echo $greeting;

// 実行結果
// Hello World
```

### ダブルクォーテーションを使用する
```php
<?php
// 文字列の結合
$greeting = 'Hello';
$name = 'World';
echo "{$greeting} {$name}";

// 実行結果
// Hello World
```
