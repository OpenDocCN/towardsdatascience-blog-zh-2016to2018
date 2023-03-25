# 走向再现性:平衡隐私和出版

> 原文：<https://towardsdatascience.com/toward-reproducibility-balancing-privacy-and-publication-77fee2366eee?source=collection_archive---------4----------------------->

在数据安全和研究披露之间的冲突中，会有一个金发女孩的选择吗？

![](img/d044d1328c9f45aaf341b4c232285f3d.png)

Photo by [Shiva Smith](https://www.pexels.com/@shiva-smyth-394854) on [Pexels](https://www.pexels.com/).

数据科学是一个高度跨学科的领域，在学术/行业分界线的两侧(以及两者之间的任何地方)都呈爆炸式增长。这导致了从业者背景和哲学方面惊人的多样性，该领域的多样性转化为数据科学和高级分析组织的观点和政策的多样性。一些组织，无论是在学术界还是工业界，都有非常“学术”的天赋，领导者鼓励开发新颖的模型和方法，然后发布这些方法并参加会议。相反，其他小组则专注于根据行业标准按时创建可销售的数据产品，同时受到 NDAs 和其他数据的限制，而不太关注理论上的新颖性。大多数组织在这两者之间寻求某种程度的平衡，但是找到平衡点通常需要仔细考虑技术和组织的需求和目标。

这些理念和环境的差异将数据科学领域分割成了基于数据和模型可用性的万花筒般的子集，这使得在不同环境之间转化发现变得非常困难。多种多样的软件许可、知识产权保护以及隐私和安全保障会使[复制，更不用说再现性，成为一个重大挑战](/data-sciences-reproducibility-crisis-b87792d88513)。然而，所有持久的职业，无论多么隐秘，都有一个共同点:从业者能够以有意义和富有成效的方式相互分享信息和最佳实践。

建立强大的专业环境的唯一方法是让数据科学家能够相互分享问题和解决方案，因为没有人知道所有的答案。在许多前沿模型和大型数据集有访问限制的领域中，这可能是极其困难的。然而，其他领域已经克服了类似的挑战，数据科学越早从其前辈和相关领域获得灵感，就越早能够在信息共享方面制定严格的标准。

但在此之前，我们必须先看看这个领域的现状。

![](img/8de01f9dbe26375b02e97ba1227c2f8f.png)

GNU, from the [Free Software Foundation](https://www.fsf.org/)

# **寄养合作**

自由和开放源码软件(FOSS)也许是软件可用性的最自由的方法之一。在这种情况下，开源意味着一个项目的代码库可以公开地被检查、修改和分发，而自由(就像“解放的”，而不是“极其便宜的”)意味着你可以用你可以访问的软件做任何你想做的事情。自由和开放源码软件有各种各样的模式，其中许多模式在什么是自由和什么是开放源码以及一个给定的软件是一个、两个还是两个都不是之间做出了令人困惑的区分。想到这一点最简单的方法是使用理查德·斯托尔曼对 4 种软件自由的定义:以你喜欢的方式运行程序的自由，研究和修改程序的自由，重新发布程序的自由，以及发布程序修改副本的自由。

这种类型的模型，或者非常类似的东西，是学术软件的默认设置。大多数出版的学术著作都与某种公开可用的代码库相关，其中最常见的是 [GitHub](https://github.com/) 。但是这个模型很少提到可及性的负担，而且[这些已经成为学术界所有领域的共同问题，不仅仅是计算领域的问题](https://web.stanford.edu/~vcs/Nov21/hilary_spencer_rdcscsJan2010.pdf)。换句话说，坚持自由/开源软件概念的规则是一回事，但坚持其原则又是另一回事。出版物禁运、员工超负荷工作、服务器停机、IT 规则和政策，甚至补丁和更新等因素都会使在有意义的时间范围内重现或复制过去的实验变得困难。这些可访问性障碍并不总是恶意的，甚至不是有意的，但它们仍然是实践的一个重大障碍。

在云计算的推动下，数据科学中的许多挑战已经减少。用电子邮件发送大量 zip 文件的日子已经一去不复返了。如果你在这个领域工作的时间够长的话，你可能还记得有一段时间你不得不将数据或软件刻录到 CD 上或加载到硬盘上，然后将整个东西邮寄给合作者。但是，尽管越来越多的人采用基于云的服务，仍然有一些负担需要解决。最重要的是，“云”实际上只是“其他人的硬件”的一个新术语，在其他人的系统上存储数据和工作通常是有成本的，无论是名义上的还是财务上的，或者两者兼而有之。理想情况下，研究产生的软件和模型都将成为免费访问的 Github 库(或类似库)的一部分。很多都是。然而，Github 仍然是一家私人公司，不管那里有多少模型或软件包，在它或任何其他平台上发布数据都有自己的问题。

因为数据科学不仅仅是软件和代码。它还与从软件中产生模型所用的数据有关，这就是问题所在。我们不能总是使用公开可用的数据集来回答每个数据科学问题，试图这样做限制了我们探索现实生活现象的能力。我们不能总是公开我们的数据。

![](img/fa631025fc8d82cb0347f97ce04edc69.png)

Photo by [Steve Johnson](https://www.pexels.com/@steve) on [Pexels](https://www.pexels.com/).

# **受限访问**

虽然自由/开源软件看起来是一个适用于大多数研究软件的美好理想，但是自由/开源软件的概念并不总是适用于数据科学的每一个方面，尤其是在数据共享方面。适用于我们领域的一些最大的数据仓库必然有访问限制。这可能是由于各种各样的原因，但最常见的是隐私和安全。无论我们喜欢与否，这两种力量都不可避免地与数据科学的实践联系在一起。

世界上大多数最大的数据集都由公司持有，对于这些公司来说，数据是其主要的(如果不是唯一的)产品或市场竞争优势。类似地，数据科学最成熟的领域之一，医学数据科学/信息学，有一系列广泛的数据隐私和同意法律，并且有充分的理由。其他不断发展的领域，如运营和制造数据科学，使用的数据可能会揭示关键的业务实践，甚至在关键基础设施的情况下会产生国家安全后果。

这些挑战甚至可以进一步延伸到模型共享，尤其是随着“对抗性数据科学”领域的发展。根据系统的不同，如果你可以访问 API 或类似的接口，就有可能攻击机器学习和深度学习工具来[提取模型信息](https://www.usenix.org/system/files/conference/usenixsecurity16/sec16_paper_tramer.pdf)，甚至[推断数据集成员关系](https://arxiv.org/abs/1610.05820)。这些信息可能足以让坏人造成严重伤害。由于这些重大的安全威胁，许多团体在最小化对他们的模型和数据的访问方面有既得利益。由于披露的不可逆转性，这一点尤其重要。数据集一旦公开发布，就几乎不可能再保护它，而且没有人知道该数据集以后会被用来做什么。

在隐私方面，通常有关于数据隐私和可用性的非常严格的法规和法律。 [HIPAA](https://www.hhs.gov/hipaa/for-professionals/index.html) ，一套在美国保护健康信息披露的复杂规则和条例，是这种不断增长的法规体系的典型例子。随着健康信息和数据科学中新趋势的发现，HIPAA 规则也在不断更新，许多机构现在都有广泛的办公室和培训计划，致力于维护 HIPAA 合规性。

GDPR 是一个更近的例子，一般隐私法规正变得越来越广泛，越来越具有技术意识。作为这些法规有多么重要的一个例子，想一想由于 GDPR 法案的生效，您收到了多少服务条款更新电子邮件。这只是一个地区的一个监管框架。

这些规则和法规是保护公民和组织个人隐私和安全的强大力量，但它们的要求也增加了数据科学家对监管意识的需求，这在我们年轻的领域中有时会被忽视。对于数据科学家来说，重要的是理解并接受这些规定的原因，并找到在规定范围内工作的方法，以免我们成为害群之马。虽然哀叹隐私和安全在我们领域的负担可能很诱人，但整合这些安全措施的强大道德立场将极大地促进我们作为一个领域的未来成功。

![](img/02cf176811af30e2b939c98e3d78e08d.png)

Photo by [Pixabay](https://www.pexels.com/@pixabay) on [Pexels](https://www.pexels.com/).

# **平衡再现性、安全性和隐私性**

数据科学的许多子领域正迅速走向严重的社会和监管障碍。在过去几年中，违规和道德上有问题的使用案例对数据科学这一领域以及我们许多人每天处理的数据的性质产生了负面影响。数据科学的“狂野西部”时代即将结束，这意味着我们需要超越“新算法、相同数据”和“相同算法、新数据”的范式。我们一些最强大的算法已经以意想不到的方式被公开利用，关于一些数据集中包含多少个人信息的更广泛披露让许多公众感到不安。

至此，数据科学已经到了它的“青春期”。仍然存在严重不足的主题，迫切需要新方法和新数据来解决根本问题，但我们也需要共同扩大我们的工作，以公平地讨论和研究数据可用性以及如何在数据可用性与安全性之间取得平衡。

大多数数据科学研究的核心是人类主体研究。我们大多数人都努力尽可能地去识别我们发表的研究的主题，但我们必须仔细区分安全性(在这种情况下，身份检索是不可能的)和模糊性(在这种情况下，身份检索简直令人讨厌)。我们还必须认识到，在许多情况下，由于新的研究和技术会随着时间的推移将强有力的安全措施转变为弱模糊，安全措施很容易被削弱。

一个值得深入研究的有前途的数据安全方法是[差分隐私](https://www.accessnow.org/understanding-differential-privacy-matters-digital-rights/)。从本质上讲，差异隐私是一种在披露前用某种程度的统计不确定性“掺杂”原始数据的方式。然而，正如我们大多数人所知，有了足够大的数据集或足够的系统访问，许多类型的统计不确定性可以被建模和抽象掉。关于一个人在一天中的位置的一个不可靠的数据点可能相对难以验证。连续 100 天内关于一个人位置的 100 个不可靠的数据点远没有那么安全。这只是数据安全措施可能成为相对较弱的数据混淆措施的一个例子。仅仅将隐私注入数据点是不够的。我们还必须考虑受试者或数据集的终生“隐私预算”，而差异隐私的隐私预算难题尚未得到可靠解决。

尽管如此，在这一点上，差分隐私是我们拥有的最好的可扩展选项之一。因此，差分隐私已经被几个主要的基于数据的组织采用，包括[苹果](https://images.apple.com/privacy/docs/Differential_Privacy_Overview.pdf)、[谷歌](https://security.googleblog.com/2014/10/learning-statistics-with-privacy-aided.html)和[美国人口普查](https://www2.census.gov/cac/sac/meetings/2017-09/statistical-disclosure-limitation.pdf)，其中每个组织对不确定性注入和隐私预算都有不同的方法。这些方法没有一个是完美的，但是这些实现导致了对它们的优点和缺点的重要研究。

美国人口普查实际上在技术和监管领域都处于数据隐私和安全的前沿。他们甚至开发了一个经济模型来判断如何管理隐私和准确性之间的平衡。虽然这种方法可能不是最佳解决方案，但它是朝着正确方向迈出的重要一步，评估和管理隐私预算和数据准确性的方法可能会继续发展。

不幸的是，尽管在公开期间对维护数据隐私的方法有很大的努力和兴趣，但在数据科学中很少有可用的方法来建模或算法隐私。这可能会让许多团体，尤其是私人数据公司，不愿分享他们在该领域通常具有开创性的工作。开源和开放获取显然可以有效地进行披露，但对于许多企业研究人员来说，如果允许的话，它们往往只是有选择地实施。迫切需要关于模型和方法披露的新的商业(和研究)伦理，特别是在与数据披露相结合时。我们如何评价一种新的建模方法？我们如何预测我们方法的新用例？我们甚至应该在披露决策中考虑估值吗？这些问题并不容易回答，而且在这一领域工作的数据科学家相对较少，使得这些问题变得更加难以回答。

随着我们领域的发展，这种类型的“元数据科学”工作将变得越来越重要。数据和模型的可用性对该领域的发展至关重要，但随着我们的工作变得更加可见和公开，我们需要不断评估和实施我们的道德披露政策。在数据科学中，我们有一个个人隐私、企业安全和公共利益的多种道德模式相互碰撞的领域，将这些道德整合成一个单一、统一的整体，平衡最大允许披露水平和最高安全水平将需要大量工作。

*走向再现性*

*迈向再现性是一个正在进行的系列文章，讨论数据科学和机器学习中再现性的当前挑战和潜在解决方案。每篇文章都聚焦于推动数据科学中* [*再现性危机的主要因素之一*](/data-sciences-reproducibility-crisis-b87792d88513) *。*