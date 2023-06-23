---
description: ndarray数组切片操作
---

# 切片和索引

<details>

<summary>普通索引目录</summary>

[#1.-yi-wei-shu-zu-qie-pian](qie-pian-he-suo-yin.md#1.-yi-wei-shu-zu-qie-pian "mention")

[#2.-duo-wei-shu-zu](qie-pian-he-suo-yin.md#2.-duo-wei-shu-zu "mention")

</details>

<details>

<summary><a data-mention href="qie-pian-he-suo-yin.md#gao-ji-suo-yin">#gao-ji-suo-yin</a>高级索引目录</summary>

[#1.-zheng-shu-shu-zu-suo-yin](qie-pian-he-suo-yin.md#1.-zheng-shu-shu-zu-suo-yin "mention")

[#2.-bu-er-suo-yin](qie-pian-he-suo-yin.md#2.-bu-er-suo-yin "mention")

[#3.-hua-shi-suo-yin](qie-pian-he-suo-yin.md#3.-hua-shi-suo-yin "mention")

</details>

## ➡️ 普通索引

ndarray数组可以基于 0-n 的<mark style="color:orange;">下标进行索引</mark>，切片对象可以通过内置的slice函数进行切片。

### 1. 一维数组切片

&#x20;数组对象切片的参数设置与列表切面参数类似，<mark style="color:orange;">【下标从 0 开始】</mark>

**`数组对象[起始位置下标:终止位置下标:步长]`**&#x20;

`+步长`：默认切从首到尾\
`-步长` ：默认切从尾到头

<mark style="color:yellow;">切的范围为：\[起始位置下标：终止位置下标)</mark>   提取两个索引(不包括停止索引)之间的项。

```python
import numpy as np
a = np.arange(1,10)
print(a) # 123456789
print(a[:3]) # 123
print(a[3:6]) # 456
print(a[6:]) # 789
print(a[::-1]) #987654321
print(a[:-4:-1]) #987
print(a[-4:-7:-1]) #654
print(a[-7::-1]) # 321
```

### 2. 多维数组

**数组对象\[行操作，列操作]**

**数组对象\[ 1 维度, 2 维度, 3 维度]**

```python
import numpy as np
a = np.arange(1,28)
a.resize(3,3,3)
print(a)

print("======")
# 切出 1 页
print("切出 1 页")
print(a[0,:,:])

# 切出 所有页的第一行
print("所有页的第一行")
print(a[:,1,:])

# 切出 0 页的 1 行 1 列
print("切出 0 页的 1 行 1 列")
print(a[0,:,1])
```

## ➡️ 高级索引

### 1. 整数数组索引

整数数组索引是指使用一个数组来访问另一个数组的元素。这个数组中的每个元素都是目标数组中某个维度上的索引值。

[#3.-hua-shi-suo-yin](qie-pian-he-suo-yin.md#3.-hua-shi-suo-yin "mention") ⬅️可以和花式索引一起看

`索引方式 ： 数组[[行元素] ,[列元素]]`

```python
import numpy as np 

# 输出数组中(0,0)，(1,1) 和 (2,0) 位置处的元素
x = np.array([[1,  2],  [3,  4],  [5,  6]]) 
y = x[[0,1,2],  [0,1,0]]  
print (y)

>>>
[1  4  5]
```

可以利用切片的方式与索引数组组合。

```python
import numpy as np
 
a = np.array([[1,2,3], [4,5,6],[7,8,9]])
b = a[1:3, 1:3] 
c = a[1:3,[1,2]]
d = a[...,1:]
print(b)
print(c)
print(d)

>>>
[[5 6]
 [8 9]]
# 截取 a[[下标为 1 和 2 的行][下标为 1 和 2 的列]]

[[5 6]
 [8 9]]
# 截取 a[[下标为 1 和 2 的行][下标为 1 和 2 的列]]
 
[[2 3]
 [5 6]
 [8 9]]
# 截取 a[[下标所有行][下标为 1 和 2 的列]]
```

### 2. 布尔索引

布尔索引通过布尔运算（如：比较运算符）来获取符合指定条件的元素的数组。

```python
# 获取大于 5 的元素

import numpy as np
x = np.array([[0,1,2],[3,4,5],[6,7,8],[9,10,11]])
print ('我们的数组是：')
print (x)
print ('\n')
# 打印出大于 5 的元素  
print  ('大于 5 的元素是：')
print (x[x >  5])
```

### 3. 花式索引

花式索引指的是利用整数数组进行索引。

**花式索引根据索引数组的值作为目标数组的某个轴的下标来取值。**

对于使用一维整型数组作为索引，如果目标是一维数组，那么索引的结果就是对应位置的元素，如果目标是二维数组，那么就是对应下标的行。

花式索引跟切片不一样，它总是将数据复制到新数组中

#### （1）一维数组

一维数组只有一个轴 **axis = 0**，所以一维数组就在 **axis = 0** 这个轴上取值

```python
import numpy as np

x = np.arange(9)
print(x)
# 一维数组读取指定下标对应的元素
print("-------读取下标对应的元素-------")
x2 = x[[0, 6]] # 使用花式索引
print(x2)

print(x2[0])
print(x2[1])

>>>
[0 1 2 3 4 5 6 7 8]
-------读取下标对应的元素-------
[0 6]
0
6
```

#### （2）二维数组

1. 传入顺序索引数组

```python
import numpy as np 
 
x=np.arange(32).reshape((8,4))
print(x)
# 二维数组读取指定下标对应的行
print("-------读取下标对应的行-------")
print (x[[4,2,1,7]])

>>>
[[ 0  1  2  3]
 [ 4  5  6  7]
 [ 8  9 10 11]
 [12 13 14 15]
 [16 17 18 19]
 [20 21 22 23]
 [24 25 26 27]
 [28 29 30 31]]
-------读取下标对应的行-------
[[16 17 18 19]
 [ 8  9 10 11]
 [ 4  5  6  7]
 [28 29 30 31]]
```

2. 传入倒序索引

```python
# 倒序索引
import numpy as np 
 
x=np.arange(32).reshape((8,4))
print (x[[-4,-2,-1,-7]])

>>>
[[16 17 18 19]
 [24 25 26 27]
 [28 29 30 31]
 [ 4  5  6  7]]
```

3. 传入多个索引数组（需要用np.ix\_）

`np.ix_` 函数就是输入两个数组，产生笛卡尔积的映射关系

> 笛卡尔乘积是指在数学中，两个集合 X 和 Y 的笛卡尔积（Cartesian product），又称直积，表示为 **X×Y**，第一个对象是X的成员而第二个对象是 Y 的所有可能有序对的其中一个成员

```
例如 A={a,b}, B={0,1,2}，则：
A×B={(a, 0), (a, 1), (a, 2), (b, 0), (b, 1), (b, 2)}
B×A={(0, a), (0, b), (1, a), (1, b), (2, a), (2, b)}
```

```python
# 传入多个索引数组 要使用np.ix_

import numpy as np 
 
x=np.arange(32).reshape((8,4))
print(x)
print("======")
print(x[np.ix_([1,5,7,2],[0,3,1,2])])

>>>
[[ 0  1  2  3]
 [ 4  5  6  7]
 [ 8  9 10 11]
 [12 13 14 15]
 [16 17 18 19]
 [20 21 22 23]
 [24 25 26 27]
 [28 29 30 31]]
======
[[ 4  7  5  6]
 [20 23 21 22]
 [28 31 29 30]
 [ 8 11  9 10]]
```
