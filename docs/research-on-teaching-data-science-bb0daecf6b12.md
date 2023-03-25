# 数据科学教学研究

> 原文：<https://towardsdatascience.com/research-on-teaching-data-science-bb0daecf6b12?source=collection_archive---------9----------------------->

*我写这篇文章是作为 2018 年春天在斯坦福大学参加 Hadley Wickham 应用数据科学课程阅读的一部分。*

# 介绍

随着数据科学技能变得越来越重要，数据科学的教学也变得越来越有价值。在数据科学的背景下，我认为教学不是在白板上交谈或给工作表评分的传统过程，而是创造环境和设计体验的过程，这种过程可以为学生带来可衡量的学习。

就定义而言，我对培养学生从数据中提取价值的能力感兴趣(我称之为数据科学)。我感兴趣的学生是任何有算术背景的人，不需要额外的培训，比如说，代数，但不一定有编程或任何级别的严肃统计的背景。

# 美国统计协会建议

美国统计协会(ASA)已经认识到，随着形势的变化，有必要对培训进行调整。2005 年，他们首次提出了关于介绍性统计未来方向的建议，并在 2016 年再次更新了这些建议(ASA 2016)。他们的目标是在大学教授统计学导论，但其中包含的智慧也适用于任何环境下的数据科学教学。以下是他们的建议(第 3 页):

1.  教授统计思维。
2.  注重概念理解。
3.  将真实数据与上下文和目的相结合。
4.  培养主动学习。
5.  利用技术探索概念和分析数据。
6.  使用评估来改进和评估学生的学习。

这些建议中的大部分只是一般的好教学。例如，最近有大量的教育研究指出了主动学习的显著的可测量的益处(C. E. Wieman 2014Koedinger 等人 2015)。还值得指出的是，一些学者认为这些建议指向正确的方向，但仅仅这样还不够(G. Cobb 2015)。

在任何情况下，ASA 建议的关键是批判性思维或决策。Holmes，Wieman 和 Bonn (2015)将批判性思维定义为“基于数据做出决策的能力，及其固有的不确定性和可变性”(第 1 页)。ASA 没有就如何培养学生的批判性思维提供任何明确的指导，但 Holmes，Wieman 和 Bonn (2015)提供了非常简单的建议:“发展这种能力的关键因素是反复练习根据数据做出决定，并对这些决定进行反馈”(第 1 页)。

# 数据科学教学中尚未解决的问题

ASA 的建议和教育研究提供了一些显而易见的建议，如让学生在用技术分析真实数据的同时主动学习；当引入新思想时，注重概念理解，而不是死记硬背；并通过评估来衡量学生的学习。那么，教学数据科学的困难或未解决的部分是什么？我认为有三个:第一，建立一个有利于学习的社会环境或文化；第二，选择技术和设计学习活动，要求学生做出决定；第三，测量或评估学习。

## 1)创造文化

建立一个让学生自由地展示他们自己的知识状态并同情地互相帮助学习的环境是非常困难的。增长思维模式的想法首先由卡罗尔·德韦克提出(德韦克和 Sumoreads 2017)。Jo Boaler 特别在数学课堂的背景下讨论了成长思维模式，并恰当地将其称为“数学思维模式”(Boaler 2016)。他们的研究指出了学生相信他们可以通过实践提高的重要性。或许更有趣的是，他们提供了如何培养成长心态的建议，比如赞扬努力而不是技能(Khan 2014)。

我喜欢“数据科学思维”的想法建立这样一种心态尤其重要的是让学生进行批判性思考，并作为一个群体做出决定。为了有效地做到这一点，学生们需要在社交上彼此特别自在。人类可能是害羞的动物。创造环境来克服这种趋势，让学生们彼此深入交流，分享想法，并富有成效地挑战彼此的想法是极其困难的。

