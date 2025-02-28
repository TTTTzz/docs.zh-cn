# timestampdiff

## 功能

返回`datetime_expr2`和`datetime_expr1`的差值，其中`datetime_expr1`和`datetime_expr2`是日期或日期时间表达式。

结果(整数)的单位由`unit`参数给出。`interval`的单位由`unit`参数给出，应该是下列值之一:
SECOND，MINUTE，HOUR，DAY，WEEK，MONTH，YEAR。

## 语法

```Haskell
INT TIMESTAMPDIFF(unit, DATETIME datetime_expr1, DATETIME datetime_expr2)`
```

## 示例

```plain text

SELECT TIMESTAMPDIFF(MONTH,'2003-02-01','2003-05-01');
+--------------------------------------------------------------------+
| timestampdiff(MONTH, '2003-02-01 00:00:00', '2003-05-01 00:00:00') |
+--------------------------------------------------------------------+
|                                                                  3 |
+--------------------------------------------------------------------+

SELECT TIMESTAMPDIFF(YEAR,'2002-05-01','2001-01-01');
+-------------------------------------------------------------------+
| timestampdiff(YEAR, '2002-05-01 00:00:00', '2001-01-01 00:00:00') |
+-------------------------------------------------------------------+
|                                                                -1 |
+-------------------------------------------------------------------+

SELECT TIMESTAMPDIFF(MINUTE,'2003-02-01','2003-05-01 12:05:55');
+---------------------------------------------------------------------+
| timestampdiff(MINUTE, '2003-02-01 00:00:00', '2003-05-01 12:05:55') |
+---------------------------------------------------------------------+
|                                                              128885 |
+---------------------------------------------------------------------+

```
