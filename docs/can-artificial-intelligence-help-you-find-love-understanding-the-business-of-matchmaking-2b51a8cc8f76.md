# 人工智能能帮助你找到爱情吗:理解婚介行业

> 原文：<https://towardsdatascience.com/can-artificial-intelligence-help-you-find-love-understanding-the-business-of-matchmaking-2b51a8cc8f76?source=collection_archive---------5----------------------->

![](img/6cf045676a52fdea3880a0c681cc2ea4.png)

我认为我这一代人是极其幸运的一代，他们处在由技术革命推动的世界巨变的尖端。我们伴随着盒式录像带和录音机、有线电话和大盒子电脑、充满书香的大图书馆长大。然后，几乎不知不觉地，我们过渡到了 iPods 和 YouTube，智能手机和 iPads 和电子书。我猜想，数百年或数千年后，当人们回头看时，我们将正好处于这条线的中间，这条线不亚于现代版的公元前和公元——“谷歌之前-苹果-脸书”和“谷歌之后-苹果-脸书”。

也许更微妙，但更重要的是，我们也正处于风口浪尖的变化是技术的到来在社会学上意味着什么。个人关系变了。互动的模式和渠道已经演变。“做朋友”有了不同的含义。一个看不见的在线网络越来越多地定义了社会。当我思考这个问题时，它让我想到了另一个方面——坠入爱河的概念和行为是否也发生了变化？

你还记得在那些简单的日子里，爱是如何到来的吗？相亲是由朋友和了解你的人安排的。你和人们面对面交流，看看你们是否有共同的兴趣和信仰。相容性是由相处时间决定的。切入今天的世界——在为你寻找完美伴侣的过程中，数据科学和人工智能越来越多地取代了你的朋友、家人、同事、熟人甚至你自己的判断。

交战规则(一语双关)围绕两个轴心发生了变化:

1.  **你如何连接潜在的爱情兴趣**，即介绍和交流的渠道。现在物理会议来的晚多了。你的手机、平板电脑或电脑是你发现和建立潜在浪漫关系的大厦。你用手指轻轻一划就能做出选择。你通过屏幕说话，表情符号代表真实的表情。你希望爱情开花结果。
2.  **你和谁联系**，也就是你可以从中选择的一群人。对我来说，这是更明显的变化，在某些方面也更可怕。不再是你或你认识的人提出潜在的匹配。机器已经取代了这个角色。

在当前的范式中，人——人类和个人——可以被参数化，归结为一个“特征集”，然后人工智能驱动的算法可以找到最“最佳匹配”，即你最有可能与谁兼容。让我们把它分解一下，看看这个“爱的事业”到底是如何在幕后运作的。

推荐引擎如今被广泛应用于我们生活的方方面面。当你在亚马逊上购物时，你会得到关于你可能购买的商品的建议，这就是推荐引擎在起作用。当网飞向你推荐你可能喜欢的电影时，情况也是如此。这种应用的清单今天是无止境的。简单地说，这些引擎通常以三种方式之一工作:

*   **历史趋势:**基于人 X 过去的行为，引擎会尝试预测 X 未来可能做出的选择的可能性。
*   **“像你一样的人”**:在这种方法中，首先基于机器学习的聚类算法将确定倾向于相似的人群。相似性可以通过行为(例如，他们购买或浏览什么，他们如何支付，购买频率，以及无数其他类似的事情)或特征(例如，他们的年龄、性别、地点等)来定义。)或者两者都有。然后，推荐引擎不仅会根据 X 过去做过的事情，还会根据其他“喜欢 X”的人做过的事情来预测 X 的选择。
*   **【基于内容】**:这种方法更关注目标项目及其特征，而不是人的特征。所以在网飞电影的例子中，这将转化为识别 X 喜欢看的电影的特征(类型、长度、语言、年代、演员等。)来确定他可能感兴趣的内容。

实际上，大多数推荐引擎可能会混合使用以上所有方式。反馈越多，引擎就能越准确地预测行为。反馈实质上是特定的预测(也称为推荐)是否被接受。

现在，让我们回到爱情的话题上。这种相似之处很容易画出来。

*   不再是被预测有可能被接受的物品或电影，而是 X 可能与之一见如故的人。
*   历史趋势指的是任何关于 X 以前关系的数据。
*   喜欢 X '的人将根据 X 自己的行为和特征来确定，例如年龄、种族、教育程度、地点、就业状况、食物偏好、爱好、眼睛颜色、体型、身高等。
*   目标项目特征现在将指属于预期目标列表的个体中的这些相同特征。

这些特征的列表越长，算法的效果就越好。请记住，X 没有必要明确提供这些数据——在我们今天生活的世界中，大多数这些信息都以某种方式、形式或形式在互联网上围绕着每个人流动——这只是关于访问和挖掘这些信息。

一旦这些数据点可用，人工智能算法就可以施展魔法，为每个潜在客户分配可能性或概率分数，以确定 X 最有可能选择和喜欢的人。和其他情况一样，系统会自我学习，因此它会随着每次反馈变得越来越好，即每次 X 接受或拒绝建议的匹配。

你可能会同意，这背后的科学并不难理解。但这种暗示并不一定令人舒服。理论上，这种方法实际上可以非常好地找到你的爱。像我一样经常网上购物的人可能会同意，亚马逊似乎比你自己更清楚你会对什么感兴趣。它非常好用。这和做媒很像。

这里有一个陷阱——这整个方法有一个潜在的假设，即寻找爱情是基于规则或逻辑的。这就是我个人认为婚介业务永远无法像几乎所有其他应用程序那样从人工智能中获益的地方。因为在现实中，或者说我愿意相信，寻找爱情并不总是合乎逻辑的。因此，尽管机器和人工智能越来越多地扩散到我们生活的各个方面，但我坚信，在这个特定的领域，神秘和神奇可能会挥之不去。