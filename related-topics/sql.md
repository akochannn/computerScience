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

- 変数は型と値を持っています
  - 宣言の仕方は次のようにします.`DECLARE @<variable> <data_type>`
    - 初期設定では値は`NULL`です
  - 変数への値の代入は次のようにします.`SET @<variable> <value>`
    - これは宣言の後にする方法です
  - 変数の宣言と値の代入を同時にすることも可能です.`DECLARE @<variable> <data_type> = <value>`
- `NULL`は値でないので条件文で`<value> = NULL`と書くことができません.代わりに`<value> is NULL`と書きます

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
WITH <sub_query> AS (<processing the sub_query>)
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

例えば,`LEFT`の場合,`LEFT`のテーブルにしかない値も取得し,`RIGHT`の列が入る部分は`NULL`で補完されます

```text
SELECT <column1> <column2> FROM <table1>
    (LEFT|RIGHT) OUTER JOIN table2 ON <condition>
```

### RANK

`RANK`は順序を付け,列に整数がデータとして入ります

`<name>`という列としてDBを更新します

順序付けの基準は`ORDER BY`で定め,`PARTITION BY`でグループごとに順位付けることができます

```text
RANK() OVER (PARITITION BY <group> ORDER BY <value> (DESC|ASC)) [AS] name
```