我见过的实现这个目标的最接近魔术的方法是即兴表演。从我的经验来看，学生们可以害羞和不自信地进入一个房间，几个小时后通过一起即兴表演，彼此之间完全舒服了。《第二城市课堂即兴表演指南》一书详细介绍了课堂即兴表演的好处以及具体的活动建议(McKnight 和 Scruggs 2008)。这些技术可以很容易地适应数据科学环境，例如，让学生作为一个小组表演一个函数做什么，让学生在遇到错误时热情地大喊“耶”，或者要求学生在头脑风暴如何解决数据科学问题时以“是的，并且…”开始句子。这些想法可能会让一些人觉得很傻，但实际上这是最基本的要素。

教师经常忽略有目的地建设文化。在我看来，没有比这更大的错误了。投资课堂文化，尤其是在开始阶段，会带来巨大的回报。如果一个老师没有明确地构建文化，课堂的文化很可能会变得类似于课堂之外的“真实世界”的文化，这对于来自往往在分析圈子中被边缘化的背景的学生来说尤其有害。从本质上说，建设文化既是一个公平和有效性的问题(P. Cobb 和 Hodge 2011)。

## 2)选择技术和设计学习活动(要求学生做出决定)

学习技术的选择归结为管理一门课程的能量。如果精力花在学习技术的细节上，那么用于其他主题的精力就会减少。然而，认识到一些学习技术比其他技术对学生来说更有价值也很重要。例如，使用 R(相对于特定用途的学习小程序)可能会为课程带来更高的成本，但在课程结束后对学生也有更大的潜在价值。

在使用激励视频、真实数据和免费软件学习统计数据时，Harraway (2012)提倡使用 GenStat 软件进行教学(GTL ),这是专业软件 GenStat 14 的淡化版本。GTL 旨在占据电子表格和高级数据分析软件之间的中间地带，完全由菜单驱动，专注于基本统计需求的易用性，如转换数据、模型拟合、假设检验和引导。创作者通过在几个教室试用该软件，然后观察和调查结果来衡量该软件的有效性——例如，在 41 名学生中，只有 6 名学生认为 GTL 很难使用。GTL 也有与其特色直接相关的学习活动和视频。

Harraway (2012)承认 R 是 GTL 的最大竞争对手，但不断强调不必要的复杂性和因需要编程和语法而导致的挫折感。我发现这是这篇论文提出的最有趣的问题。使用专业软件，消除初学者的复杂性，设计有目的的学习活动似乎是一个好主意，但我很难接受基于菜单是必需的甚至是可取的功能这一论点。我之前认为，对于所有学生来说，与基于语法的程序进行互动是一个很好的练习，并且通过良好的课程设计和教学，可以使这种互动变得不那么痛苦。无论如何，为学习者特别设计的轻量级软件的基本点是有趣的。

在 FiveThirtyEight R Package:统计学和数据科学入门课程的“驯服数据”原则中，Kim、Ismay 和 Chunn (2018)没有描述如何使软件变得更简单，而是倡导以一种要求学生专注于重要障碍的方式驯服数据。例如，首先以整齐的格式提供数据，这样学生就不必担心数据的整形。他们将这一建议付诸行动，提供了一个记录良好的 R 包，其中包含来自数据驱动的新闻网站 FiveThirtyEight 的数据集。

他们的基本原则是，学生需要学习数据科学的“整个游戏”,而不是一次只学习一个孤立的部分，但通过将学生抛入深渊来这样做是适得其反的，因为学生经常会在低收益概念或他们尚未准备好的概念上打转。因此，解决方案是基于有目的地策划的数据来设计学习体验，让学生体验数据科学的整个游戏，并在正确的时间遇到正确的障碍(例如，富有成效的斗争)。我认为这正是数据科学教师应该持有的正确心态。非常困难的部分是设计数据集和这种目的水平的学习体验。提供的 R 包是一个好的开始。

关于数据科学教学技术的第三篇论文是使用 R 和 Shiny 的统计数据 Web 应用教学工具(Potter 等人，2016 年)。他们指出，小程序可以成为强大的教学工具，尤其是帮助学生建立直觉。然而，构建小程序需要专业技术知识和大量的时间。Shiny 大大简化了这个过程。这篇论文附带了一个网站，展示了各种令人印象深刻的小程序。

