# 连接和分割

<details>

<summary>连接数组</summary>

[#1.-concatenate](lian-jie-he-fen-ge.md#1.-concatenate "mention")

[#2.-stack](lian-jie-he-fen-ge.md#2.-stack "mention")

[#3.-chui-zhi-fang-xiang-hstack-shui-ping-dui-die](lian-jie-he-fen-ge.md#3.-chui-zhi-fang-xiang-hstack-shui-ping-dui-die "mention")

[#4.-shui-ping-fang-xiang-vstack-chui-zhi-dui-die](lian-jie-he-fen-ge.md#4.-shui-ping-fang-xiang-vstack-chui-zhi-dui-die "mention")

</details>

<details>

<summary>分割数组</summary>

[#numpy.split](lian-jie-he-fen-ge.md#numpy.split "mention")

[#hsplit](lian-jie-he-fen-ge.md#hsplit "mention")

[#vsplit](lian-jie-he-fen-ge.md#vsplit "mention")

</details>

## 1. 连接数组

| 函数            | 描述              |
| ------------- | --------------- |
| `concatenate` | 连接沿现有轴的数组序列     |
| `stack`       | 沿着新的轴加入一系列数组。   |
| `hstack`      | 水平堆叠序列中的数组（列方向） |
| `vstack`      | 竖直堆叠序列中的数组（行方向） |

### 1. concatenate

numpy.concatenate 函数用于沿指定轴连接相同形状的两个或多个数组，格式如下：

```
numpy.concatenate((a1, a2, ...), axis)
```

参数说明：

* `a1, a2, ...`：相同类型的数组
* `axis`：沿着它连接数组的轴，默认为 0

```python
# numpy.concatenate
import numpy as np
 
a = np.array([[1,2],[3,4]])
 
print ('第一个数组：')
print (a)
print ('\n')
b = np.array([[5,6],[7,8]])
 
print ('第二个数组：')
print (b)
print ('\n')
# 两个数组的维度相同
 
print ('沿轴 0 连接两个数组：')
print (np.concatenate((a,b)))
print ('\n')
 
print ('沿轴 1 连接两个数组：')
print (np.concatenate((a,b),axis = 1))

>>>
第一个数组：
[[1 2]
 [3 4]]


第二个数组：
[[5 6]
 [7 8]]


沿轴 0 连接两个数组：
[[1 2]
 [3 4]
 [5 6]
 [7 8]]


沿轴 1 连接两个数组：
[[1 2 5 6]
 [3 4 7 8]]
```

### 2. stack

numpy.stack 函数用于沿新轴连接数组序列，格式如下：

```
numpy.stack(arrays, axis)
```

参数说明：

* `arrays`相同形状的数组序列
* `axis`：返回数组中的轴，输入数组沿着它来堆叠

```python
# stack
import numpy as np
 
a = np.array([[1,2],[3,4]])
 
print ('第一个数组：')
print (a)
print ('\n')
b = np.array([[5,6],[7,8]])
 
print ('第二个数组：')
print (b)
print ('\n')
 
print ('沿轴 0 堆叠两个数组：')
print (np.stack((a,b),0))
print ('\n')
 
print ('沿轴 1 堆叠两个数组：')
print (np.stack((a,b),1))

>>>
第一个数组：
[[1 2]
 [3 4]]


第二个数组：
[[5 6]
 [7 8]]


沿轴 0 堆叠两个数组：
[[[1 2]
  [3 4]]

 [[5 6]
  [7 8]]]


沿轴 1 堆叠两个数组：
[[[1 2]
  [5 6]]

 [[3 4]
  [7 8]]]
```

### 3. 垂直方向 hstack - 水平堆叠

水平堆叠序列中的数组（列方向）

```python
import numpy as np
 
a = np.array([[1,2],[3,4]])
 
print ('第一个数组：')
print (a)
print ('\n')
b = np.array([[5,6],[7,8]])
 
print ('第二个数组：')
print (b)
print ('\n')
 
print ('水平堆叠：')
c = np.hstack((a,b))
print (c)
print ('\n')

>>>
第一个数组：
[[1 2]
 [3 4]]


第二个数组：
[[5 6]
 [7 8]]


水平堆叠：
[[1 2 5 6]
 [3 4 7 8]]
```

### 4. 水平方向 vstack - 垂直堆叠

垂直堆叠序列中的数组（行方向）

```python
import numpy as np
 
a = np.array([[1,2],[3,4]])
 
print ('第一个数组：')
print (a)
print ('\n')
b = np.array([[5,6],[7,8]])
 
print ('第二个数组：')
print (b)
print ('\n')
 
print ('竖直堆叠：')
c = np.vstack((a,b))
print (c)

>>>
第一个数组：
[[1 2]
 [3 4]]


第二个数组：
[[5 6]
 [7 8]]


竖直堆叠：
[[1 2]
 [3 4]
 [5 6]
 [7 8]]
```

## &#x20;2. 分割数组

| 函数       | 数组及操作               |
| -------- | ------------------- |
| `split`  | 将一个数组分割为多个子数组       |
| `hsplit` | 将一个数组水平分割为多个子数组（按列） |
| `vsplit` | 将一个数组垂直分割为多个子数组（按行） |

### numpy.split

numpy.split 函数沿特定的轴将数组分割为子数组，格式如下：

```
numpy.split(ary, indices_or_sections, axis)
```

参数说明：

* `ary`：被分割的数组
* `indices_or_sections`：如果是一个整数，就用该数平均切分，如果是一个数组，为沿轴切分的位置（左开右闭）
* `axis`：设置沿着哪个方向进行切分，\
  默认为 0，横向切分，即水平方向。将列轴进行切分\
  为 1 时，纵向切分，即竖直方向。将横轴进行切分

```python
import numpy as np

a = np.arange(16).reshape(4, 4)
print('第一个数组：')
print(a)
print('\n')
print('默认分割（0轴）：')
b = np.split(a,2)
print(b)
print('\n')

print('沿水平方向分割：')
c = np.split(a,2,1)
print(c)
print('\n')

print('沿水平方向分割：')
d= np.hsplit(a,2)
print(d)

>>>
第一个数组：
[[ 0  1  2  3]
 [ 4  5  6  7]
 [ 8  9 10 11]
 [12 13 14 15]]


默认分割（0轴）：
[array([[0, 1, 2, 3],
       [4, 5, 6, 7]]), array([[ 8,  9, 10, 11],
       [12, 13, 14, 15]])]


沿水平方向分割：
[array([[ 0,  1],
       [ 4,  5],
       [ 8,  9],
       [12, 13]]), array([[ 2,  3],
       [ 6,  7],
       [10, 11],
       [14, 15]])]


沿水平方向分割：
[array([[ 0,  1],
       [ 4,  5],
       [ 8,  9],
       [12, 13]]), array([[ 2,  3],
       [ 6,  7],
       [10, 11],
       [14, 15]])]
```

### hsplit()

用于水平分割数组，通过指定要返回的相同形状的数组数量来拆分原数组

```python
# hsplit 沿着水平分割数组
import numpy as np
 
harr = np.floor(10 * np.random.random((2, 6)))
print ('原array：')
print(harr)
 
print ('拆分后：')
print(np.hsplit(harr, 3))

>>>
原array：
[[3. 8. 6. 7. 6. 6.]
 [2. 6. 4. 0. 7. 5.]]
拆分后：
[array([[3., 8.],
       [2., 6.]]), array([[6., 7.],
       [4., 0.]]), array([[6., 6.],
       [7., 5.]])]
```

### vsplit()

用于水平分割数组，通过指定要返回的相同形状的数组数量来拆分原数组

```python
# vsplit 沿着垂直分割数组
import numpy as np
 
a = np.arange(16).reshape(4,4)
 
print ('第一个数组：')
print (a)
print ('\n')
 
print ('竖直分割：')
b = np.vsplit(a,2)
print (b)

>>>
第一个数组：
[[ 0  1  2  3]
 [ 4  5  6  7]
 [ 8  9 10 11]
 [12 13 14 15]]


竖直分割：
[array([[0, 1, 2, 3],
       [4, 5, 6, 7]]), array([[ 8,  9, 10, 11],
       [12, 13, 14, 15]])]
```
