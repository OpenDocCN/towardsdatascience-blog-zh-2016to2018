# 如何给一个人工智能项目定价

> 原文：<https://towardsdatascience.com/how-to-price-an-ai-project-f7270cb630a4?source=collection_archive---------2----------------------->

客户多次要求我为大型机器学习(ML)项目提供固定的价格估计。这真的很棘手。需求经常会在项目进行到一半时发生变化，这是由于功能蔓延、开发延误、集成问题、用户接受度和许多其他因素造成的。我建议客户**而不是**在他们的第一个 ML 项目中对抗需求变更，这与传统的软件开发原则完全相反。机器学习是**而不是**常规编程。它基本上是应用数据科学，在一个已经拥有非机器学习基础设施的组织中，与一个从头开始的初创公司相比，它的推出非常不同。

![](img/ab66b5103cca8188a3661a4bef7eb602.png)

Machine Learning consulting is a premium service

未知越大，或者我喜欢称之为需求风险，我就越倾向于按小时计费而不是固定价格。在需求非常紧张的地方，或者我喜欢称之为可执行规范的地方，我越倾向于固定价格。

在之前的一篇文章中，我讨论了[如何雇佣一名人工智能顾问](https://medium.com/towards-data-science/why-hire-an-ai-consultant-50e155e17b39)，在这篇文章中，我们将研究一个项目是如何定价的。

一位与我们共事的政府代表喜欢将这些坦率的对话称为开放的和服方式。残酷的诚实。让我们现实地考虑一下入场费和每小时的费用。如果是现场演出，我们 2017 年 8 月的标准价格是 250 美元/小时，外加差旅费和每日津贴。考虑到启动合同的努力，包括 NDA、工作说明书和初步讨论，承包商的目标是至少 5K (20 小时)大小的项目。一个低跟进潜力的一小时项目只是一个不成功的项目(例如调试我的代码)。你(客户)也有预算问题，需要考虑内部资源。我们喜欢将尽可能多的低端工作委派给客户的员工，以减少完成项目所需的时间。但是在一天结束的时候，你仍然支付你的员工在这个项目上的工作，并且需要考虑到这一点。你的目标是控制 ML 项目的成本和时间。我们的目标是努力达到我们的时薪，即使是固定价格的项目，并尽可能吸引大项目。

这篇文章的目的是帮助你对你的项目进行高层次的定价。让我们给一个小的虚构项目定价，看看我们最终会在哪里。

## 客户要求

对于 ML 中的任何项目来说，关键是我们需要设定关于[准确度、精确度、召回率、F 分数等](http://machinelearningmastery.com/classification-accuracy-is-not-enough-more-performance-measures-you-can-use/)的期望。让我们假设客户想要“好”的结果，而不是一个量化的基准。这使得项目更容易定价，因为迭代次数更少。一般来说，人工智能的质量随着数据集的大小而增长。

另一个要考虑的维度是需求质量。许多客户提出了定义不明确的需求，这就是为什么他们不仅需要我们的专家建议，还需要我们对[项目定义](https://en.wikipedia.org/wiki/Statement_of_work)和[解决方案架构](https://en.wikipedia.org/wiki/Solution_architect)的建议。在讨论的最早可能阶段，确定任何被证明不可能实现的需求，或者需要新科学的需求是非常关键的。不开玩笑。有人要求我固定研究项目的价格，而研究的定义是你不知道答案。我们的解决方案很简单。为了固定价格研究，我们提供固定价格的小时数。结果不能保证，但至少燃烧速度得到控制。在那些项目中，我们的目标是尽早交付结果，以激励进一步的发展。

我们将在本文中定价的假想项目是一个文档分类系统，它使金融机构中的 BI 分析师能够转储文档(PDF、Word 等。)并用许多不同的方法按语义和句法相似性对它们进行排序。客户感兴趣的是文档之间的相似性，以及每个文档和搜索框的关键字内容之间的相似性，以及文档和用户粘贴的文本段落之间的相似性。对于分析师来说，这是一个普通的任务，并不是一个超级新颖的 ML 项目，但它给了我们一些我们可以轻松定价的东西。让我们定义客户端没有 ML 服务器。要排序的数据不是敏感的内部数据，因此可以安全地运送到 AWS 以外的地方，供 ML 系统进行消化和呈现。[正如我在之前的文章](https://medium.com/@lemaysolutions/locked-in-a-box-machine-learning-without-cloud-or-apis-76cc54e391c8)中所讨论的，一些公司由于各种原因在使用公共云数据时遇到了困难。

让我们计划一下这个事情，然后估计一个价格。

## 规划

**第一步:打好基础**

我们现在知道该项目将存在于 AWS 中，并将使用一个或多个从现有 AMI 中派生出来的 p2/p8 实例。假设在与客户的交谈中，[定制的弹性搜索功能](https://www.elastic.co/guide/en/elasticsearch/reference/current/index-modules-similarity.html)不能满足这些分析师的需求，而[的常规搜索功能](https://www.elastic.co/guide/en/elasticsearch/reference/current/similarity.html)也是必要的，但还不够，我们决定建立一个 ML 和现有文档搜索工具的混合模型。该系统将需要 tensorflow、word2vec、doc2vec、keras、elasticsearch 和 Flask 来像 elasticsearch 一样公开这组特性。我们将需要一个用于 AngularJS GUI 的 PHP 服务器(如果是一个小规模项目，甚至可能在同一个实例上)。我们决定不使用 NLTK，因为 elasticsearch 包含了我们会从这个包中用到的所有东西。Jupyter notebook 是一个很好的想法，这样，将拥有这个项目的开发人员可以轻松安全地在服务器上运行代码，而且我们也可以轻松地重用 github 示例中的代码。这是双赢。我们还需要知道客户需求对应于这样的工具:

> 文档相似度+文档到段落相似度= word2vec 和 doc2vec，还有 CNN 的一些 Keras [型号+word2vec](https://github.com/alexander-rakhlin/CNN-for-Sentence-Classification-in-Keras/blob/master/w2v.py) 。仅供参考[这只是我们可以根据自己的需要开始和塑造的众多例子中的一个](http://www.wildml.com/2015/11/understanding-convolutional-neural-networks-for-nlp/)。
> 
> 文档关键字搜索和其他搜索功能=弹性搜索

重用模型节省了时间和金钱。我们可能会使用预先训练的谷歌新闻 word2vec 模型，或者可能是手套模型。基本上，我们的计划是使用一些现成的代码。

Word2vec 不对保存的模型进行迁移学习，因此预先训练的模型可能不能很好地代表定制模型的表现。我们建议客户，他们同意这个计划。

elasticsearch 有很多客户不知道的很酷的 API，所以除了开发工作之外，我们还为客户的员工安排了一些培训。

这就是高水平。

**第二步:优先考虑早期结果**

所以我们想给这个项目定价。让我们决定对公司来说最紧急的优先事项是什么，并为第一阶段的开发定价。为什么在我们第一次约会之前就决定我们婚姻的条款？我的理念是从第一天开始就给出现实的价格，并保持初始阶段的简短，以便客户可以很快看到并感受到结果。该项目是关于句子，段落和整个文档的语义相似性。让我们启动系统，向客户展示他们**不能**下架的功能。客户同意我们将提供 2 个实例。我们称之为**“web 1”**的一个服务器是 RESTful LEMP web 服务器，它将包含我们的 Angular 代码、文件转储，稍后它还将托管 elasticsearch 代码。这个实例上没有 GPU，但它将有一个大块存储附件来保存所有文件。我们称之为**“ML1”**的另一个服务器将保存 ML 系统。ML 服务器将接受来自 web 服务器的作业，并将存储将被成批转储回 web 服务器的响应。ML1 将是一个高内存的 p2 实例，因为它将受到大量 GPU 作业的冲击，但也有很高的内存需求。这是因为像我们将在 word2vec/gloVe 中使用的单词嵌入模型比计算密集型更占用内存。

在第一阶段，我们没有捕捉主题建模，也没有考虑整个弹性搜索模块和培训。在与客户的交谈中，我们也推动文档相关性回归。这些项目可以随时进入第二阶段。现在客户希望看到奇迹发生。

接下来我们把项目票扔进 JIRA。

专注于文档分类，我们估计 AWS 实例供应需要 10 个小时，证书安装(PKKs、SSL、OTP 等)需要另外 5 个小时。).这 15 个小时包括工具安装。我们在报价中增加了 3 个小时的知识传授时间，以确保客户了解系统的工作原理。现在我们有了一个工作的双实例系统。让我们来设置 ML 和 GUI。不需要负载平衡器、地理分布等。我们保持简单。

我们估计 10 个小时的 GUI 开发，包括文件转储和结果的介绍。我们决定使用 tensorboard 来显示文档聚类，并在单独的 GUI 中使用一个角度表来排列结果。此阶段通过 HTACCESS 密码进行身份验证。在第 2 阶段，我们可以使用 Oauth 2.0 登录，这样分析师就可以使用他们的工作帐户登录系统。

所以现在我们是 25 小时。我们继续吧。

核心 ML 的配置和部署不会超过 10 个小时。这种需求与 ML 工具的现有能力非常匹配。这段时间包括一个小时的客户演示，向他们展示整个系统如何工作。

**第三步:考虑滑移**

经验法则是，当试图估算项目价格或持续时间时，估计一个因子π。让我们把圆周率截成 3。所以滑点最多可以达到 35*3*(2/3) = 35*2 = 70 小时。

## 定价

服务器设置: **15 小时**

界面设置: **10 小时**

ML 开发: **10 小时**

延迟:**长达 70 小时**

因此，我们估计第一阶段的工作需要 35 到 105 个小时，或**8，750 到 26，250 美元**。为了控制成本，我会详细介绍客户可以采取的避免延误的步骤，包括提前规划网络访问(防火墙、端口、证书等)。).这是那种我会在 10K 提供定价的项目，因为滑点的风险很低。

如果我们指定第二和第三阶段，我希望他们每个人都会来到 10K，项目总成本为 30K。这些阶段大约每 4 周发布一次。也许会更快，因为这个项目比一般项目要简单得多。只有在项目被指定为工作说明书的这一点上，客户才真正签署合同。

当我们结束项目时，我们试图向客户追加销售更多的 ML 解决方案，这可以为客户增加超出初始项目的价值。这使我们在第 4 阶段及以后的比赛中保持领先。

## 结论

当谈到项目定价时，希望这对你来说是一个真正深入了解人工智能顾问的想法的机会。如果你喜欢这篇文章，那么请推荐它，分享它，或者给它一些爱(❤).

编码快乐！

-丹尼尔
[丹尼尔@lemay.ai](mailto:daniel@lemay.ai) ←打个招呼。
[LEMAY . AI](https://lemay.ai)
1(855)LEMAY-AI

您可能喜欢的其他文章:

*   [人工智能和不良数据](/artificial-intelligence-and-bad-data-fbf2564c541a)
*   [人工智能:超参数](/artificial-intelligence-hyperparameters-48fa29daa516)
*   [人工智能:让你的用户给你的数据贴上标签](https://medium.com/towards-data-science/artificial-intelligence-get-your-users-to-label-your-data-b5fa7c0c9e00)