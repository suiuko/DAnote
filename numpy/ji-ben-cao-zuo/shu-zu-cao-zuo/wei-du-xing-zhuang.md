# 维度形状

<details>

<summary>目录</summary>

[#1.-shi-tu-bian-wei-shu-ju-gong-xiang](wei-du-xing-zhuang.md#1.-shi-tu-bian-wei-shu-ju-gong-xiang "mention") reshape()  ravel() resize()&#x20;

[#2.-fu-zhi-bian-wei-shu-ju-du-li-flatten](wei-du-xing-zhuang.md#2.-fu-zhi-bian-wei-shu-ju-du-li-flatten "mention")

[#3.-flat](wei-du-xing-zhuang.md#3.-flat "mention")

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

### 1. 广播 broadcast&#x20;

广播(Broadcast)是 numpy 对不同形状(shape)的数组进行数值计算的方式， 对数组的算术运算通常在相应的元素上进行。

如果两个数组 a 和 b 形状相同，即满足 **a.shape == b.shape**，那么 a\*b 的结果就是 a 与 b 数组对应位相乘。这要求维数相同，且各维度的长度相同。

**广播的规则:**

* 让所有输入数组都向其中形状最长的数组看齐，形状中不足的部分都通过在前面加 1 补齐。
* 输出数组的形状是输入数组形状的各个维度上的最大值。
* 如果输入数组的某个维度和输出数组的对应维度的长度相同或者其长度为 1 时，这个数组能够用来计算，否则出错。
* 当输入数组的某个维度的长度为 1 时，沿着此维度运算时都用此维度上的第一组值。

**简单理解：**对两个数组，分别比较他们的每一个维度（若其中一个数组没有当前维度则忽略），满足：

* 数组拥有相同形状。
* 当前维度的值相等。
* 当前维度的值有一个是 1。

```python
import numpy as np 
 
a = np.array([1,2,3,4]) 
b = np.array([10,20,30,40]) 
c = a * b 
print (c)

>>>
[ 10  40  90 160]
```

```python
# 当运算中的 2 个数组的形状不同时，numpy 将自动触发广播机制
import numpy as np 
 
a = np.array([[ 0, 0, 0],
           [10,10,10],
           [20,20,20],
           [30,30,30]])
b = np.array([0,1,2])
print(a + b)

>>>
[[ 0  1  2]
 [10 11 12]
 [20 21 22]
 [30 31 32]]
```

<figure><img src="../../../.gitbook/assets/image0020619.gif" alt=""><figcaption></figcaption></figure>
