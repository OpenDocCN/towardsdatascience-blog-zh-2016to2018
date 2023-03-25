# 在 Python 中提取和转换数据

> 原文：<https://towardsdatascience.com/extracting-and-transforming-data-in-python-63291f63d350?source=collection_archive---------8----------------------->

![](img/fcfc11b4a63659dc29a0446620531267.png)

[(Source)](https://unsplash.com/photos/ZGnC2gOvzKw)

## 为了从数据中获得洞察力，你必须对它稍加处理..

重要的是能够从数据帧中提取、过滤和转换数据，以便深入到真正重要的数据中。熊猫图书馆有许多技术使这一过程高效而直观。在今天的文章中，我将列出这些技术，并附有代码示例和一些解释。让我们开始吧。

在这篇文章中，我用随机数创建了一个样本数据帧来玩它。在本文的解释过程中，我们将使用这些数据作为例子。

```
import pandas as pd
import numpy as np
cols = ['col0', 'col1', 'col2', 'col3', 'col4']
rows = ['row0', 'row1', 'row2', 'row3', 'row4']
data = np.random.randint(0, 100, size=(5, 5))
df = pd.DataFrame(data, columns=cols, index=rows)df.head()**Out[2]: 
      col0  col1  col2  col3  col4
row0    24    78    42     7    96
row1    40     4    80    12    84
row2    83    17    80    26    15
row3    92    68    58    93    33
row4    78    63    35    70    95**
```

# 索引数据帧

为了从 pandas 数据帧中提取数据，我们可以使用直接索引或访问器。我们可以使用标签选择必要的行和列:

```
df['col1']['row1']**Out[3]: 4**
```

请注意这种索引的顺序:首先指定列标签，然后指定行。但事实是，数据集很少，而且很小，而在现实生活中，我们使用的机器要重得多。使用访问器— *来选择数据要好得多。锁定*和*。iloc* 。他们的区别在于*。loc* 接受标签，而*接受标签。iloc* —索引。同样，当我们使用访问器时，我们首先指定行，然后指定列。一开始我很难适应它——SQL 背景，你还能说什么..

![](img/976e1b03f91603fc0ac973eb46c91a6b.png)

因此，要使用访问器选择单个值，您需要执行以下操作:

```
df.loc['row4', 'col2']
**Out[4]: 35** df.iloc[4, 2]
**Out[5]: 35**
```

使用索引，我们可以从数据帧中选择单个值、系列或数据帧(抱歉，这是同义反复)。上面我已经展示了如何选择一个值。

要再选择几列，只需传递其标签的嵌套列表，DataFrame 将被返回:

```
df_new = df[['col1','col2']]
df_new.head(3)

**Out[6]: 
      col1  col2
row0    78    42
row1     4    80
row2    17    80**
```

如果您还想选择特定的行，添加它的索引，您将再次获得一个数据帧。这种技术被称为切片，下面会有更详细的介绍。

```
df_new = df[['col1','col2']][1:4]
df_new.head(3)

**Out[7]: 
      col1  col2
row1     4    80
row2    17    80
row3    68    58**
```

要选择一个系列，您必须选择包含所有行或一系列行的单个列。每一行代码都会产生相同的输出:

```
df['col0']
df.loc[:,'col0']
df.iloc[:, 0]

**Out[8]: 
row0    24
row1    40
row2    83
row3    92
row4    78
Name: col0, dtype: int32**
```

冒号意味着我们要选择所有行或所有列— *df.loc[:，:]* 或 *df.iloc[:，:]* 将返回所有值。慢慢地，我们进入了切片阶段——从数据中选择特定的范围。要对一个系列进行切片，您只需添加要使用其索引选择的一系列行:

```
df['col3'][2:5]

**Out[12]: 
row2    26
row3    93
row4    70
Name: col3, dtype: int32**
```

不要忘记 Python 中的范围——第一个元素被包含，第二个被排除。所以上面的代码将返回索引为 5、6、7、8 和 9 的行。索引从 0 开始。

![](img/76a1f3aeab2ff73ee6a03bc686b9ff30.png)

切片数据帧的工作方式相同。只有一个细微的差别。使用*时。loc* (标签)包括两个边框。例如，选择从标签“行 1”到标签“行 4”的行或从行索引 1 到索引 4 的行以及所有列:

```
df.loc['row1':'row4', :]
**Out[20]: 
      col0  col1  col2  col3  col4
row1    40     4    80    12    84
row2    83    17    80    26    15
row3    92    68    58    93    33
row4    78    63    35    70    95** df.iloc[1:4, :]
**Out[21]: 
      col0  col1  col2  col3  col4
row1    40     4    80    12    84
row2    83    17    80    26    15
row3    92    68    58    93    33**
```

上面的第一行代码选择了 row1、row2、row3 和 row4。而第二个—仅行 1、行 2 和行 3。下面再举几个例子。

选择从标签“列 1”到标签“列 4”或从列索引 1 到索引 4 的列以及所有行:

```
df.loc[:, 'col1':'col4']
**Out[22]: 
      col1  col2  col3  col4
row0    78    42     7    96
row1     4    80    12    84
row2    17    80    26    15
row3    68    58    93    33
row4    63    35    70    95** df.iloc[:, 1:4]
**Out[23]: 
      col1  col2  col3
row0    78    42     7
row1     4    80    12
row2    17    80    26
row3    68    58    93
row4    63    35    70**
```

选择从标签“行 1”到标签“行 4”或从行索引 1 到索引 4 的行，以及从标签“列 1”到标签“列 4”或从列索引 1 到索引 4 的列:

```
df.loc['row1':'row4', 'col1':'col4']
**Out[24]: 
      col1  col2  col3  col4
row1     4    80    12    84
row2    17    80    26    15
row3    68    58    93    33
row4    63    35    70    95** df.iloc[1:4,1:4] **Out[25]: 
      col1  col2  col3
row1     4    80    12
row2    17    80    26
row3    68    58    93**
```

使用列表选择不在范围内的特定列或行。

```
df.loc['row2':'row4', ['col1','col3']]
**Out[28]: 
      col1  col3
row2    17    26
row3    68    93
row4    63    70** df.iloc[[2,4], 0:4]
**Out[30]: 
      col0  col1  col2  col3
row2    83    17    80    26
row4    78    63    35    70**
```

# 过滤数据帧

过滤是一种更通用的工具，它根据数据本身的感兴趣的属性而不是索引或标签来选择数据的一部分。数据帧有几种过滤方法。所有这些方法的基本思想是布尔级数。在这个条件为真的情况下， *df['col1'] > 20* (我们假设 col1 的类型是 integer)将返回一个布尔序列。我将在这里输入。head()方法，所以不需要向上滚动来匹配数字。

```
**Out[2]: 
      col0  col1  col2  col3  col4
row0    24    78    42     7    96
row1    40     4    80    12    84
row2    83    17    80    26    15
row3    92    68    58    93    33
row4    78    63    35    70    95**
```

因此，要选择数据帧中 col1 的值大于 20 的部分，我们将使用以下代码:

```
df[df['col1'] > 20]
*# assigning variable also works*
condition = df['col1'] > 20
df[condition]

**Out[31]: 
      col0  col1  col2  col3  col4
row0    24    78    42     7    96
row3    92    68    58    93    33
row4    78    63    35    70    95**
```

我们可以使用标准的逻辑运算符(and — &，or — |，not — ~)来组合这些过滤器。请注意括号在这些操作中的用法。

```
df[(df['col1'] > 25) & (df['col3'] < 30)] # logical and
**Out[33]: 
      col0  col1  col2  col3  col4
row0    24    78    42     7    96** df[(df['col1'] > 25) | (df['col3'] < 30)] # logical or
**Out[34]: 
      col0  col1  col2  col3  col4
row0    24    78    42     7    96
row1    40     4    80    12    84
row2    83    17    80    26    15
row3    92    68    58    93    33
row4    78    63    35    70    95** df[~(df['col1'] > 25)] # logical not
**Out[35]: 
      col0  col1  col2  col3  col4
row1    40     4    80    12    84
row2    83    17    80    26    15**
```

## 处理 0 和 NaN 值

几乎所有的数据集都有零值或 NaN 值，我们肯定想知道它们在哪里。我们的比较特殊，所以我们会稍微修改一下:

```
df.iloc[3, 3] = 0
df.iloc[1, 2] = np.nan
df.iloc[4, 0] = np.nan
df['col5'] = 0
df['col6'] = np.NaN
df.head()

**Out[57]: 
      col0  col1  col2  col3  col4  col5  col6
row0  24.0    78  42.0     7    96     0   NaN
row1  40.0     4   NaN    12    84     0   NaN
row2  83.0    17  80.0    26    15     0   NaN
row3  92.0    68  58.0     0    33     0   NaN
row4   NaN    63  35.0    70    95     0   NaN**
```

要选择没有任何零值的列，我们可以使用*。all()* 方法(所有数据都存在):

```
df.loc[:, df.all()] **Out[43]: 
      col0  col1  col2  col4  col6
row0  24.0    78  42.0    96   NaN
row1  40.0     4   NaN    84   NaN
row2  83.0    17  80.0    15   NaN
row3  92.0    68  58.0    33   NaN
row4   NaN    63  35.0    95   NaN**
```

如果我们希望找到至少有一个非零(任意)值的列，这将有助于:

```
df.loc[:, df.any()]

**Out[47]: 
      col0  col1  col2  col3  col4
row0  24.0    78  42.0     7    96
row1  40.0     4   NaN    12    84
row2  83.0    17  80.0    26    15
row3  92.0    68  58.0     0    33
row4   NaN    63  35.0    70    95**
```

要选择具有任何 NaN 的列:

```
df.loc[:, df.isnull().any()]

**Out[48]: 
      col0  col2  col6
row0  24.0  42.0   NaN
row1  40.0   NaN   NaN
row2  83.0  80.0   NaN
row3  92.0  58.0   NaN
row4   NaN  35.0   NaN**
```

选择不带 nan 的色谱柱:

```
df.loc[:, df.notnull().all()]

**Out[49]: 
      col1  col3  col4  col5
row0    78     7    96     0
row1     4    12    84     0
row2    17    26    15     0
row3    68     0    33     0
row4    63    70    95     0**
```

我们可以删除那些包含 nan 的行，但是这是一个危险的游戏——删除通常不是一个解决方案。您必须理解您的数据，并明智地处理这样的行。我警告过你。

![](img/1fd4635c0c025b9b2fa7a46e4c90bab1.png)

你确定你想知道吗？好..😀

```
df.dropna(how='all', axis=1) # if all values in a column are NaN it will be dropped
**Out[69]: 
      col0  col1  col2  col3  col4  col5
row0  24.0    78  42.0     7    96     0
row1  40.0     4   NaN    12    84     0
row2  83.0    17  80.0    26    15     0
row3  92.0    68  58.0     0    33     0
row4   NaN    63  35.0    70    95     0** df.dropna(how='any', axis=1) # if any value in a row is NaN it will be dropped
**Out[71]: 
      col1  col3  col4  col5
row0    78     7    96     0
row1     4    12    84     0
row2    17    26    15     0
row3    68     0    33     0
row4    63    70    95     0**
```

这种方法不会修改原始数据帧，因此要继续处理过滤后的数据，必须将其分配给新的数据帧或重新分配给现有的数据帧

```
df = df.dropna(how='any', axis=1)
```

过滤的美妙之处在于，我们实际上可以根据一列的值来选择或修改另一列的值。例如，我们可以从 col1 中选择值，其中 col2 大于 35，并通过给每个值加 5 来更新这些值:

```
*# Find a column based on another*
df['col1'][df['col2'] > 35]
**Out[74]: 
row0    78
row2    17
row3    68
Name: col1, dtype: int32**

*# Modify a column based on another*
df['col1'][df['col2'] > 35] += 5
df['col1']
**Out[77]: 
row0    83
row1     4
row2    22
row3    73
row4    63
Name: col1, dtype: int32**
```

这让我们进入下一部分——

# 转换数据帧

一旦我们选择或过滤了我们的数据，我们想以某种方式转换它。最好的方法是使用继承到 DataFrames 或 numpy universal funcs 的方法，它们按元素方式转换整列数据。熊猫*就是例子。floordiv()* 函数(来自文档:
‘data frame 和其他元素的整数除法’)或 numpy 的*。floor_divide()* (doc:'返回小于或等于输入的除法的最大整数。').

如果这些函数不可用，我们可以编写自己的函数并与*一起使用。应用()*方法。

```
def some_func(x): 
    return x * 2df.apply(some_func) -- *# update each entry of a DataFrame without any loops**# lambda also works* 
df.apply(lambda n: n*2) -- *# the same*
```

这些函数不返回转换，所以我们必须显式地存储它:

```
df['new_col'] = df['col4'].apply(lambda n: n*2)
df.head()

**Out[82]: 
      col0  col1  col2  col3  col4  col5  col6  new_col
row0  24.0    83  42.0     7    96     0   NaN      192
row1  40.0     4   NaN    12    84     0   NaN      168
row2  83.0    22  80.0    26    15     0   NaN       30
row3  92.0    73  58.0     0    33     0   NaN       66
row4   NaN    63  35.0    70    95     0   NaN      190**
```

如果 index 是一个字符串，它有一个*。允许我们一次修改整个索引的访问器:*

```
df.index.str.upper()
**Out[83]: Index(['ROW0', 'ROW1', 'ROW2', 'ROW3', 'ROW4'], dtype='object')**
```

同样，我们不能使用*。对索引应用()*方法—它的替代方法是*。map()*

```
df.index = df.index.map(str.lower)
**Out[85]: Index(['row0', 'row1', 'row2', 'row3', 'row4'], dtype='object')**
```

但是*。map()* 也可以用在列上。例如:

```
*# Create the dictionary: red_vs_blue*
red_vs_blue = {0:'blue', 12:'red'}

*# Use the dictionary to map the 'col3' column to the new column df['color']*
df['color'] = df['col3'].map(red_vs_blue)
df.head()

**Out[92]: 
      col0  col1  col2  col3  col4  col5  col6  new_col color
row0  24.0    83  42.0     7    96     0   NaN      192   NaN
row1  40.0     4   NaN    12    84     0   NaN      168   red
row2  83.0    22  80.0    26    15     0   NaN       30   NaN
row3  92.0    73  58.0     0    33     0   NaN       66  blue
row4   NaN    63  35.0    70    95     0   NaN      190   NaN**
```

序列和数据帧上的算术运算直接起作用。下面的表达式将创建一个新列，其中索引为 *n* 的每个值是来自*‘col 3’*和*‘col 7’的索引为 *n* 的值的总和。*

```
df['col7'] = df['col3'] + df['col4'] 
df.head()

**Out[94]: 
      col0  col1  col2  col3  col4  col5  col6  new_col color  col7
row0  24.0    83  42.0     7    96     0   NaN      192   NaN   103
row1  40.0     4   NaN    12    84     0   NaN      168   red    96
row2  83.0    22  80.0    26    15     0   NaN       30   NaN    41
row3  92.0    73  58.0     0    33     0   NaN       66  blue    33
row4   NaN    63  35.0    70    95     0   NaN      190   NaN   165**
```

这是文章的第二个版本，因为第一个完全是一团糟——代码中有错误，没有例子，也没有其他东西。感谢反馈，我又看了一遍这篇文章，我觉得现在看起来好多了。我在这里用代码片段和例子讲述了用 Python 转换和提取数据的基础知识，希望对刚开始涉足这一领域的人有用。

同时，热爱数据科学，多笑笑。我们必须乐观，因为我们拥有 21 世纪最性感的工作😀

*原载于*[*sergilehkyi.com*](http://sergilehkyi.com/extracting-and-transforming-data-in-python/)*。*