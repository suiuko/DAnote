# 对象

## ➡️ nadarry 对象

NUMPY 定义了一个 N 维数组对象，他是一个一系列相同类型元素组成的数组集合

其对象采用了数组的索引机制，将数组中的每个元素映射到内存块上。

ndarray 内部由以下内容组成：

* 一个指向数据（内存或内存映射文件中的一块数据）的指针。
* 数据类型或 dtype，描述在数组中的固定大小值的格子。
* 一个表示数组形状（shape）的元组，表示各维度大小的元组。
* 一个跨度元组（stride），其中的整数指的是为了前进到当前维度下一个元素需要"跨过"的字节数。

ndarray 的内部结构:

<figure><img src="../.gitbook/assets/ndarray1.png" alt=""><figcaption></figcaption></figure>

