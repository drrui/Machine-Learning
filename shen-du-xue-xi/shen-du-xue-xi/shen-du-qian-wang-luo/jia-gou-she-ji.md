# 架构设计

神经网络设计的另一个关键点是它的架构。架构一词是指网络的整体结构：它应该具有多少单元，以及这些单元应该如何连接。说白了就是网络应该多深\(有几层\)、每层应该多宽\(当前层有多少单元\)、每层之间怎么连接\(是前一层的分别全连当前层还是其他方式\)。

即使只有一个隐藏层的网络也足够适应训练集。更深层的网络通常能够对每一层使用更少的单元数和更少的参数，并且经常容易泛化到测试集，但是通常也更难以优化。

## 万能近似性质和深度

[万能近似定理\(Universal approximation theorem\)](https://en.wikipedia.org/wiki/Universal_approximation_theorem)表明，一个前馈神经网络如果具有线性输出层和至少一层具有任何一种“挤压”性质的激活函数的隐藏层，只要给与网络足够数量的隐藏单元，它可以以任意的精度来近似任何从一个有限维空间到另一个有限维空间的Borel可测函数。前馈网络的导数也可以任意好的来近似函数的导数。即只要给予符合条件的层和足够的隐藏单元，前馈神经网络可以表示任何函数。

万能近似定理意味着无论我们试图学习什么函数，我们知道一个大的MLP一定能够表示这个函数。然而，我们不能保证训练算法能够学得这个函数。即使MLP能够表达该函数，学习也可能因两个不同的原因而失败：首先，用于训练的优化算法可能找不到用于期望函数的参数值。其次，训练算法可能由于过拟合而选择了错误的函数。

## 其他架构上的考虑

到目前为止，我们都将神经网络描述成层的简单链式结构，主要的考虑因素是网络的深度和每层的宽度。许多架构构建了一个主链，但随后又添加了额外的架构特性，例如从层 $$i$$ 到层 $$i+2$$ 或者更高层的跳跃连接。这些跳跃连接使得梯度更容易从输出层流向更接近输入的层。
