# array_contains

## 功能

检查数组中是否包含某个元素，是的话返回1，否则返回0.

## 语法

```Haskell
array_contains(any_array, any_element)
```

## 示例

```plain text
mysql> select array_contains(["apple","orange","pear"], "orange");
+-----------------------------------------------------+
| array_contains(['apple','orange','pear'], 'orange') |
+-----------------------------------------------------+
|                                                   1 |
+-----------------------------------------------------+
1 row in set (0.01 sec)
```

也可以检查数组中是否包含NULL。

```plain text
mysql> select array_contains([1, NULL], NULL);
+--------------------------------+
| array_contains([1,NULL], NULL) |
+--------------------------------+
|                              1 |
+--------------------------------+
1 row in set (0.00 sec)
```

可以检查多维数组中是否包含某个子数组，此时要求子数组元素完全匹配，包括元素排列顺序

```plain text
mysql> select array_contains([[1,2,3], [4,5,6]], [4,5,6]);
+--------------------------------------------+
| array_contains([[1,2,3],[4,5,6]], [4,5,6]) |
+--------------------------------------------+
|                                          1 |
+--------------------------------------------+
1 row in set (0.00 sec)

mysql> select array_contains([[1,2,3], [4,5,6]], [4,6,5]);
+--------------------------------------------+
| array_contains([[1,2,3],[4,5,6]], [4,6,5]) |
+--------------------------------------------+
|                                          0 |
+--------------------------------------------+
1 row in set (0.00 sec)
```