相对于课程中使用的主要软件，小程序似乎有些不重要，但我实际上认为教师为他们的教室设计闪亮的应用程序可能非常有价值，特别是如果与深思熟虑的驯服数据练习相结合。想象一下，一个学生处理一个平淡无奇的数据分析，但是在这个过程中遇到了令人毛骨悚然的统计概念，有一个专门为数据分析设计的小程序可以帮助学生建立统计直觉。这可能非常强大。

总之，我在关于数据科学的技术使用和活动设计的文献中看到的最大差距是没有足够重视实际要求学生做出决定。不要问学生某人准时上班的概率有多大，而是问他们建议这个人什么时候离开。不要问学生治疗效果如何，如果有不同的效果，问他们会把药物给谁，有一百万美元的固定预算。

然后对过程和决策给出反馈。例如:

你的团队把药给了年轻男性而不是年长女性，因为你没有正确解释选择偏差。10 名年轻男子被治愈，但机会成本是 1000 名老年妇女的生命。您应该在回归中控制邮政编码，而不是州。也许您忽略了这一点，因为您在清理数据时没有将地理变量放在一起(参见第一个脚本的第 22 行)。”

想象一下这与通常的反馈有多么不同:

*“你对异质效应的估计似乎是错误的，也许是因为你没有正确解释选择偏差。”*

我的观点是，高质量数据科学活动的重要部分是提出专注于决策和设计活动的问题，以便学生遇到重要的障碍，而学生没有准备好面对的障碍则通过仔细的数据整理被离散地消除。老师还需要深入理解数据的每一个细节，以便他们能够快速识别学生的位置，并引导他们朝着正确的方向前进。真实世界的数据当然是首选，但如果这需要使用感觉真实的模拟数据，我认为这也没问题。

# 3)测量/评估学习

数据科学是关于决策的，而决策是很难衡量的。机器可分级的格式似乎并不奏效，而且替代方案非常耗时且主观。此外，理想的数据科学学习成果通常是长期的，与学生对数据科学的关系和实际掌握技能一样重要。考虑到这一点，也许课程调查和收集学生信心和情绪的数据与传统的教育评估一样有价值(Wirth and Perkins 2005)。

总之，在有效测量和评估数据科学学习的道路上，我们还有很多山要爬。Maurer 和 Lock (2016)提供了一个有趣的起点，他们将爱荷华州立大学的学生随机分配到基于模拟或传统的推理课程中，并比较学生在针对特定学习目标的问题上的前后测试收获。类似的例子见于 C. Wieman 和 Holmes (2015 年)。一个有希望的未来方向是考虑项目评估，它从更广阔的角度来衡量。Moore 和 Kaplan (2015)通过评估佐治亚大学本科统计学专业提供了一个例子。

# 文献学

