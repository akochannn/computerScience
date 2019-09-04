---
description: SQLについて
---

# SQL

## 文法

### 実行順序

SQLの実行順序は以下の通り

```text
FROM → WHERE → GROUP BY → HAVING → SELECT
```

### 句

- `null`は値でないので条件文で`<value> = null`と書くことができません.代わりに`<value> is null`と書きます

### GROUP BY

`GROUP BY`は同じ名前の列を集約します

集約されたデータの他の列の値は合計されます

```text
GROUP BY <column>
```

#### 例

|name|color|sales|
|-|-|-|
|bag|black|4500|
|bag|red|5100|
|wallet|white|3800|
|bag|black|4600|
|wallet|black|3900|

に対して

```text
SELECT name, sum(sales)
FROM report
GROUP BY name
```

を実行すると

|name|sum(sales)|
|-|-|
|bag|14200|
|wallet|7700|

となります

### ORDER BY

`ORBER BY`は抽出したデータの並べ替えをします

`DESC`をつけると降順,`ASC`をつけると昇順です(`ASC`がデフォルト値です)

```text
ORDER BY <column> (DESC|ASC)*
```

### CAST

`CAST`はデータ型を変換します

```text
CAST (<value> AS <data_type>)
```

### SELECT

`SELECT`はテーブルから列を抽出するのに使います

```text
SELECT <column>
```

### WITH

`SELECT`の前にサブクエリを作ります

```text
WITH <sub_query> AS (...<processing the sub_query>)
```

### INNER JOIN

`INNER JOIN`はそれぞれのテーブルの指定した列の値が条件を満たすものだけを統合します

```text
SELECT <column1> <column2> FROM <table1>
    INNER JOIN <table2> ON <condition>
```

### OUTER JOIN

`OUTER JOIN`は`INNER JOIN`に加えて,片方のテーブルにしかないものも取得します

`LEFT`と`RIGHT`はどちらのテーブルを軸にするかです

例えば,`LEFT`の場合,`LEFT`のテーブルにしかない値も取得し,`RIGHT`の列が入る部分は`null`で補完されます

```text
SELECT <column1> <column2> FROM <table1>
    (LEFT|RIGHT) OUTER JOIN table2 ON <condition>
```
