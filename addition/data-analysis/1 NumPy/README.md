# NumPy

`NumPy`是一个开源的Python科学计算基础库，包含：
- 一个强大的N维数组对象 `ndarray`
- 广播功能函数
- 整合C/C++/Fortran代码的工具
- 线性代数、傅里叶变换、随机数生成等功能

`NumPy`是`SciPy`、`Pandas`等数据处理或科学计算库的基础

完全是重学线性代数

## 维度

维度：一组数据的组织形式
- 形成特定的关系
- 表达数据含义

例子
```
一维
────→
 3.1413, 3.1398, 3.1404, 3.1401, 3.1349, 3.1376

二维
┌───→
│ 3.1398, 3.1349, 3.1376
↓ 3.1413, 3.1404, 3.1401
```

### 一维数据

一维数据由对等关系的有序或无序数据构成，采用线性方式组织

对应列表、数组和集合等概念
- 列表：元素类型不同
- 数组：元素类型相同

### 二维数据

二维数据由多个一维数据构成，是一维数据的组合形式

表格是典型的二维数据
- 其中，表头是二维数据的一部分

### 多维数据

多维数据由一维或二维数据在新维度上扩展形成

大学排名（二维） 再增加个时间维度

### 高维数据

高维数据仅利用最基本的二元关系展示数据间的复杂结构

键值对
```json
{
    "firstName" : "Tian" ,
    "lastName" : "Song" ,
    "address" : {
        "streetAddr" : "中关村南大街5号" ,
        "city" : "北京市" ,
        "zipcode" : "100081"
    } ,
    "prof" : [ "Computer System" , "Security" ]
}
```

### Python 表示

- 一维
    - 无序：set ：`{3.1349, 3.1398, 3.1376}`
    - 有序：list ：`[3.1398, 3.1349, 3.1376]`
- 二维：list
    - `[ [3.1398, 3.1349, 3.1376], [3.1413, 3.1404, 3.1401] ]`
- 多维：list
- 高维：dict 或 数据表示格式（XML，JSON，YAML）

## NumPy

表示N维数据对象 ndarray

优点：
- 数组对象可以去掉元素间运算所需的循环，使一维向量更像单个数据
- 设置专门的数组对象，经过优化，可以提升这类应用的运算速度
    - 观察：科学计算中，一个维度所有数据的类型往往相同
- 数组对象采用相同的数据类型，有助于节省运算和存储空间

### 例子 计算A²+B³，其中，A和B是一维数组
```python
a = [0, 1, 2, 3, 4]
b = [9, 8, 7, 6, 5]

result = []

for i in range(len(a)):
    result.append(a[i]**2 + b[i]**3)

print(result) # [729, 513, 347, 225, 141]
```

ndarray
```python
import numpy as np

a = np.array([0, 1, 2, 3, 4])
b = np.array([9, 8, 7, 6, 5])

result_np = a**2 + b**3

print(result_np) # [729 513 347 225 141]
```

## ndarray

`ndarray` 是一个多维数组对象，由两部分构成：
- 实际的数据
- 描述这些数据的元数据（数据维度、数据类型等）

ndarray数组一般要求所有元素类型相同（同质），数组下标从0开始

概念：
- 轴(axis): 保存数据的维度；
- 秩(rank)：轴的数量。

生成：`np.array()`

### 概述

#### 属性

- `.ndim` 秩，即轴的数量或维度的数量
- `.shape` ndarray对象的尺度，对于矩阵，n行m列
- `.size` ndarray对象元素的个数，相当于`.shape` 中n*m的值
- `.dtype` ndarray对象的元素类型
- `.itemsize` ndarray对象中每个元素的大小，以字节为单位

#### 元素类型

- int、float 与正常的语言（C、C++、Rust）相同
- complex 复数类型
    - `complex64` 实部和虚部都是32位浮点数
    - `complex128` 实部和虚部都是64位浮点数

ndarray为什么要支持这么多种元素类型？

