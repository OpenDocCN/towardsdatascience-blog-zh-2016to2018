# 如何创建嵌入 TensorFlow 的单词

> 原文：<https://towardsdatascience.com/how-to-create-word-embedding-in-tensorflow-ed0a61507dd0?source=collection_archive---------8----------------------->

![](img/e354f7522b2e0091d9e8300f3e213421.png)

Photo by [Vincentiu Solomon](https://unsplash.com/photos/ln5drpv_ImI?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on [Unsplash](https://unsplash.com/search/photos/stars?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)

*三种不同的方式*

**你可以在这里** 找到这篇文章的 Jupyter 笔记本[](https://github.com/FrancescoSaverioZuppichini/How-To-Embed-in-TensorFlow/blob/master/notebook.ipynb)

**今天我们将看到如何使用张量流创建单词嵌入。**

***更新至 tf 1.9***

**[单词嵌入](https://en.wikipedia.org/wiki/Word_embedding)是通过创建高维向量空间来表示单词的一种方式，在高维向量空间中，相似的单词彼此接近。**

**长话短说，神经网络和数字一起工作，所以你不能只是把单词扔进去。你可以一次性编码所有的单词，但是你会失去它们之间相似性的概念。**

**通常，几乎总是，你把你的嵌入层放在神经网络的前面。**

# **预处理**

**通常，你有一些文本文件，你从文本中提取标记，你建立词汇。类似于下面的代码**

**然后**

**这是一个非常简单的例子，你通常需要更多的预处理来并行打开多个文本源，创建令牌和创建 vocab。例如，您可以使用 PySpark 有效地预处理文本。**

**让我们打印词汇**

```
{'abutere': 0, 'ad': 1, 'audacia': 2, 'catilina': 3, 'effrenata': 4, 'eludet': 5, 'etiam': 6, 'finem': 7, 'furor': 8, 'iactabit': 9, 'iste': 10, 'nos': 11, 'nostra': 12, 'patientia': 13, 'quamdiu': 14, 'quem': 15, 'quo': 16, 'sese': 17, 'tandem': 18, 'tuus': 19, 'usque': 20}
```

**现在我们需要定义嵌入大小，也就是每个向量的维数，在我们的例子中是 50，以及词汇长度**

```
21
```

**我们知道需要定义想要嵌入的单词的 id。举个例子，我们将带着*阿布蒂雷*和*巴提尼亚***

**只是为了确定你在跟踪我。代表词汇表中某些单词的 id。词汇表是单词(令牌)到 id 的映射。**

**为什么我们必须这么做？神经网络与数字一起工作，所以我们必须将一个**数字**传递给嵌入层**

# **“本地”方法**

**为了嵌入，我们可以使用低级 API。我们首先需要定义一个大小为`[VOCAL_LEN, EMBED_SIZE]` (20，50)的矩阵，然后我们必须使用`tf.nn.embedding_lookup`告诉 TensorFlow 在哪里寻找我们的单词 id。**

**`tf.nn.embedding_lookup`创建一个操作，根据第二个参数的索引检索第一个参数的行。**

```
[[0.2508639 0.6186842 0.04858994 0.5210395 0.46944225 0.93606484 0.31613624 0.37244523 0.8245921 0.7652482 0.05056596 0.82652867 0.637517 0.5321804 0.84733844 0.90017974 0.41220248 0.659974 0.7645968 0.5598999 0.40155995 0.06464231 0.8390876 0.139521 0.23042619 0.04655147 0.32764542 0.80585504 0.01360166 0.9290798 0.25056374 0.9695363 0.5877855 0.9006752 0.49083364 0.5052364 0.56793296 0.50847435 0.89294696 0.4142543 0.70229757 0.56847537 0.8818027 0.8013681 0.12879837 0.75869775 0.40932536 0.04723692 0.61465013 0.97508 ] [0.846097 0.8248534 0.5730028 0.32177114 0.37013817 0.71865106 0.2488327 0.88490605 0.6985643 0.8720304 0.4982674 0.75656927 0.34931898 0.20750809 0.16621685 0.38027227 0.23989546 0.43870246 0.49193907 0.9563453 0.92043686 0.9371239 0.3556149 0.08938527 0.28407085 0.29870117 0.44801772 0.21189022 0.48243213 0.946913 0.40073442 0.71190274 0.59758437 0.70785224 0.09750676 0.27404332 0.4761486 0.64353764 0.2631061 0.19715095 0.6992599 0.72724617 0.27448702 0.3829409 0.15989089 0.09099603 0.43427885 0.78103256 0.30195284 0.888047 ]]
```

# **喀拉斯层**

**我不是 keras 的粉丝，但它可能是有用的。您可以使用独立的层来创建嵌入**

```
[[0.9134803 0.36847484 0.51816785 0.19543898 0.07610226 0.8685185 0.7445053 0.5340642 0.5453609 0.72966635 0.06846464 0.19424069 0.2804587 0.77481234 0.7343868 0.16347027 0.56002617 0.76706755 0.16558647 0.6719606 0.05563295 0.22389805 0.47797906 0.98075724 0.47506428 0.7846818 0.65209556 0.89036727 0.14960134 0.8801923 0.23688185 0.70695686 0.59664845 0.6206044 0.69665396 0.60709286 0.42249918 0.7317171 0.03822994 0.37915635 0.60433483 0.4168439 0.5516542 0.84362316 0.27857065 0.33540523 0.8601098 0.47720838 0.9827635 0.09320438] [0.27832222 0.8259096 0.5726856 0.96932447 0.21936393 0.26346993 0.38576245 0.60339177 0.03083277 0.665465 0.9077859 0.6219367 0.5185654 0.5444832 0.16380131 0.6688931 0.82876015 0.9705752 0.40097427 0.28450823 0.9425919 0.50802815 0.02394092 0.24661314 0.45858765 0.7080616 0.8434526 0.46829247 0.0329994 0.10844195 0.6812979 0.3505745 0.67980576 0.71404254 0.8574227 0.40939808 0.8668809 0.58524954 0.52820635 0.31366992 0.05352783 0.8875419 0.04600751 0.27407455 0.6398467 0.74402344 0.9710648 0.5717342 0.78711486 0.9209585 ]]
```

# **张量流层**

**由于 Tensorflow 很混乱，总是有几种方法来做同样的事情，并且不清楚应该使用哪一种，所以毫不奇怪还有另一个函数来创建嵌入。**

```
[[ 0.11656719 -0.21488819 0.04018757 -0.18151578 -0.12417153 -0.00693065 0.27286723 0.00712651 -0.05931629 -0.20677638 0.14741448 -0.24938995 -0.21667814 0.09805503 0.2690411 0.20826831 0.19904876 0.08541816 0.20128882 0.15323257 -0.0386056 0.03025511 0.11573204 0.2161583 -0.02596462 -0.15845075 -0.26478297 -0.13366173 0.27797714 -0.08158416 -0.25292248 -0.16360758 -0.1846793 0.2444193 0.13292032 0.15807101 0.24052963 -0.0346185 0.02243239 0.2350963 -0.0260604 0.12481615 -0.1984439 0.20924723 -0.00630271 -0.26579106 0.04491454 0.10764262 0.170991 0.21768841] [-0.09142873 -0.25572282 0.2879894 -0.2416141 0.0688259 -0.06163606 0.2885336 -0.19590749 -0.04164416 0.28198788 0.18056017 -0.03718823 -0.09900685 0.14315534 -0.25260317 -0.00199199 -0.08959872 0.23495004 -0.18945126 -0.16665417 0.18416747 0.05468053 -0.23341912 0.02287021 0.27363363 0.07707322 -0.02453846 0.08111072 0.12435484 0.12095574 0.2879583 0.12930956 0.09152126 -0.2874632 -0.26153982 -0.10861655 -0.01751739 0.20820773 0.22776482 -0.17411226 -0.10380474 -0.14888035 0.01492503 0.24255303 -0.10528904 0.19635591 -0.22860856 0.2117649 -0.08887576 0.16184562]]
```

# **编写自己的模块**

**您可以使用经典范例`__init__` + `__call__`来创建您的定制类。**

```
[[0.19501674 0.954353 0.30957866 0.65923584 0.28241146 0.80623126 0.46677458 0.5877205 0.25624812 0.03041542 0.24185908 0.8056189 0.61915445 0.04368758 0.16852558 0.24910712 0.66250837 0.01929498 0.82387006 0.8489572 0.3970251 0.8156922 0.5550339 0.39991164 0.64657426 0.1980362 0.35962176 0.89992213 0.99705064 0.7636745 0.5627477 0.09286976 0.12509382 0.9644747 0.3412783 0.3238287 0.08844066 0.06885219 0.2377944 0.04519224 0.6535493 0.39360797 0.69070065 0.44310153 0.58286166 0.32064807 0.9180571 0.47852004 0.6686201 0.44279683] [0.0843749 0.77335155 0.14301467 0.23359239 0.77076364 0.3579203 0.95124376 0.03154683 0.11837351 0.622192 0.44682932 0.4268434 0.21531689 0.5922301 0.12666893 0.72407126 0.7601874 0.9128723 0.07651949 0.7025702 0.9072187 0.5582067 0.14753926 0.6066953 0.7564144 0.2200278 0.1666696 0.63408077 0.57941747 0.9417999 0.6540415 0.01334655 0.8736309 0.4756062 0.66136014 0.12366748 0.8578756 0.71376395 0.624522 0.22263229 0.35624254 0.00424874 0.1616261 0.43327594 0.83355534 0.51896024 0.53433514 0.47303247 0.7777432 0.4082179 ]]
```

# **预训练嵌入**

**您可以通过使用预训练的单词嵌入来获益，因为它们可以提高模型的性能。他们通常用庞大的数据集来训练，例如维基百科，用跳过语法模型的词袋。**

**有几个已经训练好的嵌入，最著名的是 [word2vec](https://arxiv.org/abs/1301.3781) 和 [Glove](https://nlp.stanford.edu/pubs/glove.pdf) 。**

**你可以在这篇 [tensorflow tutoria](https://www.tensorflow.org/tutorials/representation/word2vec) l 和这篇[文章](/learn-word2vec-by-implementing-it-in-tensorflow-45641adaf2ac)中读到更多关于训练单词嵌入以及如何从头开始训练它们的内容**

**在过去，加载到 TensorFlow 预训练的单词嵌入并不容易。你必须从某个地方下载矩阵，加载到你的程序中，并可能再次存储它。现在，我们可以使用 **TensorFlow Hub** 。**

# **张量流集线器**

**您可以通过 TensorFlow hub 轻松使用预训练的单词嵌入:一个预训练模块的集合，您可以在代码中导入它。完整列表在[这里](https://www.tensorflow.org/hub/modules/text)**

**让我们看看它的实际效果。**

**顺便说一句，TensorFlow Hub 有缺陷，在木星上不能很好地工作。或者至少在我的机器上，你可以试着运行它，看看它是否适合你。在 PyCharm 上我没有任何问题，所以我将复制并粘贴输出。**

**如果您有同样的问题，请在 TensorFlow 资源库上打开一个问题。**

**你也可以通过将`hub.Module`构造器的`trainable`参数设置为`True`来重新训练它们。当您有一个特定领域的文本语料库，并且希望您的嵌入专门针对该语料库时，这是非常有用的。**

**`hub.Module("https://tfhub.dev/google/Wiki-words-250-with-normalization/1", trainable=True)`**

# **结论**

**现在，您应该能够在 TensorFlow 中高效地创建单词嵌入层了！**

**你可能也会觉得下面这篇文章很有趣**

**[](/how-to-use-dataset-in-tensorflow-c758ef9e4428) [## 如何在 TensorFlow 中使用数据集

### 内置的输入管道。再也不用“feed-dict”了

towardsdatascience.com](/how-to-use-dataset-in-tensorflow-c758ef9e4428) [](/reinforcement-learning-cheat-sheet-2f9453df7651) [## 强化学习备忘单

### 声明:这是一个正在进行中的项目，可能会有错误！

towardsdatascience.com](/reinforcement-learning-cheat-sheet-2f9453df7651) 

感谢您的阅读，

弗朗西斯科·萨维里奥·祖皮奇尼**