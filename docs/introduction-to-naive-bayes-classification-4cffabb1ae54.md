# 朴素贝叶斯分类简介

> 原文：<https://towardsdatascience.com/introduction-to-naive-bayes-classification-4cffabb1ae54?source=collection_archive---------1----------------------->

![](img/5d144ad6223002b387c57f576b7de2bd.png)

朴素贝叶斯是一个简单、有效且常用的机器学习分类器。它是一种概率分类器，在贝叶斯设置中使用最大后验决策规则进行分类。也可以用一个非常简单的贝叶斯网络来表示。朴素贝叶斯分类器在文本分类中特别受欢迎，是垃圾邮件检测等问题的传统解决方案。

## 模型

任何概率分类器的目标是，利用特征 x_0 到 x_n 和类 c_0 到 c_k，确定特征在每个类中出现的概率，并返回最可能的类。因此，对于每一类，我们希望能够计算 P(c_i | x_0，…，x_n)。

为了做到这一点，我们使用**贝叶斯规则**。回想一下贝叶斯规则如下:

![](img/2e694cc6c5def483e76f9ee96682d9f5.png)

在分类的上下文中，您可以用一个类 c_i 替换 A，用我们的一组特征 x_0 到 x_n 替换 B。由于 P(B)用作归一化，并且我们通常无法计算 P(x_0，…，x_n)，我们可以简单地忽略该术语，而是只陈述 P(c_i | x_0，…，x_n) ∝ P(x_0，…，x_n | c_i) * P(c_i)，其中∝表示“与成比例”。P(c_i)计算简单；P(x_0，…，x_n | c_i)更难计算。为了简化其计算，我们假设 x_0 到 x_n 是**条件独立**给定 c_i，这就允许我们说 P(x_0，…，x _ n | c _ I)= P(x _ 0 | c _ I)* P(x _ 1 | c _ I)*…* P(x _ n | c _ I)。这个假设很可能是不正确的——因此命名为*朴素*贝叶斯分类器，但是该分类器在大多数情况下仍然表现良好。因此，我们对类概率的最终表示如下:

![](img/0c94e83f9454adbd0f256cd7ee7dac4e.png)

计算各个 P(x_j | c_i)项将取决于您的要素所遵循的分布。在文本分类的背景下，其中特征可以是字数，特征可以遵循**多项式分布**。在其他情况下，特征是连续的，它们可能遵循**高斯分布**。

请注意，与其他常见的分类方法相比，朴素贝叶斯中的显式训练非常少。在预测之前必须做的唯一工作是找到特征的个体概率分布的参数，这通常可以快速且确定地完成。这意味着朴素贝叶斯分类器甚至可以在高维数据点和/或大量数据点的情况下表现良好。

![](img/443a8e35611ea3ed7bed2b1df7a84030.png)

## 分类

既然我们有了一种方法来估计给定数据点落入某个类别的概率，我们需要能够使用它来产生分类。朴素贝叶斯以非常简单的方式处理这个问题；根据数据点的特征，简单地选择具有最大概率的 c_i。

![](img/5aa97c91907a3dfd461ded97032ae3cd.png)

这被称为**最大后验概率**决策规则。这是因为，回头参考我们的贝叶斯规则公式，我们只使用 P(B|A)和 P(A)项，它们分别是似然项和先验项。如果我们只使用 P(B|A)的可能性，我们将使用一个**最大可能性**决策规则。