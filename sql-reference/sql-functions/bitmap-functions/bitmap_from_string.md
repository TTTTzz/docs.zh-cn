# bitmap_from_string

## 功能

将一个字符串转化为一个 bitmap，字符串由逗号分隔的一组 UInt32 数字组成。比如将 "0, 1, 2" 字符串转化为一个 bitmap，会对其中的第 0，1，2 位会进行设置，当输入字段不合法时返回 NULL。

## 语法

```Haskell
BITMAP_FROM_STRING(input)
```

## 参数说明

`input`: 输入的字符串，支持的数据类型为 VARCHAR。字符串里的每个值必须是 UInt32 类型数字。

## 返回值说明

返回值的数据类型为 BITMAP。如果输入字段不合法，则返回 `NULL`。如果输入字段为空字符串，则返回空。

## 示例

```Plain Text
-- 返回空值。
MySQL > select bitmap_to_string(bitmap_from_string(""));
+--------------------------------------------+
|  bitmap_to_string(bitmap_from_string(''))  |
+--------------------------------------------+
|                                            |
+--------------------------------------------+

-- 返回`0,1,2`。
MySQL > select bitmap_to_string(bitmap_from_string("0, 1, 2"));
+-------------------------------------------------+
| bitmap_to_string(bitmap_from_string('0, 1, 2')) |
+-------------------------------------------------+
| 0,1,2                                           |
+-------------------------------------------------+

-- 输入非法，返回NULL。
MySQL > select bitmap_from_string("-1, 0, 1, 2");
+----------------------------------------+
|   bitmap_from_string('-1, 0, 1, 2')    |
+----------------------------------------+
| NULL                                   |
+----------------------------------------+
```
