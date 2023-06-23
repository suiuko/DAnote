# 翻转数组

<details>

<summary>目录</summary>

[#1.-transpose-arr-axes](fan-zhuan-shu-zu.md#1.-transpose-arr-axes "mention") 对换维度

[#2.-rollaxis-arr-axis-start](fan-zhuan-shu-zu.md#2.-rollaxis-arr-axis-start "mention")

[#3.-swapaxes-arr-axis1-axis2](fan-zhuan-shu-zu.md#3.-swapaxes-arr-axis1-axis2 "mention")

</details>

| 函数          | 描述                      |
| ----------- | ----------------------- |
| `transpose` | 对换数组的维度                 |
| `ndarray.T` | 和 `self.transpose()` 相同 |
| `rollaxis`  | 向后滚动指定的轴                |
| `swapaxes`  | 对换数组的两个轴                |

### 1. transpose(arr,axes)

arr ：要操作的数组\
axes ： 整数列表，对应维度，通常所有维度都会对换

`numpy.ndarray.T` 类似于 `numpy.transpose`&#x20;

```python
import numpy as np
 
a = np.arange(12).reshape(3,4)
 
print ('原数组：')
print (a )
print ('\n')
 
print ('对换数组：')
print (np.transpose(a))

>>>
原数组：
[[ 0  1  2  3]
 [ 4  5  6  7]
 [ 8  9 10 11]]


对换数组：
[[ 0  4  8]
 [ 1  5  9]
 [ 2  6 10]
 [ 3  7 11]]
```

### 2. rollaxis(arr,axis,start)

* `arr`：数组
* `axis`：要向后滚动的轴，其它轴的相对位置不会改变
* `start`：默认为零，表示完整的滚动。会滚动到特定位置

```python
# numpy.rollaxis

import numpy as np
 
# 创建了三维的 ndarray
a = np.arange(8).reshape(2,2,2) # 两页，两行，两列
 
print ('原数组：')
print (a)
print ('获取数组中一个值：')
print(np.where(a==6))   
print(a[1,1,0])  # 为 6
print ('\n')
 
 
# 将轴 2 滚动到轴 0（宽度到深度）
 
print ('调用 rollaxis 函数：')
b = np.rollaxis(a,2,0)
print (b)
# 查看元素 a[1,1,0]，即 6 的坐标，变成 [0, 1, 1]
# 最后一个 0 移动到最前面
print(np.where(b==6))   
print ('\n')
 
# 将轴 2 滚动到轴 1：（宽度到高度）
 
print ('调用 rollaxis 函数：')
c = np.rollaxis(a,2,1)
print (c)
# 查看元素 a[1,1,0]，即 6 的坐标，变成 [1, 0, 1]
# 最后的 0 和 它前面的 1 对换位置
print(np.where(c==6))   
print ('\n')

>>>
原数组：
[[[0 1]
  [2 3]]

 [[4 5]
  [6 7]]]
获取数组中一个值：
(array([1]), array([1]), array([0]))
6


调用 rollaxis 函数：
[[[0 2]
  [4 6]]

 [[1 3]
  [5 7]]]
(array([0]), array([1]), array([1]))


调用 rollaxis 函数：
[[[0 2]
  [1 3]]

 [[4 6]
  [5 7]]]
(array([1]), array([0]), array([1]))

```

### 3. swapaxes(arr,axis1,axis2)

* `arr`：输入的数组
* `axis1`：对应第一个轴的整数
* `axis2`：对应第二个轴的整数

```python
import numpy as np
 
# 创建了三维的 ndarray
a = np.arange(8).reshape(2,2,2)
 
print ('原数组：')
print (a)
print ('\n')
# 现在交换轴 0（深度方向）到轴 2（宽度方向）
 
print ('调用 swapaxes 函数后的数组：')
print (np.swapaxes(a, 2, 0))


>>>
原数组：
[[[0 1]
  [2 3]]

 [[4 5]
  [6 7]]]


调用 swapaxes 函数后的数组：
[[[0 4]
  [2 6]]

 [[1 5]
  [3 7]]]
```
