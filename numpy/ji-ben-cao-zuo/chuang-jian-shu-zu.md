# 创建数组

<details>

<summary>快速查看目录</summary>

[#yi-chuang-jian-ji-ben-shu-zu](chuang-jian-shu-zu.md#yi-chuang-jian-ji-ben-shu-zu "mention")

[#san-cong-shu-zhi-fan-wei-chuang-jian-shu-zu](chuang-jian-shu-zu.md#san-cong-shu-zhi-fan-wei-chuang-jian-shu-zu "mention")

</details>

## 创建数组

### 一、创建基本数组

### 1. array 创建数组

```python
numpy.array(object,dtype = None, copy = True, order = None, subok = False, ndmin = 0)
```

<table><thead><tr><th width="136">参数</th><th></th></tr></thead><tbody><tr><td>object</td><td>表示一个数组序列</td></tr><tr><td>dtype</td><td>可选参数，通过他可以更改数组的数据类型</td></tr><tr><td>copy</td><td>可选参数，当数据源是ndarray时表示数组能否被复制，默认 T</td></tr><tr><td>order</td><td>可选参数，以哪种内存布局创建数组。可选值：C(行序列)/F(列序列)/A(默认)</td></tr><tr><td>ndmin</td><td>可选参数，用于指定数组的纬度</td></tr><tr><td>subok</td><td>可选参数，类型为 bool 值，默认 false。为 True：使用 object 的内部数据类型；False：使用 object 数组的数据类型。</td></tr></tbody></table>

<pre class="language-python"><code class="lang-python">import numpy as np 
# 迭代对象
np.array(range(10))
<strong>>>> array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])
</strong><strong>
</strong>
#生成器
np.array([i**2 for i in range(10)]) # i**2 是取平方
array([ 0,  1,  4,  9, 16, 25, 36, 49, 64, 81])

# 取偶数
np.array(range(2,11,2))
#np.array([i for i in range(10) if i%2 == 0])

# 最小维度  

a = np.array([1, 2, 3, 4, 5], ndmin =  2)  
print (a)
>>> [[1 2 3 4 5]]

print(a.shape) # 纬度
</code></pre>

### 2. empty(shape,dtype = float,order='C')

| 参数    | 描述                                        |
| ----- | ----------------------------------------- |
| shape | 数组形状                                      |
| dtype | 数据类型，可选                                   |
| order | 有"C"和"F"两个选项,分别代表，行优先和列优先，在计算机内存中的存储元素的顺序 |

```python
import numpy as np 
x = np.empty([3,2], dtype = int) 
print (x)
# 注意，数组元素为随机值，因为他们没有初始化
```

### 3. zeros(数组元素个数, dtype='类型')

`numpy.zeros(shape,dtupe = float,order = 'C')`&#x20;

| 参数    | 描述                                   |
| ----- | ------------------------------------ |
| shape | 数组形状                                 |
| dtype | 数据类型，可选                              |
| order | 'C' 用于 C 的行数组，或者 'F' 用于 FORTRAN 的列数组 |

```python
import numpy as np 
a = np.zeros(10)
print(a)

b = np.zeros((2,2), dtype = [('x', 'i4'), ('y', 'i4')])  
print(b)
```

### 4. zeros\_like(a,dtype=None,order='K',subok=True,shape=None)

| 参数    | 描述                                                         |
| ----- | ---------------------------------------------------------- |
| a     | 给定要创建相同形状的数组                                               |
|       |                                                            |
| dtype | 创建的数组的数据类型                                                 |
| order | 数组在内存中的存储顺序，可选值为 'C'（按行优先）或 'F'（按列优先），默认为 'K'（保留输入数组的存储顺序） |
| subok | 是否允许返回子类，如果为 True，则返回一个子类对象，否则返回一个与 a 数组具有相同数据类型和存储顺序的数组   |
| shape | b创建的数组的形状，如果不指定，则默认为 a 数组的形状。                              |

### 5. ones(shape,dtype = None,order='C')

创建一个数组，元素都为 1

### 6. ones\_like(a)

```
numpy.ones_like(a, dtype=None, order='K', subok=True, shape=None)
```

