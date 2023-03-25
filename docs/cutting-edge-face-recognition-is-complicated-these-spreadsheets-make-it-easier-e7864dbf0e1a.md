# 前沿的人脸识别很复杂。这些电子表格使它变得更容易。

> 原文：<https://towardsdatascience.com/cutting-edge-face-recognition-is-complicated-these-spreadsheets-make-it-easier-e7864dbf0e1a?source=collection_archive---------2----------------------->

![](img/d2bb7671871319a57933378f168d4ca1.png)

## 在 Excel 中为正常人构建深度卷积神经网络的 9 个步骤。

机器学习可能很复杂……而且刚开始学的时候很吓人。另一方面，电子表格很简单。它们并不*性感，*但是它们去除了干扰，帮助你以直观的方式可视化代码背后发生的事情。

通过一步一步的电子表格(可以使用下面的链接查看或下载)，我将向您展示计算机视觉中使用的卷积神经网络(“CNN”)是如何工作的。有一点数学，但你可以遵循电子表格中的所有公式:

【https://drive.google.com/open? id = 1 tjxppq 6 cz-4kvrxtsrbj 4 u 4 orcaamtpgvy 58 yujbzhk

电子表格模型查看图片，分析其像素，并预测它是否是埃隆马斯克，杰夫·贝索斯，或 rrrr 琼恩·雪诺…显然是天网的最大威胁。

![](img/7c548bd1117ab4658b8047220788a786.png)

Terminator Vision — Creating a convolutional neural net in a spreadsheet

这篇文章将涵盖上述 9 个步骤，并对每个步骤进行类比，以帮助增强你的直觉。

目标是给你一个简单的方法来开始机器学习，并向好奇的头脑展示尖端人工智能如何通过易于遵循的电子表格“在引擎盖下”工作。如果这对你有帮助，请考虑通过点击下面的注册我的电子邮件列表，我将向你发送更多电子表格，帮助你开始机器学习。