*   阿萨。2016."统计教育评估和指导指南-学院报告."[http://www . amstat . org/asa/files/pdf/GAISE/GAISE college _ full . pdf](http://www.amstat.org/asa/files/pdfs/GAISE/GaiseCollege_Full.pdf)。
*   Boaler，J. 2016。“数学思维。”加利福尼亚州旧金山:乔西-巴斯。
*   科布乔治。2015.“单纯的革新太少也太迟了:我们需要从头开始重新思考我们的本科课程。”美国统计学家 69④。泰勒和弗朗西斯:266–82。
*   科布，保罗，林恩廖霍奇。2011."数学课堂中的文化、身份和公平."《数学教育研究之旅:保罗·科布作品中的洞见》, Anna Sfard，Koeno Gravemeijer 和 Erna Yackel 编辑，179–95 页。多德雷赫特:荷兰施普林格。
*   德韦克，卡罗尔 s，和 Sumoreads。2017.卡罗尔 s .德韦克的心态总结:关键要点与分析。创建空间独立发布平台。
*   约翰·哈罗维，2012 年。"使用激励视频、真实数据和免费软件学习统计学."统计教育中的技术创新 6 (1)。[https://escholarship.org/uc/item/1fn7k2x3](https://escholarship.org/uc/item/1fn7k2x3)。
*   N. G .福尔摩斯卡尔·E·威曼和波恩地方检察官。2015.“教授批判性思维。”美国国家科学院院刊 112(36):11199–204。
*   可汗萨尔。2014."学习神话:为什么我永远不会告诉我的儿子他很聪明."可汗学院。2014.[https://www . khanacademy . org/talks-and-visitors/conversations-with-sal/a/the-learning-myth-why-ill-never-tell-my-son-hes-smart](https://www.khanacademy.org/talks-and-interviews/conversations-with-sal/a/the-learning-myth-why-ill-never-tell-my-son-hes-smart)。
*   金、艾伯特·y、切斯特·伊斯梅和詹妮弗·楚恩。2018." FiveThirtyEight R 包:统计学和数据科学入门课程的“驯服数据”原则."统计教育中的技术创新 11 (1)。【https://escholarship.org/uc/item/0rx1231m】T4。
*   Koedinger，Kenneth R .，Jihee Kim，Julianna 祝新贾，Elizabeth A. McLaughlin 和 Norman L. Bier。2015."学习不是一项观赏性运动:从 MOOC 中学习，做比看更好."第二届(2015 年)ACM 学习会议论文集，第 111-20 页。L@S '15。美国纽约州纽约市:ACM。
*   毛雷尔，卡斯滕和丹尼斯·洛克。2016."在一个设计的教育实验中，基于模拟和传统推理课程的学习结果的比较."统计教育中的技术创新 9 (1)。[https://escholarship.org/uc/item/0wm523b0](https://escholarship.org/uc/item/0wm523b0)。
*   麦克奈特，凯瑟琳 s 和玛丽斯克鲁格斯。2008.第二城市课堂即兴表演指南:利用即兴表演教授技能和促进学习。约翰·威利父子公司。
*   摩尔、艾莉森·阿曼达和詹妮弗·j·卡普兰。2015."本科统计学专业的项目评估."美国统计学家 69④。泰勒和弗朗西斯:417–24。
*   波特、盖尔、黄谷悦、欧文·阿尔卡拉斯、彼得·池等人。2016." Web 应用统计教学工具使用 R 和 Shiny . "统计教育中的技术创新 9 (1)。[https://escholarship.org/uc/item/00d4q8cp](https://escholarship.org/uc/item/00d4q8cp)。
*   斯特恩丹。2017.“自学数据科学:我用来在 Jet.com 获得分析工作的学习途径”，2017 年。[https://medium . freecodecamp . org/a-path-for-you-learn-analytics-and-data-skills-BD 48 ccde 7325](https://medium.freecodecamp.org/a-path-for-you-to-learn-analytics-and-data-skills-bd48ccde7325)。
*   斯塔滕，萨维纳·范德。2017.“离开我的风投工作，去学习数据科学和机器学习。”2017.[https://towards data science . com/leaving-my-VC-job-to-learn-about-data-science-and-machine-learning-4 DBC 15427 fc 5](/leaving-my-vc-job-to-learn-about-data-science-and-machine-learning-4dbc15427fc5)。
*   卡尔·威曼，2014 年。"科学教学方法的大规模比较传达了明确的信息."美国国家科学院学报 111(23):8319–20。
*   威曼、卡尔和 N. G .霍姆斯。2015."测量物理入门实验室对学习的影响."arXiv[物理学博士]。arXiv。[http://arxiv.org/abs/1507.00264](http://arxiv.org/abs/1507.00264)。
*   沃思，卡尔 r，和德克斯特帕金斯。2005."知识调查:不可或缺的课程设计和评估工具."教与学的学术创新。serc.carleton.edu。[http://serc . carleton . edu/files/garnet/knowledge _ surveys _ indepensabl _ 1313423391 . pdf](http://serc.carleton.edu/files/garnet/knowledge_surveys_indispensabl_1313423391.pdf)。