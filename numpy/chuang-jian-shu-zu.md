# 创建数组

## nadarry 对象

NUMPY 定义了一个 N 维数组对象，他是一个一系列相同类型元素组成的数组集合

其对象采用了数组的索引机制，将数组中的每个元素映射到内存块上。

## array 创建数组

```python
numpy.array(object,dtype = None, copy = True, order = None, subok = False, ndmin = 0)
```

<table><thead><tr><th width="136">参数</th><th></th></tr></thead><tbody><tr><td>object</td><td>表示一个数组序列</td></tr><tr><td>dtype</td><td>可选参数，通过他可以更改数组的数据类型</td></tr><tr><td>copy</td><td>可选参数，当数据源是ndarray时表示数组能否被复制，默认 T</td></tr><tr><td>order</td><td>可选参数，以哪种内存布局创建数组。可选值：C(行序列)/F(列序列)/A(默认)</td></tr><tr><td>ndmin</td><td>可选参数，用于指定数组的纬度</td></tr><tr><td>subok</td><td>可选参数，类型为 bool 值，默认 false。为 True：使用 object 的内部数据类型；False：使用 object 数组的数据类型。</td></tr></tbody></table>

### 用法

#### 基础用法

array(初始值，结束值-1，步长)

<pre class="language-python"><code class="lang-python"># 迭代对象
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

</code></pre>
