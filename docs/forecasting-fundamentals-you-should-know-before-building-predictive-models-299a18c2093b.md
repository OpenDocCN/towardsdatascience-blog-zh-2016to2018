# 在构建预测模型之前，您应该了解的预测基础知识

> 原文：<https://towardsdatascience.com/forecasting-fundamentals-you-should-know-before-building-predictive-models-299a18c2093b?source=collection_archive---------10----------------------->

预测，还是不预测，这是一个问题。

人类文明史与我们尝试预测方法的历史交织在一起。当我们的祖先观察天空来预测天气时，数据科学家开发并训练机器学习模型来预测销售、风险、事件、趋势等。准确的预测是一项重要的组织能力，做得好的企业将会有很大的生存优势。

## 应该预测什么

在预测项目的早期阶段，需要决定应该预测什么，什么时候可以准确预测，以及什么时候预测不会比扔硬币好。

例如，如果需要对**房地产市场**进行预测，则有必要询问是否需要对以下方面进行预测:

*   任何类型的财产，或独立/半独立/联排别墅/公寓分开？
*   是按地区分组的房产平均销售价格，还是仅针对总销售额？
*   周数据，月数据还是年数据？

需要注意的关键是**并不是所有的预测都比掷硬币**好。事件或价值的可预测性取决于几个因素，包括:

*   我们是否发现并理解了影响结果的大部分因素？
*   这些因素有“大”数据吗？
*   预测是否会影响我们试图预测的事情？

例如，24 小时天气预报可以非常准确，因为这三个条件通常都满足。另一方面，很难预测下一滴雨滴落入你眼中的概率，明天的并发汇率会上升或下降或下周的比特币价格。

## 时间跨度和数据可用性方面的预测类型

是否需要提前几分钟、6 个月或 10 年的预测？就时间跨度而言，有 3 种类型的预测:

*   **短期预测**:一至三个月的正常范围
*   **中期预测**:时间周期一般为一年
*   **长期预测**:预测超过两年的结果

在大多数预测情况下，随着事件的临近，与我们预测的事物相关的不确定性会减少。换句话说，我们预测的越近，我们就越准确。

根据数据可用性，预测可以分为两种类型。

*   **定性预测**:如果没有可用数据，或者可用数据与预测无关。
*   **定量预测**(时间序列预测):如果过去的数字信息可用；过去的模式将延续到未来。

用于定量预测(时间序列预测)的数据通常以固定的时间间隔观察，例如每小时、每天、每周、每月、每季度、每年。目标是估计历史观察序列将如何延续到未来。

## 预测方法

方法的选择取决于可用的数据和事件的可预测性或要预测的价值。

**由于缺乏历史数据，判断性预测**是定性预测的唯一选择。例如，预测新政策、新产品或新竞争对手的影响。

最简单的**时间序列预测**方法仅使用待预测变量的历史值，并排除可能影响其行为的因素，如竞争对手的活动、环境或经济条件的变化等。下图显示了使用过去 10 年的销售数据对 2017 年的房屋销售预测。

![](img/c14b844141768ee4c4bb56b5013182ff.png)

house sales prediction for 2017 with past 10-year sales data

在本文中，我们将讨论什么是预测、预测类型和预测方法。预测显然是一项具有挑战性的活动。在以后的文章中，我将探讨一些常用的预测方法，包括指数平滑法、ARIMA 模型、动态回归模型、LSTM 等。

“你看到这些伟大的建筑了吗？没有一块石头留在另一块石头上，不被拆毁。”( [**马克 13:1–2**](https://bible.knowing-jesus.com/Mark/13/1))

## 让预测在未来到来之前向你展示它。