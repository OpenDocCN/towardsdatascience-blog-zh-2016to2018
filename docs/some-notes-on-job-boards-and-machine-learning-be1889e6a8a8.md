# 关于工作板和机器学习的一些说明

> 原文：<https://towardsdatascience.com/some-notes-on-job-boards-and-machine-learning-be1889e6a8a8?source=collection_archive---------7----------------------->

![](img/36d29970470aaf66ddc56246782b190e.png)

Image [via](https://commons.wikimedia.org/wiki/File:A_typewriter_(10995863465).jpg), used [under](https://creativecommons.org/licenses/by-sa/2.0/deed.en)

找工作最难的部分之一是首先找到申请什么。用户知道自己想要什么工作、工作地点和工资范围，但招聘信息板很难搞清楚。

与其让求职者在无穷无尽的清单中寻找合适的东西，为什么不使用机器学习来做一些排序呢？至少，一个算法可以清理掉一些杂物，让用户专注于严肃的选项。充其量，它可以找到一个完美的职业发展机会。

首先，机器学习算法必须学习职位发布的样子。也就是说，它必须知道如何提取标题，位置，薪酬范围等。从一个文本块。这些信息构成了数据库，程序从中提取信息，将工作发送给用户。然后，一旦程序能够提取所有这些信息，它需要能够根据经验和偏好向求职者提供好的建议。

所有这些后端计算意味着用户只能看到系统总库存的一小部分。只有少数工作会出现在用户的提要中，应用程序在提供未来选择时会考虑这些工作的匹配程度。

这种系统最困难的部分是从用户反馈中微调推荐。随着用户数量的增加，对新回复进行再培训的需求将呈指数级增长，而快速、可靠地改善每个人的个人资料将需要大量的时间和金钱。然而，规模问题并不妨碍构建一个基本的程序架构。

和大多数事情一样，机器学习可能会彻底改变我们找工作的方式。更有针对性的推荐可以节省求职者的时间和精力，也让公司的招聘过程不那么痛苦。通过仔细减少给用户的选择，一种算法可以让漫长而艰苦的求职成为过去。