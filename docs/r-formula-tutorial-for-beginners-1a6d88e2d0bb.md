# 初学者 r 公式教程

> 原文：<https://towardsdatascience.com/r-formula-tutorial-for-beginners-1a6d88e2d0bb?source=collection_archive---------5----------------------->

![](img/7bacd7cb916a6d033df8d6f4d32fa7da.png)

想一想，R 中的很多函数都利用了公式:像`ggplot2`、`stats`、`lattice`、`dplyr`等包都在用！使用这些 R 对象的常见函数示例有`glm()`、`lm()`、`facet_wrap()`等。但是这些公式到底是什么，为什么要用呢？

这些只是本教程希望回答的一些问题:

**提示**:您有兴趣在统计建模的背景下学习更多的公式吗？看看 DataCamp 的[多元与 Logistic 回归](https://www.datacamp.com/courses/multiple-and-logistic-regression)课程。

# R 中的数据结构

因为公式是 R 编程语言中的一个特殊类，所以简单地修改一下这种编程语言中可用的数据类型和数据结构是一个好主意。

记住 R 是一种面向对象的编程语言:这种语言是围绕对象来组织的。R 中的一切都是对象。

让我们从头开始:在编程中，你使用数据结构存储数据，函数处理数据。数据结构是组织在计算机内存中的数据的接口。正如 R 语言定义所说，R 并不提供对计算机内存的直接访问，而是提供一些你可以称为“对象”的特殊数据结构。每个数据结构都是为优化存储、访问或处理的某个方面而设计的。

R 中的五种主要数据结构是:

*   原子向量，
*   列表，
*   矩阵，
*   数据帧，以及
*   排列

```
# Create variables 
a <- c(1,2,3,4,5,6,7,8,9) 
b <- list(x = LifeCycleSavings[,1], y = LifeCycleSavings[,2])
```

**提示**:你可以使用`typeof()`函数返回一个 R 对象的类型。对象的类型告诉您关于任何对象的(R 内部)类型或存储模式的更多信息:

```
# Retrieve the types of `a` and `b` 
typeof(a) 
typeof(b)
```

双份

'列表'

在上面定义变量`a`和`b`的例子中，您可以看到数据结构包含数据元素序列。这些元素可以是相同或不同的数据类型。您可以在 R 中找到以下 6 种原子数据类型:

*   数字，如`100`、`5`、`4`，包含整数。
*   字符，如`"Hello"`、`"True"`或`"23.4"`，由键盘字符串组成。；
*   逻辑的，如`TRUE`或`FALSE`，由“真值”组成；
*   raw，如`48 65 6c 6c 6f`，由比特组成；
*   复数，如`2+5i`，包含复数；最后一点，
*   double，如`3.14`，包含十进制数。

在 r 中，几乎所有的对象都有属性。例如，您可能已经知道矩阵和数组只是简单的向量，属性`dim`和可选的`dimnames`被附加到向量上。属性用于实现 r 中使用的类结构。作为一种面向对象的编程语言，类的概念以及方法是它的核心。类是对象的定义。它定义了对象包含的信息以及如何使用该对象。

看看下面的例子:

```
# Retrieve the classes of `a` and `b` 
class(a) 
class(b)
```

'数字'

'列表'

**注意**如果一个对象没有`class`属性，它有一个隐式类，“矩阵”、“数组”或`mode()`函数的结果。

您可能遇到的一些特殊类是日期和公式；而这最后一个就是今天教程的题目！

# R 中的公式是什么？

当你阅读本教程的介绍时，你可能已经看到了在使用像`ggplot2`这样的包或者像`lm()`这样的函数时出现的公式。因为您通常在这些函数调用中使用公式来表达统计模型的思想，所以在建模函数和一些图形函数中经常使用这些 R 对象是合乎逻辑的。

对吗？

然而，公式并不局限于模型。它们是一个强大的通用工具，允许您捕获两件事情:

*   未赋值的表达式，以及
*   创建表达式的上下文或环境。

这解释了为什么在函数调用中使用公式来生成“特殊行为”:它们允许您捕获变量的值，而无需对它们求值，以便它们可以被函数解释。

记住数据结构后，您就可以将这些 R 对象描述为“语言”对象或未赋值的表达式，它们具有一个“公式”类和一个存储环境的属性。

在上一节中，您看到了对象具有某些(R internal)类型，这些类型指示对象是如何存储的。在这种情况下，公式是“语言”类型的对象。

但是这到底意味着什么呢？

嗯，当你处理 R 语言本身时，你通常会遇到这种类型的对象。为了更好地理解这一点，请看下面的例子:

```
# Retrieve the object type 
typeof(quote(x * 10)) # Retrieve the class 
class(quote(x * 10))
```

“语言”

“呼叫”

在上面的例子中，你要求 R 返回`quote(x*10)`的类型和类。结果你看到`quote(x*10)`的类型是`'language'`，而`class`是`'call'`。

这绝对不是一个公式，因为你需要用`class()`来返回`'formula'`！

但那是什么呢？

R 中的公式的特征是波浪号操作符`~`。有了这个操作符，您实际上可以说:“捕捉这段代码的含义，而不用马上对它进行评估”。这也解释了为什么你可以把 R 中的公式看作一个“引用”操作符。

但是公式到底是什么样子的呢？仔细看看下面一行代码:

```
# A formula 
c <- y ~ x 
d <- y ~ x + b # Double check the class of `c` 
class(c)
```

公式

波浪号(`~`)左侧的变量称为“因变量”，而右侧的变量称为“自变量”，由加号`+`连接。

很高兴知道这些变量的名称会根据上下文而变化。你可能已经看到自变量以“预测值(变量)”、“受控变量”、“特征”等形式出现。同样，你可能会遇到因变量，如“反应变量”、“结果变量”或“标签”。

**注意**尽管您在上面的代码块中定义的公式`d`包含几个变量，但公式的基本结构实际上只是波浪号`~`和至少一个独立或右侧变量。

**记住**公式实际上是具有存储环境属性的语言对象:

```
# Return the type of `d` 
typeof(d) # Retrieve the attributes of `d` 
attributes(d)
```

“语言”

```
$class [1] "formula" 
$.Environment <environment: R_GlobalEnv>
```

正如你在上面的例子中看到的，公式中包含的变量可以是向量。但是，您经常会看到公式中包含的变量来自数据框，就像下面的示例一样:

```
Sepal.Width ~ Petal.Width + log(Petal.Length) + Species
```

**注意**当创建公式本身时，不会访问任何已分配给公式中符号的数据值。

现在你已经知道了 R 中的公式是什么样子，它们是什么，最好提一下底层的公式对象是不同的，这取决于你有一个单边还是双边的公式。你可以通过观察左边的变量来识别前者。如果没有，就像`~ x`中一样，你有一个片面的公式。

这也意味着单侧公式的长度为 2，而双侧公式的长度为 3。

不完全信服？看看下面的代码块。您可以借助方括号:`[[`和`]]`来访问公式的元素。

```
e <- ~ x + y + z 
f <- y ~ x + b # Return the length of `g` 
length(e) 
length(f) # Retrieve the elements at index 1 and 2 
e[[1]] 
e[[2]] 
f[[3]]
```

2

3

```
`~` x + y + z 
x + b
```

# 为什么在 R 中使用公式？

如您所见，公式是功能强大的通用工具，允许您捕获变量的值，而无需对它们求值，以便它们可以被函数解释。这已经是为什么应该在 r 中使用公式的答案的一部分了。

此外，您使用这些 R 对象来表达变量之间的关系。

比如下面代码块中的第一行代码，你用第一行代码说“y 是 x，a，b 的函数”；当然，你也可以遇到更复杂的公式，比如在第二行代码中，你的意思是“萼片宽度是花瓣宽度的函数，取决于物种”。

```
y ~ x + a + b 
Sepal.Width ~ Petal.Width | Species
```

# 在 R 中使用公式

现在，您已经了解了这些特殊 R 对象的“是什么”和“为什么”,是时候了解如何使用基本公式以及更复杂的公式了！在本节中，您不仅会看到如何创建和连接基本公式，还会发现如何在运算符的帮助下构建更复杂的公式。

***如果您想了解更多关于如何在 R 中创建公式、连接公式、使用公式运算符以及如何在 R 中检查公式的信息，请访问*** [***原始教程***](https://www.datacamp.com/community/tutorials/r-formula-tutorial) ***。***

# 何时使用公式

到目前为止，您已经了解到 R 公式是通用工具，并不局限于建模，并且您已经看到了一些可以使用公式的例子。在本节中，您将更深入地了解最后一个主题:您将看到一些可以利用这些工具的案例。当然，您将会涉及到诸如`lattice`和`stats`之类的软件包的建模和图形功能，但是您也将会涉及到`dplyr`中的非标准评估。

***转到*** [***原创教程***](https://www.datacamp.com/community/tutorials/r-formula-tutorial) ***阅读全节。***

# r 配方奶粉包

之前，您已经看到您可以使用`as.formula`、`update()`、`all.vars`等函数来创建和检查您的公式。...这些都是简单的操作和处理，但是高级的公式处理呢？也许下面这些套餐会让你有些兴趣！

# `Formula`套餐

最近，这个包发表在 CRAN 上。这款套装非常适合那些想让配方更上一层楼的人。这个包扩展了基类`formula`。

更具体地说，`Formula`对象扩展了基本的公式对象:使用这个包，您实际上可以定义公式，这些公式接受一个附加的公式操作符`|`来分隔多个部分，或者可以在左侧包含所有的公式操作符(包括管道字符)来支持多个响应。

您将能够创建的公式示例如下:

*   多部分公式，如`y ~ x1 + x2 | u1 + u2 + u3 | v1 + v2`
*   多响应公式，如`y1 + y2 ~ x1 + x2 + x3`
*   多部分响应，如`y1 | y2 + y3 ~ x`，以及
*   以上三者的组合。

```
# Load package 
library(Formula) # Create formulas 
f1 <- y ~ x1 + x2 | z1 + z2 + z3 
F1 <- Formula(f1) # Retrieve the class of `F1` 
class(F1)
```

**注意**功能`as.formula()`和`is.formula()`在这个包中也被更新:你将使用`is.Formula()`和`as.Formula()`来代替！

在这里阅读更多。

[这个包](https://www.rdocumentation.org/packages/formula.tools/versions/1.5.4)是最近发布的，它为你提供了“操作公式、表达式、调用、赋值和其他 R 对象的编程工具”。这是一大堆，但本质上，这一切都归结为:您可以使用这个包来访问和修改公式结构，以及提取和替换那些 R 对象的名称和符号。这个包裹是克里斯托弗·布朗写的。

在使用这个包时，您可能会发现以下一些有用的东西:

*   `get.vars()`:代替`all.vars()`，这个函数会从各种 R 对象中提取变量名，但是所有符号等。将被插入到变量的名称中。
*   `invert()`:您可以使用此功能反转对象中的运算符，如公式。
*   `is.one.sided()`:这个函数可以很方便的判断一个函数是单边的还是双边的。

**记住**一个公式如果长这样就是片面的:`~x`；当表述为`x~y`时，它将是双面的。

***有兴趣了解更多套餐？查看*** [***原教程***](https://www.datacamp.com/community/tutorials/r-formula-tutorial) ***。***

# 还有更多的发现！

万岁！你已经完成了 R 公式的教程。如果你想了解更多，一定要看看 Hadley Wickham 的数据科学 书籍 [*R，其中有一章专门介绍 R 中的公式和模型族*](http://r4ds.had.co.nz/)

您能想出更多可以找到公式或更多可以用来操作公式的包的例子吗？随时在推特上告诉我: [@willems_karlijn](https://twitter.com/willems_karlijn) 。

*原载于*[*www.datacamp.com*](https://www.datacamp.com/community/tutorials/r-formula-tutorial)*。*