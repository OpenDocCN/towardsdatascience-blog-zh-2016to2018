# 不仅仅是算法——在工业中建立模型

> 原文：<https://towardsdatascience.com/more-than-algorithms-building-models-in-industry-109badf5318a?source=collection_archive---------13----------------------->

![](img/555b9388af0ff3eea27626b2b3eaaed8.png)

*本文原载于*[*【blog.zakjost.com】*](https://blog.zakjost.com/post/more-than-models/)

由于数据科学博客圈几乎完全专注于机器学习算法的本质细节，你会被原谅认为这是作为一名 ML 从业者最重要的方面。但是那些在行业中建立模型来解决实际商业问题的人知道这只是工作的一小部分。学术人员可能在本地构建模型，并根据基准数据对其进行评估，以获得可发布的结果，而工业界的人员正在将模型集成到一个更大的系统中，这有很多失败的机会。这篇文章是关于在这种环境下你需要做的其他重要的事情。

# 垃圾进，垃圾出

在工业界，当有人问一个模型表现如何时，得到的回答往往是:*让我做一些分析*。如果这是您的情况，您将面临不必要痛苦的风险。

![](img/220d622e4045f47f83377843722476c4.png)

有一天，一些人将审查业务度量，并且不可避免地发现一个主要问题。他们会说，“你的模型说所有这些东西都是 X，但实际上它们是 y。这没有任何意义，而且每天要花费我们数十亿美元！”

当事实证明基于某个模型的决策是糟糕的时，就会引出几个明显的问题:*我的模型坏了吗？我的数据管道坏了吗？我建模的东西变了吗？回答这些问题应该不比看仪表盘难。这给我们带来了重要的事情 1。*

> *重要的事情 1:除非你有实时的性能监控，否则你还没有完成*

(“实时”的定义将取决于您的业务问题，并受到标签成熟度的限制)。这听起来可能真的很难，但是除非你在一个有极端数据孤岛的组织中，否则你可以在几个小时内构建一些东西。你只需要:

1.  访问模型分数和标签
2.  可以运行 cron 作业的机器
3.  一台可以托管仪表板堆栈的机器，如[Grafana](https://grafana.com/)+[influx db](https://www.influxdata.com/)

使用 Docker 图像，我在大约 3 个小时内构建了整个堆栈，尽管以前从未使用过这些工具。即使您是唯一可以访问它的人，这个练习仍然值得您花费时间，因为这是一项时间投资，当出现问题时，它会在早期向您提供可操作的信号。您不仅能够更快地排除故障，而且通过观察模型的时间行为，您将对模型有更多的了解。

结果可能是你的模型是好的，但是进入你的模型的数据才是问题所在。好消息:这也很容易测量，你只需将其连接到你的新仪表板解决方案。一旦有了用于性能监控的监控仪表板/数据库设置，添加这样的新视图就变得容易多了。这是重要的事情。

> *重要的事情 2:监控你的模型输入和输出*

太好了！您可以监控模型的输入、输出和性能。现在你可以在东西坏了的时候检查它！或者每隔一分钟检查一次，确保一切正常。*对吗？*错了。

> *重要的事情 3:在你的显示器上设置闹钟*

如果你费了很大的劲来构建将所有重要指标放在一个地方的东西，为什么不构建一些简单的规则来在事情变得不可靠时提醒你呢？得到一个关于你的一个重要输入变量突然丢失的警报，远比从这个问题给企业带来的所有痛苦中间接地发现它要好得多。警报将允许您联系企业并说，“注意:有丢失的数据，它导致我的模型行为怪异，这将导致错误的决策和数十亿美元的损失，所以让我们暂停事情，直到数据问题得到解决。我已经将此事上报给负责数据的团队。”

# 保持新鲜

由于各种原因，模型几乎总是随着时间而退化。最终，您可能会希望使用最新的数据来重新训练您的模型。既然你有一个奇特的仪表板可视化性能，至少这应该是预期和计划的，而不是对紧急问题的反应。但是有一个更好的方法，这是下一个重要的事情。

> *重要的事情 4:自动化模型再训练和部署*

这不仅使你的模型保持新鲜和高性能，而且这是一项应该在*年*内获得回报的投资，即使在你离开团队之后。

它如何节省您的时间？因为技术债务会引发更多的技术债务。当一个团队在运营痛苦中溺水时，他们倾向于反动，去扑灭紧急的大火。这意味着他们可能不知道模型降级了，直到它引起了问题，然后他们尽可能快地修复这个问题。而“尽快”这一部分导致了额外的技术债务。

与自动刷新的模型形成对比。如果您从一开始就知道这是一个需求，那么您会做出设计决策，并在整个过程中支持它。因此，与其用一个大的 Jupyter 笔记本从您的笔记本电脑中取出一个 csv 文件，然后吐出一个模型工件，您可以用一些黑魔法将其部署到生产中，不如将您的数据提取过程从您的模型构建过程中模块化，并自动跟踪和部署模型。有了这一点，模型再培训项目从几周/几个月变成了每天或每周进行，没有人参与。

这是另一个非常强大的原因:人们倾向于从头开始重建，而不是逆向工程。如果您不自动化一个过程来保持模型的新鲜，那么您的工作很可能在您不积极维护它的时候就被丢弃了。如果你的解决方案在你离开后继续增值，你的影响力会被放大。

当我们谈到这个话题时，你可以做最后一件重要的事情，让你的工作不至于很快变得无关紧要:

> *重要的事情 5:文件，文件，文件*

不同的公司有不同的文化规范来保存信息。不管是什么，做好，做好。早点开始，不要让它成为你会回来做的事情之一，因为你可能永远不会回来。撰写正式的白皮书，记录您的设计决策和分析。还要创建一个更容易访问的 wiki 页面，或者其他面向下一个可能需要维护的人的页面。从头开始重建系统的主要原因之一是因为原始系统没有很好的文档记录。

# 摘要

因此，这里有 5 件重要的事情，它们将使您的工作保持稳健和相关，同时为您节省大量时间，否则这些时间会浪费在不必要的操作消防上:

1.  实时监控您的模型
2.  监控您的模型输入和输出
3.  监视器上的警报
4.  自动化模型再训练和部署
5.  记录你的工作

【blog.zakjost.com】您可以在 [*找到我所有的内容并订阅*](http://blog.zakjost.com)