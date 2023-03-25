# 让我们谈谈 NumPy——针对数据科学初学者

> 原文：<https://towardsdatascience.com/lets-talk-about-numpy-for-datascience-beginners-b8088722309f?source=collection_archive---------3----------------------->

![](img/494e4aa4d58031f4ba858efa792d255a.png)

Numpy For Beginners

[NumPy](http://www.numpy.org/) (数值 Python)是 Python 中的线性代数库。它是一个非常重要的库，几乎每个数据科学或机器学习 Python 包，如 SciPy(科学 Python)、Mat plot lib(绘图库)、Scikit-learn 等都在一定程度上依赖于它。

NumPy 对于在数组上执行数学和逻辑运算非常有用。它为 Python 中的 n 数组和矩阵操作提供了大量有用的特性。

本课程涵盖了作为数据科学初学者需要了解的关于 NumPy 的基础知识。其中包括如何创建 NumPy 数组、使用广播、访问值和操作数组。更重要的是，您将了解 NumPy 优于 Python 列表的优点，包括:更紧凑、读写条目更快、更方便、更高效。

在本课程中，我们将使用 [Jupyter](http://jupyter.org/) 笔记本作为我们的编辑器。

我们走吧！

## **安装 NumPy**

如果您有 [Anaconda](http://anaconda.com/) ，您可以简单地从您的终端或命令提示符安装 NumPy，使用:

`conda install numpy`

如果您的计算机上没有 Anaconda，请使用以下命令从终端安装 NumPy:

`pip install numpy`

一旦你安装了 NumPy，启动你的 Jupyter 笔记本并开始使用。让我们从 NumPy 数组开始

## NumPy 数组

NumPy 数组只是一个包含相同类型值的网格。NumPy 数组有两种形式:向量和矩阵。向量是严格的一维(1-d)数组，而矩阵是多维的。在某些情况下，矩阵仍然只能有一行或一列。

让我们从在您的 Jupyter 笔记本中导入 NumPy 开始。

```
import numpy as np
```

**从 python 列表创建 numpy 数组**

假设我们有一个 Python 列表:

```
my_list = [1, 2, 3, 4, 5]
```

我们可以简单地创建一个名为 *my_numpy_list* 的 NumPy 数组，并显示结果:

```
my_numpy_list = np.array(my_list)
my_numpy_list  *#This line show the result of the array generated*
```

我们刚刚做的是将 python 列表转换成一维数组。为了得到一个二维数组，我们必须转换一个列表，如下所示。

```
second_list = [[1,2,3], [5,4,1], [3,6,7]]new_2d_arr = np.array(second_list)
new_2d_arr  *#This line show the result of the array generated*
```

我们已经成功地创建了一个有 3 行 3 列的二维数组。

**使用 arange()内置函数创建 NumPy 数组。**

类似于 python 内置的 range()函数，我们将使用 arange()创建一个 NumPy 数组。

```
my_list = np.arange(10)*#OR*my_list = np.arange(0,10)
```

这将生成从索引 0 到 10 的 10 位数的值。

需要注意的是，arange()函数也可以接受 3 个参数。第三个参数表示操作的步长。例如，要获得从 0 到 10 的所有偶数，只需添加如下所示的步长 2。

```
my_list = np.arange(0,11,2)
```

我们也可以生成一个由七个零组成的一维数组。

```
my_zeros = np.zeros(7)
```

我们也可以生成一个由五个一组成的一维数组。

```
my_ones = np.ones(5)
```

类似地，我们可以生成具有 3 行 5 列的二维零数组

```
two_d = np.zeros((3,5))
```

**使用 linspace()内置函数创建 NumPy 数组。**

函数的作用是:返回指定区间内均匀分布的数字。假设我们想要从 1 到 3 的 15 个均匀间隔的点，我们可以很容易地使用:

```
lin_arr = np.linspace(1, 3, 15)
```

这给了我们一个一维向量。

不像 arange()函数将第三个参数作为步数，linspace()将第三个参数作为要创建的数据点的数量。

**在 NumPy 中创建一个单位矩阵**

处理线性代数时，单位矩阵非常有用。通常，是一个二维方阵。这意味着行数等于列数。关于单位矩阵要注意的一个独特的事情是对角线是 1，其他的都是 0。单位矩阵通常只有一个参数。下面是如何创建一个。

```
my_matrx = np.eye(6)    *#6 is the number of columns/rows you want*
```

**在 NumPy 中生成一个随机数数组**

我们可以使用 rand()、randn()或 randint()函数生成一个随机数数组。

*   使用 random.rand()，我们可以生成一个形状的随机数数组，从 0 到 1 的均匀分布传递给它。

例如，假设我们想要一个从 0 到 1 均匀分布的 4 个对象的一维数组，我们可以这样做:

```
my_rand = np.random.rand(4)
```

如果我们想要一个 5 行 4 列的二维数组:

```
my_rand = np.random.rand(5, 4)
my_rand
```

*   使用 randn()，我们可以从以 0 为中心的标准、正态或高斯分布中生成随机样本。例如，让我们生成 7 个随机数:

```
my_randn = np.random.randn(7)
my_randn
```

当你绘图时，结果会给我们一个正态分布曲线。

类似地，要生成 3 行 5 列的二维数组，请执行以下操作:

```
np.random.randn(3,5)
```

*   最后，我们可以使用 randint()函数生成一个整数数组。randint()函数最多可以接受 3 个参数；数组的下限(包括)、上限(不包括)和大小。

```
np.random.randint(20) *#generates a random integer exclusive of 20*np.random.randint(2, 20) *#generates a random integer including 2 but excluding 20*np.random.randint(2, 20, 7) *#generates 7 random integers including 2 but excluding 20*
```

**将一维数组转换成二维**

首先，我们生成一个由 25 个随机整数组成的一维数组

```
arr = np.random.rand(25)
```

然后使用 shape()函数将其转换为二维数组

```
arr.reshape(5,5)
```

注意:reshape()只能转换成相等数量的行和列，并且必须等于等于元素的数量。在上面的例子中， **arr** 包含 25 个元素，因此只能调整为 5X5 矩阵。

**定位 NumPy 数组的最大值和最小值**

使用 max()和 min()，我们可以获得数组中的最大值或最小值。

```
arr_2 = np.random.randint(0, 20, 10) arr_2.max() *#This gives the highest value in the array* arr_2.min() *#This gives the lowest value in the array*
```

使用 argmax()和 argmin()函数，我们可以定位数组中最大值或最小值的索引。

```
arr_2.argmax() #This shows the index of the highest value in the array 
arr_2.argmin() #This shows the index of the lowest value in the array
```

假设你有一个很大的数组，你想知道这个数组的形状，你想知道它是一维的还是二维的，只需使用 **shape** 函数。

```
arr.shape
```

**从 NumPy 数组中索引/选择元素或元素组**

索引 NumPy 数组与 Python 类似。你只需传入你想要的索引。

```
my_array = np.arange(0,11)my_array[8]  *#This gives us the value of element at index 8*
```

为了获得数组中的一系列值，我们将使用切片符号' ***:* '** ，就像在 Python 中一样

```
my_array[2:6] *#This returns everything from index 2 to 6(exclusive)*my_array[:6] *#This returns everything from index 0 to 6(exclusive)*my_array[5:] *#This returns everything from index 5 to the end of the array.*
```

类似地，我们可以使用双括号[][]符号或单括号[，]符号来选择二维数组中的元素。

使用双括号符号，我们将从下面的二维数组中获取值' **60** ':

```
two_d_arr = np.array([[10,20,30], [40,50,60], [70,80,90]])two_d_arr[1][2] *#The value 60 appears is in row index 1, and column index 2*
```

使用单括号符号，我们将从上面的数组中获取值' **20** ':

```
two_d_arr[0,1] 
```

我们还可以进一步使用切片符号来获取二维数组的子部分。让我们在数组的一些角落里抓取一些元素:

```
two_d_arr[:1, :2]           *# This returns [[10, 20]]*two_d_arr[:2, 1:]           *# This returns ([[20, 30], [50, 60]])*two_d_arr[:2, :2]           *#This returns ([[10, 20], [40, 50]])*
```

我们也可以索引整个行或列。要获取任何行，只需使用它的索引号，如下所示:

```
two_d_arr[0]    *#This grabs row 0 of the array* ([10, 20, 30])two_d_arr[:2] *#This grabs everything before row 2* ([[10, 20, 30], [40, 50, 60]])
```

我们还可以使用 **&** (AND)、 **|** (OR)、<、>和==运算符对数组执行条件和逻辑选择，以将数组中的值与给定值进行比较。方法如下:

```
new_arr = np.arange(5,15)new_arr > 10 *#This returns TRUE where the elements are greater than 10 [False, False, False, False, False, False,  True,  True,  True, True]*
```

现在我们可以打印出在上述条件中为真的实际元素，使用:

```
bool_arr = new_arr > 10new_arr[bool_arr]  *#This returns elements greater than 10 [11, 12, 13, 14]*new_arr[new_arr>10] *#A shorter way to do what we have just done*
```

使用条件逻辑运算符 **&** (AND)的组合，我们可以得到大于 6 但小于 10 的元素。

```
new_arr[(new_arr>6) & (new_arr<10)]
```

我们的预期结果是:([7，8，9])

**广播**

广播是更改 NumPy 数组值的快速方法。

```
my_array[0:3] = 50*#Result is:* **[50, 50, 50, 3, 4,  5,  6,  7,  8,  9, 10]**
```

在本例中，我们将索引 0 到 3 中元素的值从初始值更改为 50。

**对 NumPy 数组进行算术运算**

```
arr = np.arange(1,11)arr * arr              *#Multiplies each element by itself* arr - arr              *#Subtracts each element from itself*arr + arr              *#Adds each element to itself*arr / arr              *#Divides each element by itself*
```

我们也可以在数组上执行标量操作。NumPy 通过广播使之成为可能。

```
arr + 50              *#This adds 50 to every element in that array*
```

Numpy 还允许你在数组上执行诸如平方根、指数、三角函数等通用函数。

```
np.sqrt(arr)     *#Returns the square root of each element* np.exp(arr)     *#Returns the exponentials of each element*np.sin(arr)     *#Returns the sin of each element*np.cos(arr)     *#Returns the cosine of each element*np.log(arr)     *#Returns the logarithm of each element*np.sum(arr)     *#Returns the sum total of elements in the array*np.std(arr)     *#Returns the standard deviation of in the array*
```

我们还可以获取二维数组中列或行的总和:

```
mat = np.arange(1,26).reshape(5,5)mat.sum()         *#Returns the sum of all the values in mat*mat.sum(axis=0)   *#Returns the sum of all the columns in mat*mat.sum(axis=1)   *#Returns the sum of all the rows in mat*
```

恭喜你，我们已经到了 NumPy 教程的最后了！

如果你学完了这一课，那么你已经学了很多。坚持练习，这样你新发现的知识就会保持新鲜。

有问题，遇到困难或者只是想打个招呼？请使用评论框。如果这个教程在某些方面对你有帮助，给我看一些👏。