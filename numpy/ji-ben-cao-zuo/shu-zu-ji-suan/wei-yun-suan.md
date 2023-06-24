# 位运算

| 函数            | 描述          |
| ------------- | ----------- |
| `bitwise_and` | 对数组元素执行位与操作 |
| `bitwise_or`  | 对数组元素执行位或操作 |
| `invert`      | 按位取反        |
| `left_shift`  | 向左移动二进制表示的位 |
| `right_shift` | 向右移动二进制表示的位 |

**注：**也可以使用 "&"、 "\~"、 "|" 和 "^" 等操作符进行计算。

## bitwise\_and

位与操作运算规律如下：

<table><thead><tr><th width="100">A</th><th width="106">B</th><th>AND</th></tr></thead><tbody><tr><td>1</td><td>1</td><td>1</td></tr><tr><td>1</td><td>0</td><td>0</td></tr><tr><td>0</td><td>1</td><td>0</td></tr><tr><td>0</td><td>0</td><td>0</td></tr></tbody></table>

## bitwise\_or

位或操作运算规律如下：

<table><thead><tr><th width="97">A</th><th width="103">B</th><th>OR</th></tr></thead><tbody><tr><td>1</td><td>1</td><td>1</td></tr><tr><td>1</td><td>0</td><td>1</td></tr><tr><td>0</td><td>1</td><td>1</td></tr><tr><td>0</td><td>0</td><td>0</td></tr></tbody></table>

## invert

对于有符号整数，取该二进制数的补码，然后 +1。二进制数，最高位为0表示正数，最高位为 1 表示负数。

看看 \~1 的计算步骤：

* 将**`1`**(这里叫：原码)转二进制 ＝ **`00000001`**
* 按位取反 ＝ **`11111110`**
* 发现符号位(即最高位)为**`1`**(表示负数)，将除符号位之外的其他数字取反 ＝ **`10000001`**
* 末位加1取其补码 ＝ **`10000010`**
* 转换回十进制 ＝ **`-2`**

<table data-header-hidden><thead><tr><th width="98">表达式</th><th width="200">二进制值（2 的补数）</th><th>十进制</th></tr></thead><tbody><tr><td>5</td><td>00000000 00000000 00000000 0000010</td><td>5</td></tr><tr><td>~5</td><td>11111111 11111111 11111111 11111010</td><td>-6</td></tr></tbody></table>

## left\_shift( )

将数组元素的二进制形式向左移动到指定位置，右侧附加相等数量的 0

## right\_shift( )

将数组元素的二进制形式向右移动到指定位置，左侧附加相等数量的 0。
