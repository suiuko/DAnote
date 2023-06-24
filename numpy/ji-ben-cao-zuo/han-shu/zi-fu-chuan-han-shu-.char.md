---
description: 字符数组类 char
---

# 字符串函数 .char

| 函数             | 描述                    |
| -------------- | --------------------- |
| `add()`        | 对两个数组的逐个字符串元素进行连接     |
| multiply()     | 返回按元素多重连接后的字符串        |
| `center()`     | 居中字符串                 |
| `capitalize()` | 将字符串第一个字母转换为大写        |
| `title()`      | 将字符串的每个单词的第一个字母转换为大写  |
| `lower()`      | 数组元素转换为小写             |
| `upper()`      | 数组元素转换为大写             |
| `split()`      | 指定分隔符对字符串进行分割，并返回数组列表 |
| `splitlines()` | 返回元素中的行列表，以换行符分割      |
| `strip()`      | 移除元素开头或者结尾处的特定字符      |
| `join()`       | 通过指定分隔符来连接数组中的元素      |
| `replace()`    | 使用新字符串替换字符串中的所有子字符串   |
| `decode()`     | 数组元素依次调用`str.decode`  |
| `encode()`     | 数组元素依次调用`str.encode`  |

## np.char.add()

numpy.char.add() 函数依次对两个数组的元素进行字符串连接。

```python
import numpy as np 
 
print ('连接两个字符串：')
print (np.char.add(['hello'],[' xyz']))
print ('\n')
 
print ('连接示例：')
print (np.char.add(['hello', 'hi'],[' abc', ' xyz']))

>>>
连接两个字符串：
['hello xyz']

连接示例：
['hello abc' 'hi xyz']
```
