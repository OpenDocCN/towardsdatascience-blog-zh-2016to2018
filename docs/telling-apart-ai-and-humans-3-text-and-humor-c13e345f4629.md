# 区分人工智能和人类#3:文本和幽默

> 原文：<https://towardsdatascience.com/telling-apart-ai-and-humans-3-text-and-humor-c13e345f4629?source=collection_archive---------18----------------------->

如果你错过了这个系列的前几个装置，在这里了解一下[人类和机器人的区别](https://medium.com/@sina_lana/telling-apart-ai-and-humans-1-humans-vs-androids-bddeab54b0e2)和[照片和生成的图像](https://medium.com/@sina_lana/telling-apart-ai-and-humans-2-photo-vs-gan-generated-image-c20e09e69554)。

在本帖中，我们攻击自动生成输出的最古老的形式之一:文本。对许多人工智能研究人员来说，给计算机编程以生成类似人类的文本是一个圣杯，这不仅是因为[图灵测试](https://en.wikipedia.org/wiki/Turing_test)，还因为围绕语言存在的神秘性。包括科学家在内的许多人都喜欢用近乎宗教的术语来看待语言——在你所选择的上帝的创造物中，语言会让人类“凌驾”于其他生物之上，这是一种神秘而神奇的东西，让我们变得特别(因此更优越，这是逻辑)。想象一下，如果你能创造一个会说话的机器人，你会变成什么样！

无论你是在寻找让你比你的宠物狗更好的东西，还是对语言本身感兴趣，文本生成算法都是无尽的乐趣。目前没有算法可以理解人类的话(不，甚至谷歌机器翻译。尤其不是谷歌机器翻译！).目前没有算法有足够的真实世界的经验来知道字母“椅子”应该是什么。最好的语言处理算法是那些可以计算诸如“R 完成 CHAI 序列而不是 O 完成相同序列的可能性有多大？在法语文本中，CHAISE 翻译的字母 CHAIR 的频率是多少？”。这是一个非常不同的过程，当你读到“椅子”这个词时，你会立即想到椅子是什么样子，以及它是如何使用的。

知道算法不理解意义是你需要辨别一段文本是由机器人还是由人类生成的最重要的事情。人类可能会犯错误，但它们是人类的错误:句法、语法……计算机错误是意义上的错误。这正是它们如此有趣的原因。让我们转向我最喜欢的神经网络幽默来源:[詹妮尔·谢恩](http://aiweirdness.com/)。

詹妮尔·谢恩用她能找到的任何有趣的数据来训练网络。以下是生成的 cookie 配方的示例:

我觉得很精彩！也是剖析典型神经网络错误的绝佳例子。

1.  重复:这里使用的特定模型具有短暂的记忆。这意味着它不跟踪它以前写的超过几个单词或几行的东西。它会经常重复自己。毕竟，如果它知道“一杯糖”在食谱中出现的概率很高，并且记忆短暂，它就没有办法理解食谱中没有 6 杯糖，也没有办法跟踪它已经写了多少杯。它还会忘记在食谱中使用所有这些杯子。
2.  忘记标点符号:网络可能很难学习跨越长时间尺度的关系。例如，括号需要在打开后的某个地方关闭。这比短期规则难学多了，比如“一个大写字母紧跟在句号之后！”所以最后你会看到永久的左括号、引号等等。
3.  混淆的标点符号:在普通文本中，大写字母出现在句号之后，但有时也会出现在句子中间:地名或人名。有时候大写字母在名字中间！但是网络无法理解普通单词和名字之间的区别。都是字母。所以它会随机放置大写字母，因为从统计上来说，你时不时需要一个大写字母…
4.  最明显的迹象表明你正在和一个网络打交道。大多数时候，一个训练有素的网络会使用现有的单词。但是，接受过字母训练的网络对“单词”没有很好的概念。是一组字母，周围有两个空格吗？好吧，那“Mapkamares”怎么样？我看不错！一些网络从一开始就接受完整单词的训练。给他们一个单词列表，以及只包含这些单词的文本。这些网络无法组成随机的单词，但它们仍然会在意义和标点符号上挣扎。

这里还有两个来自我自己的机器人的例子。第一个是纽约餐馆菜单的培训:

注意重复、随机大写和左括号。巧克力片肉汁和外套。

第二个是我在自己的推特档案上训练的机器人:

文字还可以，但是意思就是有点太奇怪了，不像真的。与这个“我强迫了一个机器人…”迷因相比。

这可能是人类的幽默，但不是神经网络幽默。剧情太一致，意思太平实，大写太对，语法太完美。幽默来自对意义的高度理解。很难像机器人一样写作，正是因为机器人远非人类。

完全披露:我对这种喜剧有两个理由。首先，人类以一种不明显虚假的方式伪装成机器人伤害了我的研究领域。大多数人根本不知道这些是人类写的，也不知道有什么先进的算法可以产生这种类似人类的幽默。他们告诉我，“你见过这个机器人吗？太搞笑了！”或者“我不确定这是不是真的，你怎么看？”任何混淆计算机能做什么和不能做什么的东西对我的领域来说都是一种威胁。人们提高了他们的期望，并将算法视为银弹，一个可以在眨眼之间做任何事情的魔盒。当有人真的制造出一个具有人类幽默的机器人时，谁会理解其中的含义呢？当外行人期望高水平的输出在我们的能力范围之内时，谁来解释为什么最先进的输出看起来像是乱码垃圾？第二个问题:如果你说“这是我写的”时，你的喜剧并不好笑，如果整个机器人的事情是人们发笑的唯一原因，也许它一开始就没那么好笑。

让我们来看一个更难的例子:

这让我哭笑不得，当它第一次出现。然而，这个场景的时间线是不是有点太一致了，标点符号是不是太好了？

Botnik 工作室有一种不同的生成文本的方法。是的，在某个地方涉及到了算法，但它是一个人写的文本。电脑只是提出建议，就像你手机的自动更正功能；但最终，是人来决定写什么。你可以在[https://botnik.org/apps/](https://botnik.org/apps/)试试(可惜经常宕机)。

那么，我怎么知道其中涉及到一个算法呢？可能需要一些训练来确定你的判断，但是如果你发现自己不断地问“我错过了什么吗？”，想知道为什么事情会发生，或者必须使用大量的想象力来使场景工作，这是一个很好的机会，你正在阅读算法的散文。这就是神经网络幽默的核心:当文字实事求是地在你的脑海中创造出一个极其荒谬的场景时，当大多数喜剧作品不是由文本而是由你的大脑生成的图像完成时，这就是你知道你有一个神经网络来感谢这些笑声的时候。

我给你留下三个链接供你欣赏。遇见 [inspirobot](https://inspirobot.me/) 及其励志名言:

![](img/b669b30796c22a12a8fede08b6001047.png)

Inspirobot 在[美国生活](https://www.thisamericanlife.org/663/how-i-read-it)中亮相。

看一部科幻电影，其中每个人都尽了最大努力来遵循机器人编写的场景:

并在 J [anelle Shane 的博客](http://aiweirdness.com/)上找到真正的神经网络幽默的无穷乐趣。