# 数据集增强

使用更多的样本数据训练模型可以获得更好的泛化性能，然而，实践中我们很难获得更多的训练数据。一种解决方法是人为创造一些合理的假数据并把它们添加到训练集。

这样的方法对于分类任务来说是最简单的。一个分类器需要有能力把一个复杂高维的输入 $$x$$ 映射到单一类目的输出 $$y$$ ，因此分类器需要对大量 $$x$$ 的变换保持预测结果的不变，即对于相似的输入需要有相同的输出。因此，我们可以轻易地转换训练集中的 $$x$$ 来生成新的 $$(x,y)$$ 对。例如，对于图像识别任务来说，像素的部分平移、缩放、旋转操作并不会改变图片中物体对语义表达，因而我们可以使用这些操作来生存新对训练数据。数据集增强对于语音识别任务也是有效的。

另一种数据集增强的方法是向网络的输入层注入噪声。神经网络已被证明对噪声不是非常健壮。简单地将随机噪声施加到输入再进行训练可以改善神经网络的健壮性。对于某些模型，在模型的输入上添加方差极小的噪声等价于对权重施加范数惩罚（Bishop）。

研究表明，将噪声施加到网络的隐藏层也是有效的，这可以被看成是在多个抽象层上进行数据集增强。著名的Dropout方法可以看作是对隐藏层输出乘以一个噪声后输出到下一层。

