# 基于人群的餐馆评论的反民主化

> 原文：<https://towardsdatascience.com/the-anti-democratization-of-crowd-based-restaurant-reviews-67ab01bad38f?source=collection_archive---------11----------------------->

我完全赞同过去 20 年技术爆炸为发达国家所做的一切。直接——它带来了效率，让我们的生活更轻松，让我们更快地得到东西，甚至帮助我们活得更久。间接的——也许它最丰富的副产品已经在我们看待书呆子、内向者、书呆子和一般社交笨拙者的方式上带来了一场非常激进的改革。至于不发达国家的技术进步，我倾向于说，他们既无法跟上同样的步伐，也没有深远的潜力。我的意思是，上一次我费心去检查的时候，小额金融贷款的增长似乎达到了顶峰，其最初最响亮的倡导者转向了争议较少和更具社会影响的追求。

具体来说，我想重点谈谈技术如何在很大程度上影响我们相互交往方式的范式转变。NYU 经济学家兼作家 Arun Sundararajan 将人类的这种进化称为“共享经济”,他进一步指出:

> “这种转变将通过刺激新的消费、提高生产率以及催化个人创新和创业精神，对经济增长和福利产生积极影响。”

越来越多的企业家几乎每天都在单独或集体创办新的企业，这证明了以上几乎所有的观点都是正确的。无论动机是为了解决现存的老问题，还是为了超越一个似乎没有得到正确公式的倒闭的企业，创业社区继续经历着快速加速的增长。

是的，你没看错，我的确把整个创业社区归为两类。

因为这种创业失败的历史记录往往会因幸存者史诗般的“凤凰涅槃”故事而半途而废，对成功的过度索引往往会使外部观察者认为这种成功和高度搜索引擎优化显著(正)相关。在大多数情况下，要在这个合理的逻辑中找出漏洞是非常困难的。我敢说它几乎是气密的。

***但不完全是。***

请允许我分享一些观点。作为一名企业家，我的大多数企业都失败了，因为我要么没有足够地培养它们，要么没有组建合适的团队来补充我有限的技能。虽然许多失败的企业家可能会很快指出资本不足几乎是他们创业失败的唯一原因，但我认为这只是一个借口。事实上，我被大量的数据所左右，这些数据表明相反的情况更符合经验事实。

至于我们(这次是一个团队，有我姐姐、她的丈夫，还有你的丈夫)最近的投资，是一家印度快餐餐馆([孟买弗兰基公司](http://www.thebombayfrankiecompany.com))，我们已经决定依赖于一个大量启动的初始投资方法。这在很大程度上是基于确保软着陆，因为一旦失败，我们没有投资者可以偿还。但正如许多企业家喜欢过分自信地安慰自己，“这次会不同。”*我们也是。*

这家餐厅开业几周后，我没有意识到有多少技术会渗透到业务的几乎每一个部分。虽然在我职业生涯的大部分时间里，我广泛地从事技术工作，并编写了数百万行代码，但不知何故，我未能预见到交集会变得如此位和字节密集。从建立我们的 Square 销售点到现在与我们合作的 8 个在线交付服务，除了依赖生物计量时钟设备进行工资支付，每一次集成都有一个独特的技术障碍需要克服。但寻找解决方案的每一步都变得越来越令人满意，因为这种努力似乎完全是精英制的——我们投入的工作越多，得到的回报就越多。

*   系统启动了
*   顾客越来越多
*   付款处理速度很快，交易费用低于行业平均水平，付款到我们银行账户的延迟时间也很短
*   簿记很快就完成了，没有一个陡峭的学习曲线
*   我们的数字业务开始快速增长。

# ***但随后我们遇到了意想不到的绊脚石。***

# **Yelp**

在你去餐馆或任何其他地方之前，别人的评论或评论可能会严重影响你成为最终消费者的决定，我相信你已经查看了那家店的 Yelp 评论。作为一个严重依赖这些评论和“看似”民主的评论分享过程的人，我已经养成了努力缩小消费者和贡献者之间差距的习惯。所以，我写评论已经很多年了。现在，在接收端(作为企业所有者)，我们从来没有考虑过以下问题——当我们的评论者给我们留下一贯的五星评论(现在达到 37 星)时,“看似”民主的平台同时将它们一扫而光，这公平吗？

![](img/beaeaf7b90ded10939adeb8f3a06bf28.png)

***超级强调‘bot’。***

Yelp 这么做的理由？这是一种算法。说到蒙骗我们。为了验证我的假设，即模型拟合他们的“算法”实际上有多差，一些实验是必要的:

1.  由于我们的大多数评论者都来自那些很少或根本没有 Yelp 存在的人，这些评论可以合理地假设被指定删除。但是当更多的(甚至一些资深的)评论家开始投稿时，结果是完全一样的。
2.  评论似乎倾向于不同程度的情绪变化和夸张。无论是明显的压抑，高度的尖锐，还是仅仅敷衍了事，结果似乎也是完全一样的。
3.  移除此类审查后，回归确定半衰期。如果在第 1 天留下了 4 条评论，那么到第 3 天，这 4 条评论都将被删除。
4.  不顾一切地向我们的在线社区展示我们至少有一篇评论，我决定写一篇。令人惊讶的是，这 4 天没有被删除。更奇怪的是，该算法没有自动删除我的评论，因为我正在使用我的企业主资料来留下对 Yelp 知道我拥有的企业的评论。也许扩大同情票是一个嵌入的功能。
5.  我们甚至决定屈服于这样一种观念，即通过承诺向 Yelp 广告支付 350 美元,“付费游戏”将使我们的评论复活。到目前为止，两周过去了，还是没有任何改善。

结论:与语义算法几乎没有线性关系，但是嵌入在时间去除函数中的模型拟合很好

# **扎加特调查对比**

起初，我们对这种看似欺诈的做法感到愤怒，但现在看到我们的业务并没有完全衰退，我们不得不将我们的想法转移到我们从基于不对称寡头垄断的经济中转移出来的是多么少。快进到 20 世纪 80 年代和 90 年代，当时 Zagat 调查似乎是餐厅评论领域唯一的真理来源，多年后在 2004 年出现的穿着闪亮盔甲的骑士是 Yelp。随着它在市场上的无处不在和声名鹊起，它似乎为这个被垄断的市场带来了一场基本上民主的改革，更不用说降低那些长期以来享受小人物特权的乏味评论家的垄断影响力了。但是随着许多企业走向成熟，无意中脱离了他们充满理想主义的开端，Yelp 失宠成为像 Zagat 调查最终那样令人厌恶(和淡化)只是时间问题。

# **让颠覆游戏开始吧。**