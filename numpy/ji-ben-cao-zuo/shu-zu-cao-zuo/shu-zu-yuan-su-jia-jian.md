# 数组元素加减

<table data-header-hidden><thead><tr><th width="162.5"></th><th></th></tr></thead><tbody><tr><td><code>resize</code></td><td>返回指定形状的新数组</td></tr><tr><td><code>append</code></td><td>将值添加到数组末尾</td></tr><tr><td><code>insert</code></td><td>沿指定轴将值插入到指定下标之前</td></tr><tr><td><code>delete</code></td><td>删掉某个轴的子数组，并返回删除后的新数组</td></tr><tr><td><code>unique</code></td><td>查找数组内的唯一元素</td></tr></tbody></table>

## resize()

numpy.resize 函数返回指定大小的新数组。

如果新数组大小大于原始大小，则包含原始数组中的元素的副本。

```
numpy.resize(arr, shape)
```

参数说明：

* `arr`：要修改大小的数组
* `shape`：返回数组的新形状

## append()

numpy.append 函数在数组的末尾添加值。 追加操作会分配整个数组，并把原来的数组复制到新数组中。 此外，输入数组的维度必须匹配否则将生成ValueError。

append 函数返回的始终是一个一维数组。

```
numpy.append(arr, values, axis=None)
```

参数说明：

* `arr`：输入数组
* `values`：要向`arr`添加的值，需要和`arr`形状相同（除了要添加的轴）
* `axis`：默认为 None。当axis无定义时，是横向加成，返回总是为一维数组！当axis有定义的时候，分别为0和1的时候。当axis有定义的时候，分别为0和1的时候（列数要相同）。当axis为1时，数组是加在右边（行数要相同）。

```python
import numpy as np
 
a = np.array([[1,2,3],[4,5,6]])
 
print ('第一个数组：')
print (a)
print ('\n')
 
print ('向数组添加元素：')
print (np.append(a, [7,8,9]))
print ('\n')
 
print ('沿轴 0 添加元素：')
print (np.append(a, [[7,8,9]],axis = 0))
print ('\n')
 
print ('沿轴 1 添加元素：')
print (np.append(a, [[5,5,5],[7,8,9]],axis = 1))

>>>
第一个数组：
[[1 2 3]
 [4 5 6]]


向数组添加元素：
[1 2 3 4 5 6 7 8 9]


沿轴 0 添加元素：
[[1 2 3]
 [4 5 6]
 [7 8 9]]


沿轴 1 添加元素：
[[1 2 3 5 5 5]
 [4 5 6 7 8 9]]
```

## insert

numpy.insert 函数在给定索引之前，沿给定轴在输入数组中插入值。

如果值的类型转换为要插入，则它与输入数组不同。 插入没有原地的，函数会返回一个新数组。 此外，如果未提供轴，则输入数组会被展开。

```
numpy.insert(arr, obj, values, axis)
```

参数说明：

* `arr`：输入数组
* `obj`：在其之前插入值的索引
* `values`：要插入的值
* `axis`：沿着它插入的轴，如果未提供，则输入数组会被展开

```python
import numpy as np
 
a = np.array([[1,2],[3,4],[5,6]])
 
print ('第一个数组：')
print (a)
print ('\n')
 
print ('未传递 Axis 参数。 在删除之前输入数组会被展开。')
print (np.insert(a,3,[11,12]))
print ('\n')

print('传递 axis 参数')
print (np.insert(a,1,[11,12],axis = 0))
print ('\n')
print ('传递了 Axis 参数。 会广播值数组来配输入数组。')
 
print ('沿轴 0 广播：')
print (np.insert(a,1,[11],axis = 0))
print ('\n')
 
print ('沿轴 1 广播：')
print (np.insert(a,1,11,axis = 1))

>>>
第一个数组：
[[1 2]
 [3 4]
 [5 6]]


未传递 Axis 参数。 在删除之前输入数组会被展开。
[ 1  2  3 11 12  4  5  6]


传递 axis 参数
[[ 1  2]
 [11 12]
 [ 3  4]
 [ 5  6]]


传递了 Axis 参数。 会广播值数组来配输入数组。
沿轴 0 广播：
[[ 1  2]
 [11 11]
 [ 3  4]
 [ 5  6]]


沿轴 1 广播：
[[ 1 11  2]
 [ 3 11  4]
 [ 5 11  6]]
```

## unique()

numpy.unique 函数用于去除数组中的重复元素。

```
numpy.unique(arr, return_index, return_inverse, return_counts)
```

* `arr`：输入数组，如果不是一维数组则会展开
* `return_index`：如果为`true`，返回新列表元素在旧列表中的位置（下标），并以列表形式储
* `return_inverse`：如果为`true`，返回旧列表元素在新列表中的位置（下标），并以列表形式储
* `return_counts`：如果为`true`，返回去重数组中的元素在原数组中的出现次数

```python
import numpy as np
 
a = np.array([5,2,6,2,7,5,6,8,2,9])
 
print ('第一个数组：')
print (a)
print ('\n')
 
print ('第一个数组的去重值：')
u = np.unique(a)
print (u)
print ('\n')
 
print ('去重数组的索引数组：')
u,indices = np.unique(a, return_index = True)
print (indices)
print ('\n')
 
print ('我们可以看到每个和原数组下标对应的数值：')
print (a)
print ('\n')
 
print ('去重数组的下标：')
u,indices = np.unique(a,return_inverse = True)
print (u)
print ('\n')
 
print ('下标为：')
print (indices)
print ('\n')
 
print ('使用下标重构原数组：')
print (u[indices])
print ('\n')
 
print ('返回去重元素的重复数量：')
u,indices = np.unique(a,return_counts = True)
print (u)
print (indices)

>>>
第一个数组：
[5 2 6 2 7 5 6 8 2 9]


第一个数组的去重值：
[2 5 6 7 8 9]


去重数组的索引数组：
[1 0 2 4 7 9]


我们可以看到每个和原数组下标对应的数值：
[5 2 6 2 7 5 6 8 2 9]


去重数组的下标：
[2 5 6 7 8 9]


下标为：
[1 0 2 0 3 1 2 4 0 5]


使用下标重构原数组：
[5 2 6 2 7 5 6 8 2 9]


返回去重元素的重复数量：
[2 5 6 7 8 9]
[3 2 2 1 1 1]
```
