# [Pandas](https://pandas.pydata.org)

便于操作的数据类 + 分析工具

- 安装：`pip install pandas`
- 使用：`import pandas as pd`

两个数据类型：
- Series：一维
- DataFrame：二维

各类操作：基本操作、运算操作、特征类操作、关联类操作

## NumPy 与 Pandas

NumPy | Pandas
-- | --
基础数据类型 | 扩展数据类型
关注数据的结构表达 | 关注数据的应用表达
维度：数据间关系 | **数据与索引间关系**

Pandas 更关注应用

## Series

一维的带“标签”（Index）的数组

### 创建

- 列表
- 标量值
- 字典
- ndarray

- `pd.Series(array, index_array)`
- `pd.Series(dict)`

索引没有对应值，为NaN Not a Number

### 操作

- 索引、切片：自定义和数字
- 字典操作
- 加减乘除（Index 对应）

特殊的切片：`s[s > 值]`

### .name

能给 Series 和 Index 加名字

## DataFrame

