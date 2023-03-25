# 如何与客户交谈以获得更好的结果

> 原文：<https://towardsdatascience.com/how-to-talk-to-customers-to-get-better-results-5fcae25c5f0c?source=collection_archive---------0----------------------->

## 他们可能不懂数据科学，但他们可以教你很多东西。

*本文摘自* [*像数据科学家一样思考*](https://manning.com/books/think-like-a-data-scientist?a_aid=thinklikeadatascientist&a_bid=eb49dc22) *。*

数据科学领域的每个项目都有一个客户。有时，客户是付钱给你或你的企业来做项目的人，例如，客户或合同代理。在学术界，客户可能是要求您分析其数据的实验室科学家。有时客户是你、你的老板或另一位同事。无论客户是谁，他们都希望从你这个负责项目的数据科学家那里得到一些东西。

通常，这些期望与以下方面有关:

1.  需要回答的问题或需要解决的问题；
2.  有形的最终产品，如报告或软件应用程序；或者，
3.  先前研究或相关项目和产品的总结

期望可以来自任何地方。一些是希望和梦想，另一些来自类似项目的经验或知识。然而，关于期望的典型讨论可以归结为两个方面:客户想要什么，数据科学家认为什么是可能的。这可以被描述为愿望与实用主义，客户描述他们的愿望，数据科学家根据表面的可行性批准、拒绝或限定每一个。另一方面，如果你愿意把自己这个数据科学家想象成一个精灵，一个愿望的授予者，你不会是第一个这样做的人！

## 解决愿望和实用主义

至于客户的愿望，他们可以从完全合理到完全古怪，这是可以的。很多商业发展和硬科学都是由直觉驱动的。也就是说，首席执行官、生物学家、营销人员和物理学家都利用他们的经验和知识来发展关于世界如何运转的理论。其中一些理论有可靠的数据和分析支持，但其他更多的来自直觉，这基本上是一个人在他们的领域广泛工作时开发的概念框架。很多领域和数据科学的一个显著区别是，在数据科学中，如果一个客户有一个愿望，即使是一个有经验的数据科学家也不一定知道是否可能。软件工程师通常知道软件工具能够执行什么任务，生物学家或多或少知道实验室能做什么，但尚未看到或使用过相关数据的数据科学家面临着大量的不确定性，主要是关于哪些具体数据可用以及它能为回答任何给定问题提供多少证据。同样，不确定性是数据科学过程中的一个主要因素，在与客户谈论他们的愿望时，应该首先考虑这一点。

例如，在我与生物学家和基因表达数据打交道的几年中，我开始形成自己的概念，即 RNA 是如何从 DNA 翻译而来的，RNA 链是如何在细胞中漂浮并与其他分子相互作用的。我是一个视觉型的人，所以我经常发现自己在想象一条由数百或数千个核苷酸组成的 RNA 链，每个核苷酸看起来就像四个字母中的一个，代表一个碱基化合物(A、C、G 或 T；为了方便起见，我用“T”代替“U”)，整个链看起来像一条长而柔韧的链——这个句子只对细胞内的机器有意义。由于 RNA 及其核苷酸的化学性质，互补序列喜欢彼此结合；a 喜欢与 T 结合，C 喜欢与 g 结合。因此，当两条 RNA 链包含接近互补的序列时，它们很可能会彼此粘在一起。如果一条 RNA 链足够灵活并含有互补的序列，它也可能折叠并粘在自身上。这是一个概念框架，我在很多场合下用它来猜测当一堆 RNA 在细胞中漂浮时会发生什么。

因此，当我开始处理微小 RNA 数据时，我意识到微小 RNA 大约 20 个核苷酸的短序列——可能会与遗传 mRNA 序列的一部分(即直接从对应于特定基因的 DNA 链翻译的 RNA，通常要长得多)结合，并抑制其他分子与该基因的 mRNA 相互作用，从而有效地使该基因序列变得无用。对我来说，一点 RNA 可以粘在一段遗传 RNA 上，并最终阻止另一个分子粘在同一段上，这在概念上是有意义的。这一概念得到了科学期刊文章和确凿数据的支持，这些数据表明，如果 microRNA 和基因 mRNA 具有互补序列，它们可以抑制基因 mRNA 的表达或功能。

然而，与我一起工作的一位生物学教授有一个更加微妙的概念框架，描述了他如何看待这个基因、微小 RNA 和 mRNA 的系统。特别是，他几十年来一直在研究普通小鼠小家鼠的生物学，可以列出任何数量的显著基因、它们的功能、相关基因以及物理系统和特征，如果开始做“敲除”这些基因的实验，这些基因就会受到明显的影响。因为教授比我更了解老鼠的遗传学，而且因为他不可能和我分享他所有的知识，所以在花太多时间研究一个项目的任何方面之前，讨论这个项目的目标和期望对我们来说是非常重要的。没有他的投入，我基本上只能猜测生物学相关的目标是什么。如果我错了(这很有可能)，工作就白费了。例如，某些特定的微小 RNA 已经得到了很好的研究，并且已知它们在细胞内完成非常基本的功能，甚至更多。如果该项目的目标之一是发现很少研究的微小 RNA 的新功能，我们可能会想从分析中排除某些微小 RNA 家族。如果我们不把它们排除在外，它们很可能只会给细胞内已经非常嘈杂的基因对话增添噪音。这仅仅是教授知道的许多重要事情中的一件，而我却不知道。因此，在认真开始任何项目之前，对目标、期望和注意事项进行冗长的讨论是必要的。

从广义(如果简单的话)来说，当且仅当客户对结果满意时，项目才被认为是成功的。当然，这一准则也有例外，但无论如何，在数据科学项目的每一步中始终牢记期望和目标是非常重要的。不幸的是，根据我自己的经验，在项目的开始阶段，期望通常是不清楚或者不明显的，或者不容易简明地表达出来。因此，我决定采用一些实践来帮助我找出合理的目标，这些目标可以指导我完成涉及数据科学的项目的每一步。

## ***客户很可能不是数据科学家***

关于客户期望的一件有趣的事情是，他们可能不合适。这并不总是——甚至通常也不是——客户的错，因为数据科学解决的问题本质上是复杂的，如果客户完全了解他们自己的问题，他们可能就不需要数据科学家来帮助他们了。因此，当客户的语言或理解不清楚时，我总是放他们一马，我认为设定期望和目标的过程是一个联合练习，可以说类似于冲突解决或关系治疗。

您，数据科学家，和客户都有成功完成项目的共同兴趣，但是你们两个可能有不同的具体动机，不同的技能，最重要的是，不同的观点。即使你自己是客户，你也可以把自己想象成分成两半，一部分(数据科学家)专注于获得结果，另一部分(客户)专注于使用这些结果做一些“真正的”事情，或者项目本身之外的事情。通过这种方式，数据科学的项目从寻找两种性格、两种观点之间的一致开始，如果它们不冲突，至少是完全不同的。

虽然严格来说，您和客户之间没有冲突，但有时看起来是这样的，因为你们都在朝着一组既可实现(对数据科学家而言)又有帮助(对客户而言)的目标混日子。而且，就像在解决冲突和关系治疗中一样，也涉及到感情。这些感觉可能是意识形态的，受个人经历、偏好或观点的驱使，对另一方来说可能没有意义。因此，一点耐心和理解，而不需要太多的判断，对你们双方都非常有益，更重要的是，对项目也非常有益。

## ***问非常具体的问题来揭露事实，而不是发表意见***

当客户描述关于您要研究的系统的理论或假设时，他们几乎肯定会表达事实和观点的混合，区分这两者通常很重要。例如，在一项关于小鼠癌症发展的研究中，前述生物学教授告诉我，“众所周知，哪些基因与癌症有关，而这项研究只关注那些基因，以及抑制它们的微小 RNA。”人们可能会试图从表面上接受这种说法，并只分析癌症相关基因的数据，但这可能是一个错误，因为这种说法有些模糊。原则上，还不清楚是否其他可能与癌症无关的基因在实验引发的复杂反应中起辅助作用，或者是否众所周知并证明癌症相关基因的表达完全独立于其他基因。在前一种情况下，忽略与非癌症相关基因相对应的数据不是一个好主意，而在后一种情况下，这可能是一个好主意。不解决这个问题，就不清楚哪一个是合适的选择。所以，问很重要。

同样重要的是，问题本身要以客户能够理解的方式表述。例如，问“我应该忽略来自与癌症无关的基因的数据吗？”是不明智的这是一个关于数据科学实践的问题，属于你的领域，而不是生物学家的。相反，你应该问类似于“你有任何证据证明癌症相关基因的表达是独立于其他基因的吗？”这是一个关于生物学的问题，希望生物学教授能够理解。

在他的回答中，区分他所想的和他所知的是很重要的。如果教授只是认为这些基因的表达是独立于其他基因的，那么在整个项目过程中，这肯定是要记住的事情，但你不应该根据它做出任何非常重要的决定——比如忽略某些数据。另一方面，如果教授可以引用科学研究来支持他的观点，那么利用这个事实来做决定是绝对明智的。

在任何项目中，作为数据科学家，你是统计学和软件工具方面的专家，但是主要的主题专家通常是其他人，就像涉及生物学教授的情况一样。在向这位主题专家学习的过程中，你应该提出一些问题，这些问题不仅能让你对所研究的系统是如何工作的有一些直观的感觉，还能试图将事实与观点和直觉分开。基于事实的实际决策总是一个好主意，但是基于观点的决策可能是危险的。“信任，但要确认”这句格言在这里很合适。如果我忽略了数据集中的任何基因，我很可能错过了癌症实验中各种类型的 RNA 之间发生的复杂相互作用的一个关键方面。事实证明，癌症是一种非常复杂的疾病，不仅在医学层面，在基因层面也是如此。

## ***提示交付物:猜测并检查***

您的客户可能不了解数据科学及其用途。问他们，“你希望在最终报告中出现什么？”或者“这个分析应用程序应该做什么？”很容易导致“我不知道”，或者更糟，一个没有实际意义的建议。数据科学不是他们的专业领域，他们可能没有完全意识到软件和数据的可能性和局限性。因此，通常最好用一系列建议来解决最终产品的问题，然后注意顾客的反应。

我最喜欢问客户的一个问题是，“你能给我一个你可能希望在最终报告中看到的句子的例子吗？”我可能会得到这样的回答，“我想看看:‘微小 RNA-X 似乎能显著抑制 Y 基因’；”或者“基因 Y 和基因 Z 似乎在所有测试样本中表达水平相同。”诸如此类的回答为构思最终产品的格式提供了一个很好的起点。如果客户能给你这样的种子想法，你可以扩展它们，提出最终产品的建议。你可能会问，“如果我给你一张特定微 RNA 和基因 mRNAs 之间最强相互作用的表格会怎么样？”客户可能会说这很有价值，也可能不会。

然而，最有可能的是，客户会做出不太明确的陈述，例如，“我想知道哪些微小 RNA 在癌症发展中是重要的。”当然，如果我们希望成功地完成这个项目，我们需要澄清这一点。生物学意义上的“重要”是什么意思？这种重要性如何体现在现有的数据中？在继续之前得到这些问题的答案是很重要的；如果你不知道微小 RNA 的重要性如何在数据中体现出来，你怎么知道你什么时候找到了它？

我和许多其他人犯的一个错误是将相关性和重要性混为一谈。一些人谈到了相关性和因果性的混淆，一个例子是:戴头盔的骑车人比不戴头盔的骑车人卷入事故的比例更高；头盔引发事故的结论可能很诱人，但这可能是错误的。头盔与事故的相关性并不意味着头盔导致事故；也不是说事故[直接]导致头盔。事实上，在更繁忙、更危险的道路上骑自行车的人更有可能戴头盔，也更有可能发生事故。本质上，在更危险的道路上骑车会导致这两种情况。在头盔和事故的问题上，尽管存在相关性，但没有直接的因果关系。反过来，因果关系仅仅是相关性可能很重要的一个例子。如果你正在对头盔的使用和事故率进行研究，那么这种相关性可能是显著的，即使它并不意味着因果关系。应该强调的是，重要性，正如我所使用的术语，是由项目的目标决定的。头盔-事故相关性的知识可以导致考虑(和建模)作为项目一部分的每条道路上的交通和危险水平。相关性也不能保证显著性。我相当肯定更多的骑自行车事故发生在晴天，但这是因为更多的骑自行车的人在晴天上路，而不是因为任何其他重要的关系(当然，除非下雨)。我现在还不清楚如何利用这些信息来实现我的目标，所以我不会花太多时间去探索它。在这种特殊情况下，这种相关性似乎没有任何意义。

在基因/RNA 表达实验中，通常在 10-20 个生物样品中测量了数千个 RNA 序列。这种变量(每个 RNA 序列的表达水平)远多于数据点(样本)的分析被称为“高维”或通常“欠确定”，因为变量太多，其中一些只是随机相关，如果说它们在真正的生物学意义上是真正相关的，那将是荒谬的。如果你向生物学教授提交一份强相关性的列表，他会立即发现你报告的一些相关性不重要，或者更糟的是，与已有的研究相反，你将不得不回去做更多的分析。

## ***基于知识而不是愿望来重复你的想法***

正如在你所掌握的领域知识中，把事实和观点分开是重要的一样，避免让过度乐观使你对障碍和困难视而不见也是重要的。我早就说过，优秀数据科学家的一项无价技能是预见潜在困难并为其开路的能力。

在当今的软件行业中，在分析能力还处于开发阶段时就对其进行断言是很流行的。我了解到，这是一种推销策略，似乎经常是必要的，尤其是对于年轻的初创企业，以便在竞争激烈的行业中取得成功。当有人积极销售一款分析软件时，我总是感到紧张，我说我*认为*我可以开发这款软件，但考虑到我们现有数据的一些限制，我不能 100%肯定它会按计划工作。因此，当我做出如此大胆的声明时，我会尽可能地将它们保持在我几乎肯定能做到的事情范围内，如果我做不到，我会尝试制定一个备用计划，不涉及原计划中最棘手的部分。

假设您想要开发一个总结新闻文章的应用程序。你需要创建一个算法，可以解析文章中的句子和段落，并提取主要思想。有可能编写一个算法来做到这一点，但尚不清楚它的性能如何。对于大多数文章来说，摘要在某种意义上可能是成功的，但 51%的成功和 99%的成功之间有很大的区别，至少在你建立了第一个版本之前，你不会知道你的特定算法属于那个范围。盲目销售和狂热开发这种算法可能看起来是最好的主意；努力就会有回报，对吧？也许吧。这项任务很难。完全有可能的是，尽管你尽了最大努力，但你永远不会获得超过 75%的成功，从商业角度来看，这可能还不够好。那你会怎么做？你会放弃并关闭商店吗？只有在这次失败后，你才开始寻找替代方案吗？

一个优秀的数据科学家甚至在开始之前就知道任务有多难。句子和段落是复杂的随机变量，通常看起来是专门设计来挫败你可能扔给它的任何算法的。在失败的情况下，我总是回到“首要原则”，在某种意义上:我试图解决什么问题？除了总结，最终目标是什么？

如果最终目标是建立一个让阅读新闻更有效率的产品，也许有另一种方法来解决新闻读者效率低下的问题。或许把相似的文章聚合在一起呈现给读者更容易。或许可以通过更友好的设计或整合社交媒体来设计更好的新闻阅读器。

没有人想宣布失败，但数据科学是一个有风险的行业，假装失败从来没有发生本身就是一个失败。解决问题总是有多种方法，制定一个承认障碍和失败可能性的计划可以让你在前进的道路上从微小的成功中获得价值，即使主要目标没有实现。

一个更大的错误是忽略失败的可能性以及测试和评估应用程序性能的需要。如果你认为产品工作得近乎完美，但事实并非如此，那么将产品交付给客户可能是一个巨大的错误。你能想象如果你开始销售一个未经测试的应用程序，该应用程序本应该对新闻文章进行摘要，但是很快你的用户就开始抱怨摘要完全错误吗？不仅应用程序会失败，而且你和你的公司可能会因为软件不工作而名声大噪。

*要了解更多信息，请下载免费的第一章* [*像数据科学家*](https://manning.com/books/think-like-a-data-scientist?a_aid=thinklikeadatascientist&a_bid=eb49dc22) *一样思考，并查看此* [*幻灯片演示*](http://www.slideshare.net/ManningBooks/think-like-a-data-scientist) *获取折扣代码。*

*Brian Godsey 博士，是一位数学家、企业家、投资人和数据科学家，他的著作* [*像数据科学家一样思考*](https://manning.com/books/think-like-a-data-scientist?a_aid=thinklikeadatascientist&a_bid=eb49dc22) *现已面世。——【briangodsey.com】[](http://www.briangodsey.com/)*

*如果你喜欢这个，请点击💚下面。*

 *[## (我喜欢你)叫我大数据

### 恶名昭彰的 IDE 人群的滑稽嘻哈联合

medium.com](https://medium.com/@briangodsey/i-love-it-when-you-call-me-big-data-2e4b89e84740)*  *[## 不确定性意识:数据科学的一个优点

### 脸书最近在趋势分析上的失态再次表明，好的数据科学取决于承认你不知道

medium.com](https://medium.com/@briangodsey/awareness-of-uncertainty-a-virtue-in-data-science-c6751e7f5a00)*