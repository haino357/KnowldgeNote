# SQL

## 基本構文
### SELECT：データの取得
```sql
-- 指定のデータを取得する
SELECT column1, column2, ...
FROM table_name;

-- テーブルの全データを取得する
SELECT * FROM table_name;
```

### INSERT：データの挿入
```sql 
-- 指定のデータを挿入する
INSERT INTO table_name (column1, column2, ...)
VALUES (value1, value2, ...);
```

### UPDATE：データの更新
```sql
-- 指定のデータを更新する
UPDATE table_name SET column1 = value1, column2 = value2, ... WHERE condition;
```

### DELETE：データの削除
```sql
-- 指定のデータを削除する
DELETE FROM table_name WHERE condition;

-- テーブルの全データを削除する
DELETE FROM table_name;
```
安全に全データを削除する場合には、`SELECT`を使用して、削除対象のデータか確認する。
 

### 検索
```sql
-- AND/ORを使用して、複数の条件で検索する
SELECT column1, column2, ...
FROM table_name
WHERE condition1　AND/OR condition2;

-- 比較演算子を使用して、検索する
SELECT column1, column2, ...
FROM table_name
WHERE column1 = value1;

-- NULLを検索する
SELECT column1, column2, ...
FROM table_name
WHERE column1 IS NULL;

-- NULL以外を検索する
SELECT column1, column2, ...
FROM table_name
WHERE column1 IS NOT NULL;

-- LIKEを使用して、検索する
-- %：0文字以上の任意の文字列
-- _：任意の1文字
SELECT column1, column2, ...
FROM table_name
WHERE column1 LIKE '%pattern_';

-- BETWEENを使用して、検索する
-- 指定した範囲の値を検索する
SELECT column1, column2, ...
FROM table_name
WHERE column1 BETWEEN 100 AND 300;

-- IN/NOT INを使用して、検索する
-- 指定した値のいずれかを検索する
SELECT column1, column2, ...
FROM table_name
WHERE column1 IN (value1, value2, ...);

SELECT column1, column2, ...
FROM table_name
WHERE column1 NOT IN (value1, value2, ...);
```


