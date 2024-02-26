# Bladeの構文

## 値の表示
`{{}}`はHTMLスケープ処理されるためHTMLタグとしては機能しない。
```php
{{値・変数・式・関数等}}
{{ $value }}
```
エスケープ処理してほしくない場合は以下のようにする。
```php
{{!! 値・変数・式・関数等 !!}}
{!! $value !!}
```

## @ifディレクティブ
```php
@if(条件1)
    条件1が真の場合
@elseif(条件2)
    条件2が真の場合
@else
    いずれの条件も真でない場合
@endif
```

## @unlessディレクティブ
条件が非成立の場合に処理を行う。
```php
@unless(条件)
    条件が偽の場合
@endunless
```

## @issetディレクティブ
変数がセットされている場合に処理を行う。
```php
@isset($value)
    変数がセットされている場合
@endisset
```

## @emptyディレクティブ
変数が空の場合に処理を行う。
```php
@empty($value)
    変数が空の場合
@endempty
```

## 繰り返しのディレクティブ
### @forディレクティブ
```php
@for($i = 0; $i < 10; $i++)　// (初期値: 条件: 後処置)
    {{ $i }}
@endfor
```

### @foreachディレクティブ
```php
@foreach($array as $value) // (配列 as 変数)
    {{ $value }}
@endforeach
```

### @forelseディレクティブ
```php
@forelse($array as $value) // (配列 as 変数)
    {{ $value }}
@empty
    配列が空の場合
@endforelse
```

### @whileディレクティブ
```php
@while(条件)
    条件が真の間
@endwhile
```

### $loopによるループ変数
`$loop`でループに関する情報が得られる。
| プロパティ       | 説明                                               | 
| ---------------- | -------------------------------------------------- | 
| $loop->index     | 現在のインデックス(0から開始)                      | 
| $loop->iteration | 現在の繰り返しかず(1から開始)                      | 
| $loop->remaining | 後何回繰り返すか(残り回数)                         | 
| $loop->count     | 繰り返しで使っているあ配列の要素数                 | 
| $loop->first     | 最初の繰り返しかどうか(最初ならtrue)               | 
| $loop->last      | 最後の繰り返しかどうか(最後ならtrue)               | 
| $loop->depth     | 繰り返しのネスト数                                 | 
| $loop->parent	   | ネストしている場合、親送り返しのループ変数を示す。 | 


## @includeディレクティブ
他のビューを読み込む。
```php
@include('view.name')
```

## @phpディレクティブ
PHPのコードを記述する。
```php
@php
    // PHPのコード
@endphp
```

