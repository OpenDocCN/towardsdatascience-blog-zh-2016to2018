# 带 Spark 的简单度量和立方体

> 原文：<https://towardsdatascience.com/easy-metrics-and-cubes-with-spark-32b883fe7d76?source=collection_archive---------17----------------------->

你有没有参加过这样的会议:双方在同一个指标上有两个不同的数字？从这个指标中得到的任何见解都将被遗忘，获得正确数字的斗争将会开始。从长远来看，这种情况会引发一个更大的问题，那就是对你的数据、你的方法以及最终对你的团队完全缺乏信任。

![](img/b54b2fd9c6e7c531ff749313ac83f6af.png)

Photo by [Micaela Parente](https://unsplash.com/@mparente?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

提供值得信赖的数据源，建立管道以便其他人不需要重复计算，并提供唯一的真实来源，这基本上是数据工程师的主要工作。

但是……我们应该建哪些管道呢？与业务最相关的指标是什么？我们需要在哪个维度打破它们？

就命名、度量和维度达成一致是一项复杂的工作。我们相信我们的分析师同事能够找到并达成最佳定义。这一部分非常耗时，所以我们希望将他们从任何样板活动中解放出来，以便从数据中分析和提取见解。

为了增加复杂性，我们希望让我们的同事能够自主工作。我们将为他们部署和维护数据管道，但在我们找到促进生产的指标之前，有一个完整的“试错”过程。

## 我们如何促进分析自主性？

命名解决方案很简单；构建 it，没那么简单:
- *为你的同事提供工具，让他们的日常工作变得简单。*

在 [Schibsted 中，我们正在构建工具](https://bit.ly/2mDUoND)，以便于[访问数据](https://medium.com/@mitxino77/bigdata-sql-query-engine-benchmark-e8605f355464)。但是如果没有干净、整洁、连贯的数据，这些都是没有用的。数据民主的第二面来了:为正确的受众转换和准备正确的数据。理想情况下，只做一次。

我们在这方面的贡献是尽可能减少将数据转化为价值所需的代码行数和复杂性。为我们的同事提供一个安全的库，以便从包含数百万行的原始数据中创建聚合指标。

![](img/be712d4c762e62e1cdfa355ece13ec10.png)

“A child walking along a park path to catch up with their family” by [Jelleke Vanooteghem](https://unsplash.com/@ilumire?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

## 度量生成库

让我们从一个典型的用例开始:

> 分析师 M____ 希望从该数据集中提取指标 X、Y 和 Z，并按维度 a、b 和 c 对其进行分组。

你认为最简单的版本是什么？简单易行:
`SELECT col_1, col_2, count(*) FROM my_table GROUP BY col_1, col_2`

为什么我们要为这样简单的用例创建一个库呢？如果像 SQL 这样的东西如此简单、冗长和有意义，为什么还要把代码复杂化呢？因为我们工程师在日常工作中会遇到其他类型的问题。可靠性、可扩展性、自动化、警报和监控、质量等问题

我们需要生成一个软件，我们可以安排它在一个可伸缩的系统中运行，无论何时它需要运行，都是一致和正确的。我们需要知道什么时候出错(失败、不运行、奇怪的结果……)。我们需要将我们的同事 M____ 的这一段代码转换成适当的数据管道。

## 第一个简单指标

指标可以总结为维度组合(浏览器、城市和类别)的值(x 的数量)。我们添加了一个域来提供一些额外的上下文和一个惟一的标识符。我们也强烈鼓励在维度中包含一些时间框架值。

这个小片段非常容易在我们公司的 Jupyter 之间共享，作为交互验证的服务，也可以在以后与我们的自动化工程师共享。虽然这里还有一个问题:你用的是哪些数据？

这些指标背后的神奇之处在于，它们并不真正关心它们使用哪个数据源。让我换一种说法，有一些最低要求，如维度和`userId`列需要存在，但我们没有针对维度 A 或 B 或不同日期的特定代码。只需插入一个数据框，就可以得到指标。

![](img/63b9b757684f73d75353b43ad352c434.png)

Photo by [Bernard Hermant](https://unsplash.com/@bernardhermant?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

## 事情变得复杂了

在这个简单的用例之后，分析师想要知道的经常性指标是`UNIQUE xxx`。使用 SQL 也很容易，只需添加`DISTINCT`标记就可以了。你甚至在 Spark 里还有一个`countDistinct()`的方法。那是什么问题呢？您不能合计唯一计数。Android 中的唯一用户 iOS 中的唯一用户= =移动中的唯一用户是不成立的。您可能在两个平台上有相同的用户，这意味着您将计算相同用户的副本。

我们修改了 spark 库，给我们一些我们称之为小计的东西。这样，我们就可以计算出一个维度的`ALL`值里面的唯一用户。这是一个非常有用的功能，可以防止我们手动改变数据帧来计算每个维度的`ALL`度量值。还记得阶乘增长有多快吗:2 维> 2 种排列；3>6；4>24；5>120；…

好吧，让我为我们的库给这个问题的简单性感到骄傲:列出你想要计算小计的维度，就这样。重新计算指标，您将看到类似这样的内容:

## 多维数据集与度量标准

用户从来都不容易，他们总是想要越来越多，并且他们中的每一个人都有他们一生中非常特殊的一次用例。通过生成指标而不是计算最终的 KPI，您使他们能够根据相同的指标创建和调整尽可能多的 KPI。但是您也给了他们更多的工作，因为他们需要为每个维度过滤他们需要的维度，并且他们需要在一周内汇总所有指标以获得每周值(请记住，唯一计数除外！！`7*DailyUsers != 1*WeeklyUsers`)。

也有两种使用这些指标的方法:一种是使用指标作为`metric`列中的值；以及那些喜欢将每个指标视为一列的人。简单的度量方法会给我们第一个版本，但对于探索性分析来说，第二个版本确实更容易也更安全，这被称为[立方体](https://en.wikipedia.org/wiki/OLAP_cube)。

在我们的简化范围内，我们会付出更大的努力。我们如何让我们的同事变得如此简单，以至于他们可以毫不费力地从度量方法转变为立方方法？同样，我们提供一个`MetricCalculator`类来计算数据帧的度量值，我们提供一个`CubeCalculator`来做完全相同的事情:

## 实现可重用性

这个库背后的整个想法是让我们的生活更容易，在这个过程中，我们开发了一些不错的功能。这是一个迭代的故事，从一个简单的度量开始，到一个更复杂的度量，最后到立方体。但我们也发现了开发全局函数和转换的机会，我们推广了最佳实践，并简化了为非工程师构建数据管道的过程，我们还提供了广泛的开箱即用过滤器，用于使用我们最受欢迎的数据集并转换为统一的命名约定。

我们已经开始推广这个库，并使它能够在我们所有的数据发现产品中使用，我们希望这将是通往“*单一真理来源*”之旅的又一步。

希望你喜欢这个帖子，
*- Iker*