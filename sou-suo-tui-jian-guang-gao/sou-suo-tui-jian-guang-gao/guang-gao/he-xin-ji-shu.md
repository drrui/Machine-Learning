# 核心技术

广告技术的核心目标其实可以用一个公式来表达： $$f(u,s,a)$$ ，其中 $$u$$ 是用户， $$s$$ 是场景， $$a$$ 是广告，我们所要做的就是找到这样一个函数 $$f$$ ，让用户在合适的场景下看到适合的广告。

## 发展趋势

广告技术发展的业界趋势总的来说是从宏观特征、简单模型逐步演进到采用微观特征、复杂模型。

![](../../../.gitbook/assets/screenshot-from-2019-11-24-22-34-27.png)

做广告就像做饭一样，原材料是数据、特征，模型是我们的工具： 

阶段1：广告技术初期采用传统机器学习方法，例如LR等模型，这就要求大量的特征工程，但特征工程我们都知道，需要很深的业务理解而且比较玄学，就像我们要炒土豆，但是刀工不行，只能切片，如果进行简单的醋溜后能吃，但是不够入味，要是切片不够薄还容易生。

阶段2：采用了深度学习技术以后，我们避免的大量的特征工程，只需收集合理数据放入模型，模型会自己学习提取有价值特征，如同手握合适的土豆去皮器，有了擦丝工具，可以做醋溜土豆丝，并且味道直接提升一个层次。

阶段3：大胆预测下一技术阶段是知识图谱加深度学习，上了深度学习我们有了顺手的厨卫工具了，知识图谱能提供什么呢？1、新的原材料，简单来说，简单的广告投放场景就像炒西红柿，对原材料和工具的要求都不大，但复杂的场景广告有如做佛跳墙，材料都不太够肯定不地道，而图谱可以提供一些额外的数据、特征等；2、调料，有了原料和工具，调料不好味道也不行，图谱可以提供一些结构化信息，可以用来加约束更好关联用户、场景和广告，相当于给我们配齐了从南亚到东北亚各式调料。当然，有了新的原料和调料，锅得大啊，所以知识图谱的合理构建就是首先要解决的问题。再有材料多了，火候也要跟上，机器的运算力，对实时性的要求，也是一个挑战。

现阶段处在阶段2到阶段3的过渡时期，将丰富的特征和Embedding后的图谱信息代入深度学习模型中去。总而言之，数据是我们的核心，若食材为佳品，清水蒸也是美味。然而由于现实之复杂，我们无法知晓哪些数据是佳品，所以增加数据的细节程度及涵盖范围\(特征从宏观到微观\)，使用工具及调料\(模型由简单到复杂\)进行烹饪，得到味道越来越好的菜品。



## 核心问题

### CTR/CVR预估

CTR

CVR

### 智能定向

用户定向

内容定向

## 技术难点

### 高维稀疏

高维稀疏的问题简单来说就是以下两点：

* 数据高维稀疏，用户、商品、场景特征维度很高。
* 正样本少，点击样本少，转化样本极其少，而且不同平台转化跟踪还需解决。

正样本少的问题，不同平台有各自的难点，有的正样本量级可能是千分之几，有的可能是万分之几，甚至十万百万分之几的量级。不仅正样本少，还有一些获取问题

* 转化影响问题，比如广告主比较有钱，广告投了很多平台，我刷抖音、知乎、微博时都刷到了三亚旅游的广告，先在抖音上看到引起了兴趣，过几天刷知乎时也看到这个广告且已经决定要去正在做攻略，又过几天在微博上又一次看到这个广告，直接决定点击进行购买。用户只要在平台点击广告，平台就会发送信息，现在有三个媒体平台信息，广告主将这次转化归给最后一次。这就造成了，对前面转化造成影响的平台不公平，且若用户看了后有兴趣但不点击广告，自行去搜索，这样转化数据更难以记录。
* 转化滞后问题，比如游戏App广告，我们规定用户充钱才算转化，如果从爱奇艺平台入口点击、下载、安装、注册、试玩，但是半年后才充钱，这种由于转化滞后性的问题如何解决。现在naive的方法是转化的样本是1，给以样本权重，比如安装0.1，注册0.3，试玩0.6的正样本概率等；再者增加转化追踪时长，一般一个样本7天内未完成转化就当负样本了，现在由于存储量的升级，可以追踪更多用户，追踪更长的时间窗口。

从媒体平台角度来看，越接近用户日常的，特征越多，比如微博、知乎等；越接近转化出口的，转化数据越多，比如淘宝、美团等。所以如果有一个完整的生态体系，可以有更好的机会去解决这个问题。媒体平台越接近转化出口的平台越好做。淘宝、美团等转化直接就在平台完成，有丰富的转化数据。

### 实时性

