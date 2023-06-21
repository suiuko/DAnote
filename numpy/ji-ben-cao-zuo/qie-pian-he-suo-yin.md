---
description: ndarray数组切片操作
---

# 切片和索引操作

## 1. 一维数组切片

&#x20;数组对象切片的参数设置与列表切面参数类似

**`数组对象[起始位置:终止位置:步长]`**&#x20;

`步长+`：默认切从首到尾\
`步长-` ：默认切从尾到头

<mark style="color:yellow;">切的范围为：\[起始位置：终止位置)</mark> &#x20;

```python
import numpy as np
a = np.arange(1,10)
print(a) # 123456789
print(a[:3]) # 123
print(a[3:6]) # 456
print(a[6:]) # 789
print(a[::-1]) #987654321
print(a[:-4:-1]) #987
print(a[-4:-7:-1]) #654
print(a[-7::-1]) # 321
```

## 2. 多维数组

**数组对象\[行操作，列操作]**

**数组对象\[ 1 维度, 2 维度, 3 维度]**

```python
import numpy as np
a = np.arange(1,28)
a.resize(3,3,3)
print(a)

print("======")
# 切出 1 页
print("切出 1 页")
print(a[0,:,:])

# 切出 所有页的第一行
print("所有页的第一行")
print(a[:,1,:])

# 切出 0 页的 1 行 1 列
print("切出 0 页的 1 行 1 列")
print(a[0,:,1])
```
