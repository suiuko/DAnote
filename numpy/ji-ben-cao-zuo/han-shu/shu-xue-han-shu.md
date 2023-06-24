# 数学函数

## 三角函数

NumPy 提供了标准的三角函数：sin()、cos()、tan()

np.degrees(inv) 来查看角度单位

## 舍入函数

### numpy.around()&#x20;

函数返回指定数字的四舍五入值。

```
numpy.around(a,decimals)
```

* a: 数组
* decimals: 舍入的小数位数。 默认值为0。 如果为负，整数将四舍五入到小数点左侧的位置

### numpy.floor()

numpy.floor() 返回小于或者等于指定表达式的最大整数，即向下取整

### numpy.ceil()

numpy.ceil() 返回大于或者等于指定表达式的最小整数，即向上取整

```python
import numpy as np
 
a = np.array([-1.7,  1.5,  -0.2,  0.6,  10])  
print  ('提供的数组：')
print (a)
print ('\n')
print ('修改后的数组：')
print (np.ceil(a))

>>>
提供的数组：
[-1.7  1.5 -0.2  0.6 10. ]


修改后的数组：
[-1.  2. -0.  1. 10.]
```

