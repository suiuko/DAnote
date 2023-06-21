# 数组属性

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

```python
c = np.arange(1,19)
c.shape = (3,2,3) #(页，行，列)
print(c)
```

### 2. 元素的类型： np.ndarray.dtype

[#ji-ben-shu-ju-lei-xing](shu-ju-lei-xing.md#ji-ben-shu-ju-lei-xing "mention") 👈有基本的数据类型，可以通过`dtype` 来查看或者更改数据类型

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

### 3. 数组元素的个数：np.ndarray.size

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

观察维度，size，len 的区别

`print(ary2.shape,ary2.size,len(ary2))`

shape输出(2, 4) ； size输出 8 ； len输出 2

### 4. 数组元素索引（下标）index操作

数组对象\[..., 页号,行号,列号]

下标从 0 开始，到数组len-1结束

### 5. 数组的秩 .ndim&#x20;

输出数组的秩，也称 维度的个数

### 6. 修改数据类型 .astype(' ')

`b=a.astype('float32')` 对其数据类型进行修改
