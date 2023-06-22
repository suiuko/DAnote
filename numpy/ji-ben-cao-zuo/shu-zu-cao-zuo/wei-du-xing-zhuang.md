# 维度形状

<details>

<summary>目录</summary>

修改形状

[#1.-shi-tu-bian-wei-shu-ju-gong-xiang](wei-du-xing-zhuang.md#1.-shi-tu-bian-wei-shu-ju-gong-xiang "mention") reshape()  ravel() resize()&#x20;

[#2.-fu-zhi-bian-wei-shu-ju-du-li-flatten](wei-du-xing-zhuang.md#2.-fu-zhi-bian-wei-shu-ju-du-li-flatten "mention")

[#3.-flat](wei-du-xing-zhuang.md#3.-flat "mention")

修改维度

[#1.-broadcast](wei-du-xing-zhuang.md#1.-broadcast "mention")

[#2.-broadcast\_to](wei-du-xing-zhuang.md#2.-broadcast\_to "mention")

[#3.-expend\_dims](wei-du-xing-zhuang.md#3.-expend\_dims "mention")

[#4.-squeeze](wei-du-xing-zhuang.md#4.-squeeze "mention")

</details>

## 一、修改形状

| `reshape` | 不改变数据的条件下修改形状             |
| --------- | ------------------------- |
| `flat`    | 数组元素迭代器                   |
| `flatten` | 返回一份数组拷贝，对拷贝所做的修改不会影响原始数组 |
| `ravel`   | 返回展开数组                    |

### 1. 视图变维（数据共享）&#x20;

### reshape() 和 ravel()

```
numpy.reshape(arr, newshape, order='C')
reshape(页，行，列)  在不改变数据的条件下修改形状

arr：要修改形状的数组
newshape：整数或者整数数组，新的形状应当兼容原有形状
order：'C' -- 按行，'F' -- 按列，'A' -- 原顺序，'k' -- 元素在内存中的出现顺序。
```

### ravel() 展平为 1 维数组

```python
import numpy as np

a = np.arange(1,9)
print(a) # p[1,2,3,4,5,6,7,8]
b = a.reshape(2,4) # 视图变维，变为2 行 4 列的二维数组
print(b)
c = b.reshape(2,2,2)  # 视图变维，变为2 页 2 行 2 列的三维数组
print("====")
print(c)
print("====")
d = c.ravel()  # 变为 1 维数组
print(d)

>>> 
[1 2 3 4 5 6 7 8]
[[1 2 3 4]
 [5 6 7 8]]
====
[[[1 2]
  [3 4]]

 [[5 6]
  [7 8]]]
====
[1 2 3 4 5 6 7 8]
```

### resize( )

和 `reshape` 一样的用法，但是会在原地更改数组的结构

### 2. 复制变维（数据独立）flatten()

```python
import numpy as np
a = np.arange(1,10)
print(a, a.shape)

# 复制变维
b = a. flatten()
print(b,'->b')
print("=====数据独立后原修改不影响新的=====")
a[0]= 88
print(a)
print(b)

>>>
[1 2 3 4 5 6 7 8 9] (9,)
[1 2 3 4 5 6 7 8 9] ->b
=====数据独立后原修改不影响新的=====
[88  2  3  4  5  6  7  8  9]
[1 2 3 4 5 6 7 8 9]
```

### 3. flat()

这是一个数组元素迭代器

```python
import numpy as np
 
a = np.arange(9).reshape(3,3) 
print ('原始数组：')
for row in a:
    print (row)
 
#对数组中每个元素都进行处理，可以使用flat属性，该属性是一个数组元素迭代器：
print ('迭代后的数组：')
for element in a.flat:
    print (element)
    
>>>
原始数组：
[0 1 2]
[3 4 5]
[6 7 8]
迭代后的数组：
0
1
2
3
4
5
6
7
8
```

## 二、修改数组维度

| 维度             | 描述            |
| -------------- | ------------- |
| `broadcast`    | 产生模仿广播的对象     |
| `broadcast_to` | 将数组广播到新形状     |
| `expand_dims`  | 扩展数组的形状       |
| `squeeze`      | 从数组的形状中删除一维条目 |

### 1. broadcast&#x20;

```python
import numpy as np
 
x = np.array([[1], [2], [3]])
y = np.array([4, 5, 6])  
 
# 对 y 广播 x
b = np.broadcast(x,y)  
# 它拥有 iterator 属性，基于自身组件的迭代器元组
 
print ('对 y 广播 x：')
r,c = b.iters
 
# Python3.x 为 next(context) ，Python2.x 为 context.next()
print (next(r), next(c))
print (next(r), next(c))
print ('\n')
# shape 属性返回广播对象的形状
 
print ('广播对象的形状：')
print (b.shape)
print ('\n')
# 手动使用 broadcast 将 x 与 y 相加
b = np.broadcast(x,y)
c = np.empty(b.shape)
 
print ('手动使用 broadcast 将 x 与 y 相加：')
print (c.shape)
print ('\n')
c.flat = [u + v for (u,v) in b]
 
print ('调用 flat 函数：')
print (c)
print ('\n')
# 获得了和 NumPy 内建的广播支持相同的结果
 
print ('x 与 y 的和：')
print (x + y)

>>>
对 y 广播 x：
1 4
1 5


广播对象的形状：
(3, 3)


手动使用 broadcast 将 x 与 y 相加：
(3, 3)


调用 flat 函数：
[[5. 6. 7.]
 [6. 7. 8.]
 [7. 8. 9.]]


x 与 y 的和：
[[5 6 7]
 [6 7 8]
 [7 8 9]]
```

### 2. broadcast\_to

numpy.broadcast\_to 函数将数组广播到新形状。它在原始数组上返回只读视图。 它通常不连续。 如果新形状不符合 NumPy 的广播规则，该函数可能会抛出ValueError

```
numpy.broadcast_to(array, shape, subok)
```

```python
import numpy as np
 
a = np.arange(4).reshape(1,4)
 
print ('原数组：')
print (a)
print ('\n')
 
print ('调用 broadcast_to 函数之后：')
print (np.broadcast_to(a,(4,4)))

>>>
原数组：
[[0 1 2 3]]


调用 broadcast_to 函数之后：
[[0 1 2 3]
 [0 1 2 3]
 [0 1 2 3]
 [0 1 2 3]]
```

### 3. expend\_dims

numpy.expand\_dims 函数通过在指定位置插入新的轴来扩展数组形状，函数格式如下:

```
 numpy.expand_dims(arr, axis)
```

```python
import numpy as np
 
x = np.array(([1,2],[3,4]))
 
print ('数组 x：')
print (x)
print ('\n')
y = np.expand_dims(x, axis = 0)
 
print ('数组 y：')
print (y)
print ('\n')
 
print ('数组 x 和 y 的形状：')
print (x.shape, y.shape)
print ('\n')
# 在位置 1 插入轴
y = np.expand_dims(x, axis = 1)
 
print ('在位置 1 插入轴之后的数组 y：')
print (y)
print ('\n')
 
print ('x.ndim 和 y.ndim：')
print (x.ndim,y.ndim)
print ('\n')
 
print ('x.shape 和 y.shape：')
print (x.shape, y.shape)

>>>
数组 x：
[[1 2]
 [3 4]]


数组 y：
[[[1 2]
  [3 4]]]


数组 x 和 y 的形状：
(2, 2) (1, 2, 2)


在位置 1 插入轴之后的数组 y：
[[[1 2]]

 [[3 4]]]


x.ndim 和 y.ndim：
2 3


x.shape 和 y.shape：
(2, 2) (2, 1, 2)
```

### 4. squeeze

numpy.squeeze 函数从给定数组的形状中删除一维的条目，函数格式如下：

```
numpy.squeeze(arr, axis)
```

参数说明：

* `arr`：输入数组
* `axis`：整数或整数元组，用于选择形状中一维条目的子集

```python
import numpy as np
 
x = np.arange(9).reshape(1,3,3)
 
print ('数组 x：')
print (x)
print ('\n')
y = np.squeeze(x)
 
print ('数组 y：')
print (y)
print ('\n')
 
print ('数组 x 和 y 的形状：')
print (x.shape, y.shape)

>>>
数组 x：
[[[0 1 2]
  [3 4 5]
  [6 7 8]]]


数组 y：
[[0 1 2]
 [3 4 5]
 [6 7 8]]


数组 x 和 y 的形状：
(1, 3, 3) (3, 3)
```
