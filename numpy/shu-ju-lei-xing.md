# 数据类型

## 基本数据类型

| 名称         | 描述                                                 |
| ---------- | -------------------------------------------------- |
| bool\_     | 布尔型数据类型（True 或者 False）                             |
| int\_      | 默认的整数类型（类似于 C 语言中的 long，int32 或 int64）             |
| intc       | 与 C 的 int 类型一样，一般是 int32 或 int 64                  |
| intp       | 用于索引的整数类型（类似于 C 的 ssize\_t，一般情况下仍然是 int32 或 int64） |
| int8       | 字节（-128 to 127）                                    |
| int16      | 整数（-32768 to 32767）                                |
| int32      | 整数（-2147483648 to 2147483647）                      |
| int64      | 整数（-9223372036854775808 to 9223372036854775807）    |
| uint8      | 无符号整数（0 to 255）                                    |
| uint16     | 无符号整数（0 to 65535）                                  |
| uint32     | 无符号整数（0 to 4294967295）                             |
| uint64     | 无符号整数（0 to 18446744073709551615）                   |
| float\_    | float64 类型的简写                                      |
| float16    | 半精度浮点数，包括：1 个符号位，5 个指数位，10 个尾数位                    |
| float32    | 单精度浮点数，包括：1 个符号位，8 个指数位，23 个尾数位                    |
| float64    | 双精度浮点数，包括：1 个符号位，11 个指数位，52 个尾数位                   |
| complex\_  | complex128 类型的简写，即 128 位复数                         |
| complex64  | 复数，表示双 32 位浮点数（实数部分和虚数部分）                          |
| complex128 | 复数，表示双 64 位浮点数（实数部分和虚数部分）                          |

## 数据类型对象 dtype

数据类型对象 `numpy.dtype` 类 的实例，用来描述与数组对应的内存区域是如何使用。

* 数据的类型（整数，浮点数或者 Python 对象）
* 数据的大小（例如， 整数使用多少个字节存储）
* 数据的字节顺序（小端法或大端法）
* 在结构化类型的情况下，字段的名称、每个字段的数据类型和每个字段所取的内存块的部分
* 如果数据类型是子数组，那么它的形状和数据类型是什么。

```python
numpy.dtype(object, align, copy)
# object - 要转换为的数据类型对象
# align - 如果为 true，填充字段使其类似 C 的结构体。
# copy - 复制 dtype 对象 ，如果为 false，则是对内置数据类型对象的引用
```

### 特点

同质数组，即所有元素的数据类型必须相同\
数组的下标从 0 开始，最后一个元素下标为数组长度减1

### 自定义复合类型

可以通过`dtype` 对数据类型进行修改，也可以通过设置`dtype` 的方法来进行结构化操作，可以通过字段名来存取实际的列。

```python
import numpy as np
a = np.array([10,20,30],dtype=[('age',np.int8)])
b = np.array([(10),(20),(30)],dtype=[('age',np.int8)])
print(a)
print(a['age'])
print(a['age'][1])
print(b)
print(b['age'])
print(b['age'][0])

>>> 
[(10,) (20,) (30,)]
[10 20 30]
20
[(10,) (20,) (30,)]
[10 20 30]
10
```

```python
import numpy as np 
data=[
    ('zs',[90,80,85],15),
    ('ls',[92,81,83],16),
    ('ww',[95,85,85],15)
]
# 第一种设置dtype的方式
a = np.array(data, dtype='U3,3int32,int32') 
#U3意思是只保存 3 个字符
print(a)
print(a[0]['f0'],":",a[1]['f1'])
print("==========")

>>>
[('zs', [90, 80, 85], 15) ('ls', [92, 81, 83], 16)
 ('ww', [95, 85, 85], 15)]
zs : [92 81 83]
==========


# 升级 更方便获取数据
b = np.array(data,dtype=[('name','str',2),
                         ('scores','int32',3),
                         ('age','int32',1)
                         ])

print(b)
print(b[2]['age'])

>>>
[('zs', [90, 80, 85], [15, 15]) ('ls', [92, 81, 83], [16, 16])
 ('ww', [95, 85, 85], [15, 15])]
15
```
