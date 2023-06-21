# 纬度操作

## 1. 视图变维（数据共享）&#x20;

### reshape() 和 ravel()

`reshape(页，行，列)`  不会改变原来的数组结构

`ravel() 变为 1 维数组`

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

## 2. 复制变维（数据独立）flatten()

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
