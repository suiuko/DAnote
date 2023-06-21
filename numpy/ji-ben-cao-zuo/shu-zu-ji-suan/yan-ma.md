---
description: ndarray数组的掩码操作
---

# 掩码操作

### MASK 掩码

掩码操作就是 创建一个`mask` 数组

mask = \[True, Flase] 输出原来数组中，True组成的数组

```python
import numpy as np
a = np.arange(1,10)
mask =[True,False,True,False,True,False,True,False,True]
print(a[mask])

>>>
[1 3 5 7 9]
```

```python
"""mask掩码 100 的三倍数"""
import numpy as np
a = np.arange(1,100)
# print(a[a%3 == 0])
mask = a%3 == 0 # mask 为 True 和 False 的数组
print(a[mask])

>>>
[ 3  6  9 12 15 18 21 24 27 30 33 36 39 42 45 48 51 54 57 60 63 66 69 72
 75 78 81 84 87 90 93 96 99]
```

### 基于索引的掩码

```python
import numpy as np
names = np.array(['apple','Mate30','mi','oppo','vivo'])
rank = [1,0,3,4,2]
print(names[rank])

>>>
['Mate30' 'apple' 'oppo' 'vivo' 'mi']
```
