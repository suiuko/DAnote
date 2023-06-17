# nadarry

## nadarry 对象

NUMPY 定义了一个 N 维数组对象，他是一个一系列相同类型元素组成的数组集合

其对象采用了数组的索引机制，将数组中的每个元素映射到内存块上。

ndarray 内部由以下内容组成：

* 一个指向数据（内存或内存映射文件中的一块数据）的指针。
* 数据类型或 dtype，描述在数组中的固定大小值的格子。
* 一个表示数组形状（shape）的元组，表示各维度大小的元组。
* 一个跨度元组（stride），其中的整数指的是为了前进到当前维度下一个元素需要"跨过"的字节数。

ndarray 的内部结构:

<figure><img src="../.gitbook/assets/ndarray1.png" alt=""><figcaption></figcaption></figure>

## array 创建数组

```python
numpy.array(object,dtype = None, copy = True, order = None, subok = False, ndmin = 0)
```

<table><thead><tr><th width="136">参数</th><th></th></tr></thead><tbody><tr><td>object</td><td>表示一个数组序列</td></tr><tr><td>dtype</td><td>可选参数，通过他可以更改数组的数据类型</td></tr><tr><td>copy</td><td>可选参数，当数据源是ndarray时表示数组能否被复制，默认 T</td></tr><tr><td>order</td><td>可选参数，以哪种内存布局创建数组。可选值：C(行序列)/F(列序列)/A(默认)</td></tr><tr><td>ndmin</td><td>可选参数，用于指定数组的纬度</td></tr><tr><td>subok</td><td>可选参数，类型为 bool 值，默认 false。为 True：使用 object 的内部数据类型；False：使用 object 数组的数据类型。</td></tr></tbody></table>

### 用法

#### np.array(初始值0，结束值-1，步长)

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

#### np.zeros(数组元素个数, dtype='类型')

```python
import numpy as np 
a = np.zeros(10)
print(a)
```

`zeros_like(a)` 函数能做出像a 一样纬度的 0 矩阵

## ndarray 对象属性的基本操作

### 1. 数组的维度：np.ndarry.shape

```python
import numpy as np
ary = np.array([1,2,3,4,5,6])
print(type(ary),ary,ary.shape)

# 二维数组

ary1 = np.array([
    [1,2,3,4],
    [5,6,7,8]
])
print(type(ary1),ary1,ary1.shape)

>>> <class 'numpy.ndarray'> [1 2 3 4 5 6] (6,)

>>> <class 'numpy.ndarray'> [[1 2 3 4]
 [5 6 7 8]] (2, 4)
```

### 元素的类型： np.ndarray.dtype

<pre class="language-python"><code class="lang-python">import numpy as np
ary3 = np.array([1,2,3,4,5,6])
print(type(ary),ary,ary.dtype)

# 转换ary 元素的类型

ary4 = ary.astype(float)
print(type(ary4),ary4,ary4.dtype)

ary5 = ary.astype(str)
print(type(ary5),ary5,ary5.dtype)

>>> &#x3C;class 'numpy.ndarray'> [1 2 3 4 5 6] int64
>>> &#x3C;class 'numpy.ndarray'> [1. 2. 3. 4. 5. 6.] float64
<strong>>>> &#x3C;class 'numpy.ndarray'> ['1' '2' '3' '4' '5' '6'] &#x3C;U21
</strong></code></pre>

### 数组元素的个数：np.ndarray.size

```python
import numpy as np
ary2 = np.array([
    [1,2,3,4],
    [5,6,7,8]
])
# 观察维度，size, len 的区别
print(ary2.shape,ary2.size,len(ary2))
>>> (2, 4) 8 2
```

### 数组元素索引（下标）

数组对象\[..., 页号,行号,列号]

下标从 0 开始，到数组len-1结束