运行效率+内存分配的问题
- 科学计算涉及数据较多，对存储和性能都有较高要求
- 对元素类型精细定义，有助于NumPy合理使用存储空间并优化性能
- 对元素类型精细定义，有助于程序员对程序规模有合理评估

#### 非同质的ndarray对象

非同质ndarray对象无法有效发挥NumPy优势，尽量避免使用

```py
import numpy as np

x = np.array([[0,1,2,3,4], 
              [9,8,7,6]])

print(x)
print("x.ndim\t\t{}".format(x.ndim))
print("x.shape\t\t{}".format(x.shape))
print("x.size\t\t{}".format(x.size))
print("x.dtype\t\t{}".format(x.dtype))
print("x.itemsize\t{}".format(x.itemsize))

# Output:
# [list([0, 1, 2, 3, 4]) list([9, 8, 7, 6])]
# x.ndim		1
# x.shape		(2,)
# x.size		2
# x.dtype		object
# x.itemsize	8
```

### 创建

- 从Python中的列表、元组等类型创建ndarray数组
- 使用NumPy中函数创建ndarray数组，如：arange, ones, zeros 等
- 从字节流（raw bytes）中创建ndarray数组
- 从文件中读取特定格式，创建ndarray数组

#### Python 列表、元组

```py
x = np.array(list/tuple)
x = np.array(list/tuple, dtype=np.float32)
```

当np.array()不指定dtype时，NumPy将根据数据情况关联一个dtype类型

```py
import numpy as np

x = np.array([0, 1, 2, 3]) # list
print(x)
# [0 1 2 3]

x = np.array((0, 1, 2, 3)) # tuple
print(x)
# [0 1 2 3]

x = np.array([[1,2], [9,8], (0.1, 0.2)]) # 混合
print(x)
# [[1.  2. ]
#  [9.  8. ]
#  [0.1 0.2]]
```

#### ndarray 生成 函数

如：arange, ones, zeros 等

- `np.arange(n)` 类似range()函数，返回ndarray类型，元素从0到n‐1
- `np.ones(shape)` 根据shape生成一个全1数组，shape是元组类型
- `np.zeros(shape)` 根据shape生成一个全0数组，shape是元组类型
- `np.full(shape,val)` 根据shape生成一个数组，每个元素值都是val
- `np.eye(n)` 创建一个正方的n*n单位矩阵，对角线为1，其余为0

默认生成浮点数类型

xx_like ：根据已有数组的形状生成一个数组
- `np.ones_like(a)` 根据数组a的形状生成一个全1数组
- `np.zeros_like(a)` 根据数组a的形状生成一个全0数组
- `np.full_like(a,val)` 根据数组a的形状生成一个数组，每个元素值都是val

其他
- `np.linspace()` 根据起止数据等间距地填充数据，形成数组
- `np.concatenate()` 将两个或多个数组合并成一个新的数组

例子见`1.3 build-ndarray.ipynb`

### ndarray数组的变换

#### 维度

- `.reshape(shape)` 不改变数组元素，返回一个shape形状的数组，原数组不变
- `.resize(shape)` 与`.reshape()`功能一致，但修改原数组
- `.swapaxes(ax1,ax2)` 将数组n个维度中两个维度进行调换
- `.flatten()` 对数组进行降维，返回折叠后的一维数组，原数组不变

！没返回值的函数，一般改变原数组

#### 类型

`.astype(new_type)`

#### 转换为 Python list

`.tolist()`

### 索引、切片

一维：与Python的列表类似
- 索引 `ndarray[索引]`
- 切片 `ndarray[开始:结束(不含):步长]`

多维：方法相同，不同维度用逗号分隔
- 索引 `ndarray[索引1, 索引2, 索引3 ...]`
    - `a[1,2,3]`
- 切片 `ndarray[开始1:结束(不含)1:步长1, :, ::步长]`
    - `a[:, 1:3, ::2]`

### 运算

