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

>>>
连接两个字符串：
['hello xyz']

连接示例：
['hello abc' 'hi xyz']
```

## np.char.multiply()

```python
import numpy as np
print(np.char.multiply('Runoob',3))

>>>
Runoob Runoob Runoob
```

## np.char.center()

numpy.char.center() 函数用于将字符串居中，并使用指定字符在左侧和右侧进行填充

```python
import numpy as np 
 
# np.char.center(str , width,fillchar) ：
# str: 字符串，width: 长度，fillchar: 填充字符
print (np.char.center('Runoob', 20,fillchar = '*'))

>>>
*******Runoob*******
```

## numpy.char.capitalize()

numpy.char.capitalize() 函数将字符串的第一个字母转换为大写

## numpy.char.title()

numpy.char.title() 函数将字符串的每个单词的第一个字母转换为大写

## numpy.char.lower()

函数对数组的每个元素转换为小写。它对每个元素调用 str.lower

## numpy.char.upper()

函数对数组的每个元素转换为大写。它对每个元素调用 str.upper

## numpy.char.split()

通过指定分隔符对字符串进行分割，并返回数组。默认情况下，分隔符为空格。

```python
import numpy as np 
 
# 分隔符默认为空格
print (np.char.split ('i like runoob?'))
# 分隔符为 .
print (np.char.split ('www.runoob.com', sep = '.'))

>>>
['i', 'like', 'runoob?']
['www', 'runoob', 'com']
```

## numpy.char.splitlines()

函数以换行符作为分隔符来分割字符串，并返回数组

\n，\r，\r\n 都可用作换行符

```python
import numpy as np 
 
# 换行符 \n
print (np.char.splitlines('i\nlike runoob?')) 
print (np.char.splitlines('i\rlike runoob?'))

>>>
['i', 'like runoob?']
['i', 'like runoob?']
```

## numpy.char.join()

函数通过指定分隔符来连接数组中的元素或字符串

```python
import numpy as np 
 
# 操作字符串
print (np.char.join(':','runoob'))
 
# 指定多个分隔符操作数组元素
print (np.char.join([':','-'],['runoob','google']))

>>>
r:u:n:o:o:b
['r:u:n:o:o:b' 'g-o-o-g-l-e']
```

## numpy.char.replace()

函数使用新字符串替换字符串中的所有子字符串。

```python
import numpy as np 
 
print (np.char.replace ('i like runoob', 'oo', 'cc'))

>>>
i like runccb
```

