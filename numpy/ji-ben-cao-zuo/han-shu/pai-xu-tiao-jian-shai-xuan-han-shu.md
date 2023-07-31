# 排序、条件筛选函数

<details>

<summary>目录</summary>



</details>

| 种类                  | 速度 | 最坏情况          | 工作空间  | 稳定性 |
| ------------------- | -- | ------------- | ----- | --- |
| `'quicksort'`（快速排序） | 1  | `O(n^2)`      | 0     | 否   |
| `'mergesort'`（归并排序） | 2  | `O(n*log(n))` | \~n/2 | 是   |
| `'heapsort'`（堆排序）   | 3  | `O(n*log(n))` | 0     | 否   |

### numpy.sort()

numpy.sort() 函数返回输入数组的排序副本。函数格式如下：

```
numpy.sort(a, axis, kind, order)
```

参数说明：

* a: 要排序的数组
* axis: 沿着它排序数组的轴，如果没有数组会被展开，沿着最后的轴排序， axis=0 按列排序，axis=1 按行排序
* kind: 默认为'quicksort'（快速排序）
* order: 如果数组包含字段，则是要排序的字段

```python
import numpy as np

# np.sort() 默认快速排序

a = np.array([[3,7],[9,1]])  
print ('我们的数组是：')
print (a)
print ('\n')
print ('调用 sort() 函数：')
print (np.sort(a))
print ('\n')
print ('按列排序：')
print (np.sort(a, axis =  0))
print ('\n')
# 在 sort 函数中排序字段 
dt = np.dtype([('name',  'S10'),('age',  int)]) 
a = np.array([("raju",21),("anil",25),("ravi",  17),  ("amar",27)], dtype = dt)  
print ('我们的数组是：')
print (a)
print ('\n')
print ('按 name 排序：')
print (np.sort(a, order =  'name'))
print ('\n')
print ('按 age 排序：')
print(np.sort(a,order = 'age'))

>>>
我们的数组是：
[[3 7]
 [9 1]]


调用 sort() 函数：
[[3 7]
 [1 9]]


按列排序：
[[3 1]
 [9 7]]


我们的数组是：
[(b'raju', 21) (b'anil', 25) (b'ravi', 17) (b'amar', 27)]

按 name 排序：
[(b'amar', 27) (b'anil', 25) (b'raju', 21) (b'ravi', 17)]

按 age 排序：
[(b'ravi', 17) (b'raju', 21) (b'anil', 25) (b'amar', 27)]
```

### numpy.argsort() 小到大索引值

numpy.argsort() 函数返回的是数组值从小到大的索引值

```python
# argsort() 输出从小到大的索引值

import numpy as np 
 
x = np.array([3,  1,  2])  
print ('我们的数组是：')
print (x)
print ('\n')
print ('对 x 调用 argsort() 函数：')
y = np.argsort(x)  
print (y)
print ('\n')
print ('以排序后的顺序重构原数组：')
print (x[y])
print ('\n')
print ('使用循环重构原数组：')
for i in y:  
    print (x[i], end=" ")
    
>>>
我们的数组是：
[3 1 2]


对 x 调用 argsort() 函数：
[1 2 0]


以排序后的顺序重构原数组：
[1 2 3]


使用循环重构原数组

1 2 3
```

### numpy.lexsort() 多序列排序

numpy.lexsort() 用于对多个序列进行排序。把它想象成对电子表格进行排序，每一列代表一个序列，排序时优先照顾靠后的列

```python
# lexsort() 多序列排序，优先照顾靠后的列；
# 应用场景，学生多学科考试成绩排序

import numpy as np 

first_names = ('hong', 'ming', 'zhang','zhang')
age = ('12','8','9','8')
ind = np.lexsort((first_names, age))
num1 = [first_names[i] + ',' +age[i] for i in ind ]
print(num1)

>>>
['hong,12', 'ming,8', 'zhang,8', 'zhang,9']
```

### msort、sort\_complex、partition、argpartition

| 函数                                         | 描述                                                       |
| ------------------------------------------ | -------------------------------------------------------- |
| msort(a)                                   | 数组按第一个轴排序，返回排序后的数组副本。np.msort(a) 相等于 np.sort(a, axis=0)。 |
| sort\_complex(a)                           | 对复数按照先实部后虚部的顺序进行排序。                                      |
| partition(a, kth\[, axis, kind, order])    | 指定一个数，对数组进行分区                                            |
| argpartition(a, kth\[, axis, kind, order]) | 可以通过关键字 kind 指定算法沿着指定轴对数组进行分区                            |

```python
import numpy as np

# 复数排序
com1 = np.sort_complex([5,3,6,2,1])
print(com1)
com2 = np.sort_complex([1 + 2j, 2 - 1j, 3 - 2j, 3 - 3j, 3 + 5j])
print(com2)
>>> [1.+0.j 2.+0.j 3.+0.j 5.+0.j 6.+0.j]
>>> [1.+2.j 2.-1.j 3.-3.j 3.-2.j 3.+5.j]


a = np.array([3,4,2,1])
a1 = np.partition(a,3)
# 将数组 a 中所有元素（包括重复元素）从小到大排列，
#3 表示的是排序数组索引为 3 的数字，比该数字小的排在该数字前面，
#比该数字大的排在该数字的后面
print(a1)
a2 = np.partition(a,(1,3)) # 小于 1 的在前面，大于 3 的在后面，1 和 3 之间在中间
print(a2)

>>> [2 1 3 4]
>>> [1 2 3 4]
```