#### 标量

数组与标量计算为：数组中的每个元素与该标量进行计算

一元函数 | 说明
-- | --
`np.rint(x)`  | 计算数组各元素的四舍五入值
`np.modf(x)`  | 将数组各元素的小数和整数部分以两个独立数组形式返回
`np.cos(x)` `np.cosh(x)` |
`np.sin(x)` `np.sinh(x)` | 计算数组各元素的普通型和双曲型三角函数
`np.tan(x)` `np.tanh(x)` |
`np.exp(x)` | 计算数组各元素的指数值
`np.sign(x)` | 计算数组各元素的符号值，1(+), 0, ‐1(‐)

二元 | 说明
--|--
`+ - * / **` | 两个数组各元素进行对应运算
`np.maximum(x,y) np.fmax()` | 元素级的最大值计算
`np.minimum(x,y) np.fmin()` | 元素级的最小值计算
`np.mod(x,y)` | 元素级的模运算
`np.copysign(x,y)` | 将数组y中各元素值的符号赋值给数组x对应元素
`> < >= <= == !=` | 算术比较，产生布尔型数组

## 文件读写

## csv

CSV (Comma‐Separated Value, 逗号分隔值)

`np.savetxt(frame, array, fmt='%.18e', delimiter=None)`
- frame : 文件、字符串或产生器()，可以是.gz或.bz2的压缩文件
- array : 存入文件的数组
- fmt : 写入文件的格式，例如：%d %.2f %.18e
- delimiter : 分割字符串，默认是任何空格

`np.loadtxt(frame, dtype=np.float, delimiter=None， unpack=False)`
- frame : 文件、字符串或产生器，可以是.gz或.bz2的压缩文件
- dtype : 数据类型，可选
- delimiter : 分割字符串，默认是任何空格
- unpack : 如果True，读入属性将分别写入不同变量

局限性：只能一二维

## 多维

写入的文件里没有维度信息，读取的时候要`reshape((对应结构))`

`a.tofile(frame, sep='', format='%s')`
- frame : 文件、字符串
- sep : 数据分割字符串，如果是空串，写入文件为二进制
- format : 写入数据的格式

`np.fromfile(frame, dtype=float, count=‐1, sep='')`
- frame : 文件、字符串
- dtype : 读取的数据类型
- count : 读入元素个数，‐1表示读入整个文件
- sep : 数据分割字符串，如果是空串，写入文件为二进制

### NumPy自定义格式

`np.save(fname, array) 或 np.savez(fname, array)`
- fname : 文件名，以.npy为扩展名，压缩扩展名为.npz
- array : 数组变量

`np.load(fname)`
- fname : 文件名，以.npy为扩展名，压缩扩展名为.npz

## 随机数

### 按值产生数组

函数 | 说明
-- | --
`rand(d0,d1,..,dn)` | 根据d0‐dn创建随机数数组，浮点数，[0,1)，均匀分布
`randn(d0,d1,..,dn)` | 根据d0‐dn创建随机数数组，标准正态分布
`randint(low[,high,shape])` | 根据shape创建随机整数或整数数组，范围是[low, high)
`seed(s)` | 随机数种子，s是给定的种子值

### 打乱数组，抽取元素

函数 | 说明
-- | --
`shuffle(a)` | 根据数组a的第1轴进行随排列，改变数组x
`permutation(a)` | 根据数组a的第1轴产生一个新的乱序数组，不改变数组x
`choice(a[,size,replace,p])` | 从一维数组a中以概率p抽取元素，形成size形状新数组 replace表示是否可以重用元素，默认为True，使用重复元素

### 生成对应分布的数组

函数 | 说明
-- | --
`uniform(low,high,size)` | 产生具有均匀分布的数组,low起始值,high结束值
`normal(loc,scale,size)` | 产生具有正态分布的数组,loc均值,scale标准差
`poisson(lam,size)` | 产生具有泊松分布的数组,lam随机事件发生率