[![](img/5de66db1646f8052c65517158a07efa7.png)](http://bit.ly/2uNrJuc)

计算机视觉是脸书面部识别系统、[中国奥威尔式大规模监控](https://www.nytimes.com/2018/07/08/business/china-surveillance-technology.html)以及很快你的汽车:

# 大图类比:CNN 就像夏洛克·福尔摩斯

让我们先假设在终结者的大脑里住着一位名叫“夏洛克·卷积·福尔摩斯”的特殊侦探他的工作是仔细观察证据(输入图像)，并利用他敏锐的眼睛和推理能力(特征检测)，他预测照片中的人并破解案件(正确分类图像)。

以下 9 个步骤中的每一个都是这个大图类比的一部分。

![](img/86c280b65a905971791972341152ac95.png)

Convolutional neural net architecture

![](img/bae9098fb4fa80a75c8fe5b5510b9e80.png)

# 输入——一张图片胜过一千个数字

![](img/1af8368a27fefbe7f9676e48289ff644.png)

Skynet’s biggest threat, Elon Musk

当我看这张照片时，我看到了一个幻想家。一个人在改善地球的同时建造了一个火箭来逃离它，以防终结者试图炸毁它。与计算机不同，我看不到像素值，也看不出图片只是红、绿、蓝光的叠加组合:

![](img/492d93a77718358b61675c2557b1cd01.png)![](img/ef8f06f31ca86f79d5e027b1934d7fde.png)![](img/79af8ccfa66e57837b0e2a9f7b670428.png)

另一方面，计算机(即天网)是盲目的…它只能看到数字。

把一张数码照片想象成 3 个电子表格(1 个红色，1 个绿色，1 个蓝色)堆叠在一起，每个电子表格都是一个数字矩阵。拍照时，您的相机会测量照射到每个像素的红色、绿色和蓝色光量。然后，它按照 0-255 的范围对每个像素进行排序，并将它们记录在电子表格中:

![](img/62df0332321b7349b89ab5ab067b78d2.png)

Computers see spreadsheets

在上面的 28x28 图像中，每个像素由 3 行(1 行红色、1 行蓝色和 1 行绿色)表示，其值为 0–255。像素已经基于它们的值被有条件地格式化。

![](img/45df4553c83a0f615241a7f4caf1161a.png)

Terminator doesn’t see an eye, he sees a bunch of numbers

如果我们将每种颜色分成单独的矩阵，我们有 3 个 28x28 矩阵，每个矩阵都是我们用来训练神经网络的输入:

![](img/eccd4dd7534462934e7a90fa0ffe7945.png)

Model inputs

***** 侧栏:如果你想学习如何在大约 30 秒内将任何图片转换成条件格式的 Excel 文件，请访问:

http://think-maths.co.uk/spreadsheet

你将学会如何拍一张你的电子表格同事会喜欢的“前照片”……相信我，他们会在电子表格中看到你(或他们)的照片而开怀大笑🤳(小图片效果最好)。

# 培训概述—有其父必有其子

当你出生的时候，你知道什么是狗吗？不，当然不是。但是随着时间的推移，你的父母会给你看书籍、漫画、现实生活中的狗的照片，最终…你可以指着那些四条腿的毛茸茸的动物说“狗”你大脑中数十亿神经元之间的联系变得足够强大，以至于你能认出狗。

终结者学会了用同样的方式看待伊隆。通过一个叫做监督训练的过程，向它展示了数千张埃隆·马斯克、杰夫·贝索斯和琼恩·雪诺的照片。起初，它有 1/3 的机会猜出来是谁…但就像一个孩子一样…随着时间的推移，它会在训练中看到更多的图像。网络的连接或“权重/偏差”随着时间的推移而更新，使得它可以基于像素输入来预测图像输出。这就是在[第一部分](https://medium.com/excel-with-ml/machine-learning-with-spreadsheets-part-1-gradient-descent-f9316676db9b)中讨论的学习过程(梯度下降)。

![](img/d26e34e5a8ba40245a93377d653f5cb7.png)

CNN learning to see — the training loop

# 那么是什么使得卷积神经网络不同于普通的神经网络呢？

一言以蔽之:翻译不变性。

是啊…那对我来说也毫无意义。让我们来解构:

*   翻译=将某物从一个地方移到另一个地方
*   不变性=它不会改变

对于计算机视觉来说，这意味着无论物体在图像中被移动到哪里(平移)，都不会改变该物体是什么(不变性)。

![](img/1572f838d055052757ecb4f364b813d9.png)

Translation Invariance (Plus scale invariance to exaggerate the point)

必须训练卷积神经网络来识别 Elon 的特征，不管他在图像中的什么位置(平移)，也不管他的大小(比例不变)。

CNN 擅长识别图像任何部分的模式，然后将这些模式一个接一个地堆叠起来，构建更复杂的模式……就像人类一样。

在正常的神经网络中，我们会将每个单独的像素作为模型的输入(而不是 3 个矩阵)，但这忽略了一个事实，即靠近在一起的像素具有特殊的意义和结构。使用 CNN，我们查看相邻的像素组，这允许模型学习局部模式，如形状、线条等。例如，如果 CNN 看到一个黑色圆圈周围有许多白色像素，它会将这个图案识别为一只眼睛。

为了让 CNN 完成翻译差异，他们依赖于其功能侦探夏洛克卷积福尔摩斯的服务。

![](img/304a26669546f557919f4146f71298f1.png)

# 认识一下夏洛克·康科利·福尔摩斯——特写侦探

![](img/32ee1edd9940f0238ea09a30693384c5.png)

Sherlock searching for features

夏洛克活在终结者的脑海里。他用放大镜一次仔细观察一幅图像的一部分，并找到该图像的重要特征或“线索”。当他收集像简单的线条和形状这样的线索时，他把它们一个接一个地堆叠起来，开始看到像眼睛或鼻子这样的面部特征。

每个卷积层都有一堆相互依赖的特征图或“线索”。在案件结束时，他把所有这些线索放在一起，他能够破解案件，并正确识别他的目标。

![](img/1b4db2d2af4e2b4d1211cb9c7008630a.png)

Each feature map is like another “clue”

网络的每个卷积层都有一组特征图，这些特征图能够以如下所示的分层方式识别日益复杂的模式/形状。

CNN 使用数字的模式识别来找出任何图像最重要的特征。由于它将这些图案堆叠在更多的层上，因此可以构建非常复杂的特征地图。

![](img/4963bef508fe7a8e5d334a80418811c5.png)

现实生活中的 CNN 做着和夏洛克完全一样的事情:

Convolutional neural net detecting features

让 CNN 如此神奇的是，他们自己学会了这些特征…一个工程师不会写代码说寻找一组两个眼睛，一个鼻子，一张嘴，等等。

这样，工程师就更像建筑师了。他们告诉夏洛克，“我给你两叠(“卷积层”)空白特征地图(“线索”)，你的工作是分析图片并找到最重要的线索。第一个堆栈有 16 个特征地图(“线索”)，第二个堆栈有 64 个特征地图…现在去把你的侦探技能派上用场，破案吧！”

![](img/dde28cc03ce14ac76558f772d472e288.png)

为了让夏洛克找到案件中的“线索”(即“计算特征图”)，他依赖于他的侦探工具包中的几个工具，我们将逐一介绍:

*   **滤镜** —夏洛克的放大镜🔍
*   **卷积数学** —滤波器权重 x 输入图像像素
*   **大步走** —在输入图像周围移动滤镜🔍 ➡️ 🔍 ➡️
*   填充材料——像“犯罪现场胶带”一样保护线索🚧

## 夏洛克放大镜/滤光镜

毫无疑问，夏洛克非常敏锐，具有敏锐的观察能力，但如果没有他收集的特殊放大镜或“过滤器”，他就无法完成工作他使用不同的放大镜来帮助他填写每个空白特征地图的细节。所以，如果他有 16 张地图…他会有 16 个放大镜。

![](img/3c51081d678d2868b8b5f63f0b53ac02.png)

每个放大镜由多层玻璃组成，每层玻璃由不同的重量组成。玻璃的层数，我们的“过滤深度”，总是与他正在看的输入层的层深度相匹配。

首先，夏洛克在看我们的输入图像，它有三层——红色、绿色和蓝色。所以…我们的放大镜也有 3 层。

当我们构建 CNN 时，我们的层深度增加，因此我们的放大镜也会变得更厚。

为了让夏洛克构建一个特征图或“线索”,他首先拿出一个放大镜，放在输入图像的左上方。红色玻璃层只能看到红色输入图像，绿色玻璃看到绿色图像，蓝色玻璃看到蓝色图像。

现在是数学问题。

# 卷积数学

我们特征图中的每个像素都是线索的一部分。为了计算每个像素，夏洛克必须做一些基本的乘法和加法。

在下面使用 5x5x3 输入图像和 3x3x3 滤波器的示例中，1 个像素需要 27 次乘法运算:

*   3 层 x 每层 9 个乘法卷积= 27
*   27 个数字中的每一个都加在一起。
*   将 27 个计算值加在一起后，我们再加一个数字——我们的偏差。

Convolution Calculation — Sherlock building his feature maps or “clues”

让我们放大来看看数学。一个像素由 27 个乘法运算组成(3 层 x 每层 9 个乘法运算)，下面的屏幕截图显示了 27 个乘法运算中的 9 个:

![](img/37d0abc97708cba08f2dc1d016a1d73a.png)

Element-wise multiplication — calculating 1 piece of a clue

就偏向而言，你可以把它想象成每个放大镜的手柄。像权重一样，它是模型的另一个参数，在每次训练运行时都会进行调整，以提高模型的准确性并更新特征图细节。

过滤权重——在上面的例子中，我将权重设为 1 和 0，以简化计算；然而，在一个正常的神经网络中，你可以用随机的较低值来初始化你的起始权重…比如使用钟形曲线或正态分布类型的方法在 0.01 和 0.1 之间的值。要了解更多关于重量初始化的信息，请查看此[简介](https://www.youtube.com/watch?v=0mxNQA95mYE)。

# 大步走——移动放大镜

计算完特征图的第一个像素后，夏洛克下一步把放大镜移到哪里？

![](img/7175ee8eac8cc4388fcb2355db892b7b.png)

Striding — Moving magnifying glass 1 pixel at a time

答案取决于步幅参数。作为建筑师/工程师，我们必须告诉夏洛克，在他计算特征图中的下一个像素之前，他应该将放大镜向右移动或“移动”多少像素。2 或 3 的步幅在实践中是最常见的，但是为了简单起见，我们将坚持使用 1。这意味着夏洛克将他的眼镜向右移动 1 个像素，然后他将执行与之前相同的卷积计算。

当他的眼镜到达输入图像的最右边时，他将放大镜向下移动 1 个像素，一直移动到左边。

**为什么你的步幅会超过 1？**

**优点:**

*   通过减少计算量和存储在内存中的计算量来加快模型的速度。

**CONS:**

*   您会丢失关于图片的信息，因为您会跳过像素，并可能错过看到图案。

步长为 2 或 3 通常是有意义的，因为相邻像素通常具有相似的值，但如果它们相距 2-3 个像素，则对于特征图/模式来说很重要的像素值更有可能发生变化。

# 如何防止信息丢失(丢失线索)

为了让夏洛克破案，他需要大量的线索。在上面的例子中，我们拍摄了一个 5x5x3 的图像，或 75 像素的信息(75 = 5 x 5 x 3)，我们最后只得到一个 3x3x2 的图像，或第一个卷积层后的 18 像素(18 = 3 x 3 x 2)。这意味着我们失去了证据，这让他的搭档约翰·沃森非常不安。

![](img/e95a2a25d11e57a52e4a5420c068b143.png)

在 CNN 的前几层，夏洛克喜欢看到许多微小的图案(更多的线索)。在后面的图层中，当夏洛克堆叠微小的线索并查看更大的图案时，可以“向下采样”并减少我们的像素总量(更少的线索)。

那么，我们如何在 CNN 的开头防止这种信息丢失呢？

## #1:填充——我们必须在图像周围用“填充”来保护犯罪现场。

![](img/04b4f58fc98fd81c246289e2ad8f51e7.png)

Padding

在我们的例子中，在到达右边之前，我们只能移动过滤器 3 次…从上到下也是一样。这意味着我们得到的输出高度/宽度是 3x3，我们从左到右损失了 2 个像素，从上到下移动滤镜又损失了 2 个像素。

为了防止这种信息丢失，通常用零“填充”原始图像(称为“零填充”或“相同填充”)…有点像犯罪现场磁带，以确保没有人篡改这样的线索:

![](img/29f0b505374d752a0679b94d9ccccea4.png)

填充后，如果夏洛克再次使用他的放大镜，他的两个特征图将都是 5x5 而不是 3x3。

这意味着我们将剩下 50 个像素的信息，因为这个卷积的新输出是 5x5x2 = 50。

50 像素比 18 像素好。但是记住…我们从 75 像素开始，所以我们仍然缺少一些线索。

那么，我们还能做些什么让夏洛克和约翰·沃森开心呢？

## #2:更多的过滤器——通过在我们的卷积层中添加至少一个特征地图，给夏洛克更多的线索

我们的模型拥有的特征地图或“线索”的数量没有限制…这是一个我们可以控制的参数。

如果我们将特征图从 2 个增加到至少 3 个(5x5x 2…到…5x5x3)，那么我们的总输出像素(75)与我们的输入像素(75)相匹配，并且我们确保没有信息丢失。如果我们把地图增加到 10 个，那么当夏洛克找到他的线索时，我们会有更多的信息需要他整理(250 像素= 5×5×10)。

![](img/d3caa4781295c400fd64a768c49a0cd6.png)

总之，前几层的总像素信息通常高于我们的输入图像，因为我们想给夏洛克尽可能多的微小线索/图案。在我们的网络的最后几层中，向下采样和具有较少像素是常见的，因为这些层识别图像的较大模式。

![](img/d2508f4ee18d9d0f76195355409e075b.png)

# 非线性模式识别— ReLUs

在一个案件中给夏洛克足够的信息是重要的，但是现在是真正的侦探工作的时候了——非线性模式识别！比如耳朵的弯曲或者鼻子的鼻孔。

到目前为止，夏洛克已经做了大量的数学运算来构建他的特征地图，但每次计算都是线性的(获取输入像素并对每个像素执行相同的乘法/加法)，因此，他只能识别像素的线性模式。

为了在 CNN 中引入非线性，我们使用一个激活函数，称为整流线性单元或简称“ReLU”。在我们从第一次卷积计算出我们的特征图之后，每个值都通过这个函数来查看它是亮着还是被“激活”

如果输入值是负的，那么输出变成零。如果输入为正，则输出值保持不变。ReLU 就像一个开/关开关，当您通过 ReLU 运行特征图的每个值后，您就创建了非线性模式识别。

回到我们最初的 CNN 示例，我们将在卷积后立即应用 ReLU:

![](img/1f13dab8903d3f1f4cec096786c36ab4.png)

ReLU = Rectified Linear Unit

虽然有许多非线性激活函数可用于将非线性引入神经网络(sigmoids、tanh、leaky ReLU 等)。)，ReLUs 是目前 CNN 中最常用的，因为它们计算效率高，学习速度更快。查看 Andrej Karpathy 关于非线性激活函数的[概述](http://cs231n.github.io/neural-networks-1/#commonly-used-activation-functions)，了解每个函数的优缺点。

![](img/2f84567ada9bb12f6c2626976bb8debc.png)

# 最大化共享——把关键的几个放在大脑阁楼里

既然夏洛克已经有了一些特征图，或者“线索”，可以开始查看，他如何确定哪些信息是关键的，哪些是不相关的细节呢？最大池化。

夏洛克认为人脑就像一个空荡荡的阁楼。傻瓜会把各种各样的家具和物品放在那里，这样有用的信息最终会在混乱中丢失。聪明的人只储存最重要的信息，以便在需要时能迅速做出决定。这样，max pooling 就是夏洛克版的大脑阁楼。为了让他快速做出决定，他只保留最重要的信息。

![](img/97eda619df170f1ed08d1f000278a1f9.png)

Max Pooling is like Sherlock Holmes ‘Brain Attic’

使用 max pooling，他查看像素邻域，并且只保留“最大”值或“最重要”的证据。

例如，如果他在看一个 2×2 的区域(4 个像素)，他只保留具有最高值的像素，而丢弃其他 3 个像素。这种技术让他学得很快，也帮助他归纳(相对于“记忆”)线索，他可以为将来的图像存储和记忆。

类似于我们前面的放大镜过滤器，我们也控制最大池的步幅和池的大小。在下面的例子中，我们假设步幅为 1，池大小为 2x2:

![](img/627e4d4d7cccc77cfe33bd7c055041c9.png)

Max pooling — picks the “maximum” value in a defined neighborhood of values

在最大池化之后，我们已经完成了一轮卷积/ReLU/最大池化。

在一个典型的 CNN 中，在我们到达我们的分类器之前，会有几轮卷积/ReLU/pooling。对于每一轮，我们会在增加深度的同时压缩高度/宽度，这样我们就不会在途中丢失证据。

第 1-5 步的重点是收集证据，现在是夏洛克查看所有线索并破案的时候了:

![](img/e296bb5c7e5f9b385a522ba3e22da2fd.png)

现在我们有了证据，让我们开始理解这一切..

![](img/03b9d4ec43b4d71b6f3341d0f2c7e31e.png)

当夏洛克到达一个训练循环的末尾时，他有一个分散在各处的堆积如山的线索，他需要一种方法来一次查看所有的线索。每条线索都是一个简单的二维数值矩阵，但是我们有成千上万条这样的线索堆积在一起。

作为一名私人侦探，夏洛克在这种混乱中茁壮成长，但他必须将他的证据带到法庭上，并为陪审团组织起来。

![](img/ca32ac7d1dc9fa20445a9ecbba9058cc.png)

Feature maps prior to flattening

他使用一种简单的变换技术来实现这一点，这种技术叫做展平:

1.  每个二维像素矩阵变成 1 列像素
2.  我们的二维矩阵的每一个都放在另一个的上面。

这是人眼看到的变形的样子…

![](img/bb014819393d714f7a52c3651a2bc9b3.png)

回到我们的例子，这是计算机看到的…

![](img/eb152b62f5d60318203cc326d09fe260.png)

既然夏洛克已经组织好了他的证据，是时候让陪审团相信证据明确指向一名嫌疑人了。

![](img/9100bdf42ebd901bf894dc4060b73436.png)

在全连接层中，我们将证据与每个嫌疑人联系起来。从某种意义上说，我们通过向陪审团展示证据和每个嫌疑人之间的联系，为他们“连接线索”:

![](img/b238816d6d5242ce7c21967977a4655e.png)

Fully connected layer — connecting the evidence to each suspect

使用我们的数字示例，计算机会看到以下内容:

![](img/8f80e2167648bdfb912aefab330737d1.png)

Fully connected layer

在展平层中的每个证据和 3 个输出之间是一堆权重和偏差。像网络中的其他权重一样，当我们第一次开始训练 CNN 时，这些权重将被初始化为随机值，随着时间的推移，CNN 将“学习”如何调整这些权重/偏差，以产生越来越准确的预测。

现在是夏洛克破案的时候了！

![](img/e0e464567bc25f4759fcbbe7a26dc878.png)

在 CNN 的图像分类器阶段，模型的预测是得分最高的输出。目标是让正确的输出得到高分，让不正确的输出得到低分。

该评分功能有两个部分:

1.  Logit 分数—原始分数
2.  soft max-0–1 之间每个输出的概率。所有分数之和等于 1。

# 第 1 部分:逻辑——逻辑分数

每个输出的 logit 得分是一个基本的线性函数:

Logit 得分=(证据 x 权重)+偏差

每条证据都乘以将证据与输出关联起来的权重。所有这些乘法加在一起，我们在最后加上一个偏差项，最高分就是模型的猜测。

![](img/916bd095cc72a023235a53cbd1eb9926.png)

Logit score calculation

那么我们为什么不就此打住呢？2 个直观原因:

1.  夏洛克的自信程度 —我们想知道夏洛克有多自信，这样我们就可以在他高度自信并且正确的时候奖励他……在他高度自信并且错误的时候惩罚他。当我们最后计算损失(“夏洛克的准确性”)时，这个奖励/惩罚被捕获。
2.  **夏洛克的置信加权概率** —我们希望有一种简单的方法将这些概率解释为 0-1 之间的概率，并且我们希望得到与实际输出(0 或 1)相同的预测分数。实际正确的图像(Elon)具有 1，而其他不正确的图像(Jeff 和 Jon)具有 0。把正确的输出变成 1，不正确的输出变成 0 的过程叫做[一键编码](https://medium.com/excel-with-ml/machine-learning-with-spreadsheets-part-1-gradient-descent-f9316676db9b#53c4)。

夏洛克的目标是让他的预测尽可能接近 1，以获得正确的输出。

# 第二部分:soft max——夏洛克的置信加权概率得分

## 2.1.夏洛克的自信程度:

为了找出夏洛克的信心水平，我们用字母 e(等于 2.71828…)乘以 logit 分数。高分成为*非常高的置信度*，低分成为*非常低的置信度*。

这个指数计算也确保了我们没有任何负的分数。因为我们的 logit 分数“可能”是负的，所以假设的 logit 分数在取幂之后会发生什么:

![](img/80e6f0d863266beb700d8edb4ecf063b.png)

The “Confidence” Curve

## 2.2 夏洛克的置信加权概率:

为了找到置信度加权概率，我们将每个输出的置信度度量除以所有置信度得分的总和，这给出了每个输出图像的概率，其总和为 1。使用我们的 Excel 示例:

![](img/5df46d52f9203078e97996d1f160d0aa.png)

Softmax

这个 softmax 分类器很直观。夏洛克认为，终结者看到的照片有 97%的可能性是埃隆·马斯克。

我们模型的最后一步是计算我们的损失。这一损失告诉我们一个侦探夏洛克到底有多好(或多坏)。

![](img/1787816feba877aca468d92ed007b207.png)

每个神经网络都有一个损失函数，我们将预测值与实际值进行比较。随着我们训练 CNN，随着我们调整网络的权重/偏差，我们的预测会提高(夏洛克的侦探技能变得更好)。

CNN 最常用的损失函数是交叉熵损失。在谷歌上搜索交叉熵会出现几个带有大量希腊字母的解释，所以很容易混淆。尽管描述各不相同，但在机器学习的背景下，它们都意味着相同的事情，因此我们将在下面介绍 3 种最常见的方法，以便为您提供帮助。

在处理每个公式变体之前，下面是它们各自的工作:

*   比较正确类别的概率(Elon，1.00)与 CNN 对 Elon 的预测(他的 softmax 得分，0.97)
*   当夏洛克对正确类别的预测接近 1 =低成本时，奖励他👏
*   当夏洛克对正确类别的预测接近 0 时，惩罚他=高成本👎

![](img/5ab0cb83c6855cd31ec651a637954850.png)

These all result in the same answer! 3 different interpretations…

## #1 解释——测量实际概率和预测概率之间的距离

距离捕捉了这样一种直觉:如果我们对正确标签的预测接近于 1，那么我们的成本就接近于 0。如果对于正确的标签，我们的预测接近于 0，那么我们会受到很大的惩罚。目标是最小化正确类的预测(Elon，0.97)和正确类的实际概率(1.00)之间的“距离”。

在解释#2 中讨论了奖励/惩罚“对数”公式背后的直觉。

![](img/0d8fb5d0918f364a3c2ca6e7a440a9a8.png)

Cross Entropy — 1\. Distance Interpretation

## #2 解释——最大化对数可能性或最小化负对数可能性

在 CNN 中，“log”实际上是“自然对数(ln)”的意思，它是 softmax 的步骤 1 中完成的“取幂/置信度”的逆运算。

不是采用实际概率(1.00)减去预测概率(0.97)来计算成本，而是对数计算指数地惩罚夏洛克，他的预测离 1.00 越远。

![](img/23b6c6e4767795da09d0647868cc7771.png)

Cross Entropy — 2\. Log Loss Interpretation

## #3 解释— KL 分歧

KL (Kullback-Leibler)散度衡量我们的预测概率(softmax 得分)与实际概率的偏离程度。

该公式分为两部分:

1.  我们实际概率的不确定性。在机器学习的监督训练的背景下，这总是零。我们 100%确定我们的训练形象是埃隆·马斯克。
2.  如果我们使用我们预测的概率，我们会丢失多少“信息”。

![](img/216d8a8a8f2f62fea8b4a6a403677319.png)

3\. Cross-Entropy — KL Divergence Interpretation

# 包扎

在我们的特别卷积侦探夏洛克·福尔摩斯的帮助下，我们给了终结者一双眼睛，所以他现在有能力寻找并摧毁自由世界的保护者…埃隆·马斯克(抱歉埃隆！).

虽然，我们只训练终结者区分埃隆，杰夫和乔恩…天网有无限多的资源和训练图像在它的处置，所以它可以利用我们已经建立和训练终结者看到任何人或事。

# 订阅更多并分享

如果你喜欢这一点，并希望获得更多优秀的学习和备忘单直接发送到您的收件箱，请点击下面并输入您的电子邮件地址(它们都是免费的)。

[![](img/13edb0c235def2f62198679d848b02f8.png)](http://bit.ly/2Louz37)[![](img/0654cc7ed85a7bf77f47da474e548a1f.png)](https://www.facebook.com/sharer/sharer.php?u=https%3A//towardsdatascience.com/cutting-edge-face-recognition-is-complicated-these-spreadsheets-make-it-easier-e7864dbf0e1a)[![](img/ae5e6db7eff85ed23160cdb85290cf4b.png)](https://twitter.com/home?status=Learn%20Neural%20Nets%20in%20Excel!%20%22Cutting-edge%20face%20recognition%20is%20complicated.%20%20These%20spreadsheets%20make%20it%20easier.%22%20%40ExcelwithML%20https%3A//towardsdatascience.com/cutting-edge-face-recognition-is-complicated-these-spreadsheets-make-it-easier-e7864dbf0e1a)[![](img/d3d744d29f710db18f6af2d0dbb4a5f4.png)](https://twitter.com/@ExcelwithML)

# 其他资源—交互式

*   [抽一个数字，看 CNN 预测](http://scs.ryerson.ca/~aharley/vis/conv/flat.html)
*   [用谷歌+你的网络摄像头训练你自己的 CNN(或者只是观看)](https://experiments.withgoogle.com/teachable-machine)
*   安德烈·卡帕西的实时图像分类模型
*   快速结账。艾的[在 CNN 上的 YouTube 视频](https://www.youtube.com/watch?time_continue=2548&v=9C06ZPF8Uuc)(不是互动的，而是很棒的讲座和深度学习系列)

在这场对抗机器的战争中，我们未来的命运掌握在你的手中😜

![](img/d338c9438162a05b4d5e9d2aefd2744a.png)

Terminator Vision