| 参数    | 描述                                                         |
| ----- | ---------------------------------------------------------- |
| a     | 给定要创建相同形状的数组                                               |
|       |                                                            |
| dtype | 创建的数组的数据类型                                                 |
| order | 数组在内存中的存储顺序，可选值为 'C'（按行优先）或 'F'（按列优先），默认为 'K'（保留输入数组的存储顺序） |
| subok | 是否允许返回子类，如果为 True，则返回一个子类对象，否则返回一个与 a 数组具有相同数据类型和存储顺序的数组   |
| shape | 创建的数组的形状，如果不指定，则默认为 a 数组的形状。                               |

### 7. eye()

创建一个正方形的 N\*N 的单位矩阵，对角线为 1，其余都为 0

### 二、从已有的数组创建数组

### 1.frombuffer()

numpy.frombuffer 用于实现动态数组。

numpy.frombuffer 接受 buffer 输入参数，以流的形式读入转化成 ndarray 对象。

```python
numpy.frombuffer(buffer, dtype = float, count = -1, offset = 0)pytho
```

| 参数     | 描述                    |
| ------ | --------------------- |
| buffer | 可以是任意对象，会以流的形式读入。     |
| dtype  | 返回数组的数据类型，可选          |
| count  | 读取的数据数量，默认为-1，读取所有数据。 |
| offset | 读取的起始位置，默认为0。         |

```python
import numpy as np 
 
s =  b'Hello World' 
a = np.frombuffer(s, dtype =  'S1')  
print (a)
```

### 三、从数值范围创建数组

### 1. **arange()**&#x20;

类似于 `range(start,stop,step,dtype)` ，在给定的间隔内返回均匀间隔的值

根据 start 与 stop 指定的范围以及 step 设定的步长，生成一个 ndarray

| 参数      | 描述                                   |
| ------- | ------------------------------------ |
| `start` | 起始值，默认为`0`                           |
| `stop`  | 终止值（不包含）                             |
| `step`  | 步长，默认为`1`                            |
| `dtype` | 返回`ndarray`的数据类型，如果没有提供，则会使用输入数据的类型。 |

```python
import numpy as np
print(np.arange(10))    # 返回0-9，整型
print(np.arange(10.0))  # 返回0.0-9.0，浮点型
print(np.arange(5,12))  # 返回5-11
print(np.arange(5.0,12,2))  # 返回5.0-12.0，步长为2

>>> 
[0 1 2 3 4 5 6 7 8 9]
[0. 1. 2. 3. 4. 5. 6. 7. 8. 9.]
[ 5  6  7  8  9 10 11]
[ 5.  7.  9. 11.]
```

### 2. linspace()

创建一个等差数列，返回在间隔(开始，停止)上计算的num个均匀间隔的样本

`numpy.linspace(start,stop,num=50,endpoint=True,retstep=False,dtype=None)`&#x20;

<table><thead><tr><th width="329.5">用法</th><th></th></tr></thead><tbody><tr><td>start</td><td>开始</td></tr><tr><td>stop</td><td>结束</td></tr><tr><td>num</td><td>生成样本数，默认 50</td></tr><tr><td>endpoint</td><td>如果为真，则停止是最后一个样本。否则不包括在内，默认是 True</td></tr><tr><td>retstep</td><td>如果为真，返回(样本，步骤)，其中步长是样本之间的间距</td></tr></tbody></table>

```python
import numpy as np
ar1 = np.linspace(2.0, 3.0, num=5)
ar2 = np.linspace(2.0, 3.0, num=5, endpoint=False)
ar3 = np.linspace(2.0, 3.0, num=5, retstep=True)
print(ar1,type(ar1))
print(ar2)
print(ar3,type(ar3))

>>> 
[2.   2.25 2.5  2.75 3.  ] <class 'numpy.ndarray'>
[2.  2.2 2.4 2.6 2.8]
(array([2.  , 2.25, 2.5 , 2.75, 3.  ]), 0.25) <class 'tuple'>
```

### 3. logspace()

numpy.logspace 函数用于创建一个于等比数列。

```
np.logspace(start, stop, num=50, endpoint=True, base=10.0, dtype=None)
```

| 参数         | 描述                                                  |
| ---------- | --------------------------------------------------- |
| `start`    | 序列的起始值为：base \*\* start                             |
| `stop`     | 序列的终止值为：base \*\* stop。如果`endpoint`为`true`，该值包含于数列中 |
| `num`      | 要生成的等步长的样本数量，默认为`50`                                |
| `endpoint` | 该值为 `true` 时，数列中中包含`stop`值，反之不包含，默认是True。           |
| `base`     | 对数 log 的底数。                                         |
| `dtype`    | `ndarray` 的数据类型                                     |
