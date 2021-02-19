# 个人备忘录

## pypi 镜像

`pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple`

## format()

| :  |   <填充>  |   <对齐> | <宽度>|  <,>  |   <.>     |         <类型>
|---:|:---------:| :------: |------|:-----:|:---------:|:------------------------- 
|引导|  用于     |  < 左对齐 |      | 千分位|  小数精度  |   整数类型 b, c, d, o, x, X
|符号|  填充的   |  > 右对齐 |      | 间隔符|    or     |      浮点数类型 e, E, f, %
|   |  单个字符 |   ^ 居中 |      |      |  最大输出长度|

## list comprehension 列表推导式

- 返回一个新 list
- `[表达式       for in        if 条件]`

三大块：
1. 能每次返回值的表达式
2. for循环，确定循环次数
    - 循环可以嵌套
3. if 满足条件，才将表达式内的值

可以换行，增强可读性

```py
flattened = [
    i
    for row in matrix
    for i in row
]
```