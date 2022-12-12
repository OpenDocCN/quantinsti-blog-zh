# 蒙特卡洛分析简介

> 原文：<https://blog.quantinsti.com/introduction-monte-carlo-analysis/>

*本文最初发布在 Quants 门户网站上。*

由[博诺洛·莫洛皮扬](https://www.linkedin.com/in/bonolo-molopyane-001a5a73/)

安德森等人(1999)将充满神秘色彩的蒙特卡洛定义为通过模拟变量函数的样本均值来逼近期望值的艺术。在斯坦·乌兰姆和约翰·冯·诺依曼(Anderson，1999 年)之间，蒙特卡罗(Monte Carlo)一词曾被用作建造更好的原子弹的随机模拟的一个代号，后来演变成一种用于多种学科的方法，包括物理、金融、力学，甚至用于城镇规划和人口研究等领域。

[蒙特卡罗](https://blog.quantinsti.com/monte-carlo-simulation/)方法与确定性方法非常不同(麦克雷什，2004)。在确定性模型的情况下，在给定解释变量的情况下，因变量的值只能是由数学公式给出的唯一值。这种模型不包含随机成分(Rotelli，2015)。相比之下，蒙特卡罗并不求解显式方程，而是通过模拟单个粒子并记录其平均行为的某些方面(记录)来获得答案(Briesmeister，2000 年)。考虑到蒙特卡罗方法的广泛应用和涉及的问题，我们将这篇文章分成三个部分，以便有一个清晰的理解。

首先，我简要介绍了蒙特卡罗方法的历史，然后以物理学中的一个例子为例强调了它的一些用途，并展示了它在金融中的必要性，最后介绍了统计驱动的重要性抽样。

在以后的著作中，我们将更深入地研究技术方面的东西，给出重要概念的严格定义，然后继续讨论[马尔可夫链](https://blog.quantinsti.com/markov-model/)蒙特卡罗(MCMC ),因为它们在最近的蒙特卡罗计算中起着重要作用。在我的最后一篇文章中，我将结合所有这些方面，形成对称为蒙特卡罗方法的“黑箱”的坚实而全面的理解，重点关注 Metropolis-Hasting 算法，并探索乌兰和冯诺依曼创造的未来可能性。

## **蒙特卡洛的历史**

正如一个苹果落在牛顿的头上点燃了一股新的科学潮流，斯坦·乌兰不得不生病才能发现后来成为大量科学问题答案的东西。尽管乌兰和冯·诺依曼形式化并创造了术语蒙特卡罗，但近似方法的早期证据仍然存在。最引人注目的是布丰的针实验。这个实验如下:

一根长度为 L 的针以随机的方式被扔在一个光滑的桌子上，桌子上划有平行线，平行线之间的距离为 2L。观察者记录指针是否与一条直线相交。从实验中推导出，随着样本的增加，针头越线的概率趋于 1/pi。”(舒斯特，1974)。

1964 年，乌兰躺在病床上，不知道用 52 张牌拼成的坎菲尔德纸牌游戏能否被成功观察到。经过一些思考并使用纯数学方法，他玩了 100 次游戏，记录了所有成功的玩法，赢的比例反映了拿到一手好牌的几率。他获得了他的结果，很快他就提出了大多数数学物理和微分方程的问题，这些问题将从这种实用的计算方法中受益。那年晚些时候，他把这个想法传授给了约翰·冯·诺依曼(埃克哈特，1987)，他们开始研究更复杂的计算问题，后来又研究核武器。

蒙特卡洛这个名字的灵感也来自于摩纳哥的轮盘赌游戏，这是一种简单的产生随机数的游戏。另一个有点滑稽的动机是因为乌兰的叔叔喜欢去蒙特卡洛玩轮盘赌，因为这是以他的名义。

## **蒙特卡罗的应用**

如上所述，蒙特卡罗方法可以应用于许多研究领域。最早的应用是由发明人完成的，其中他们使用 MC 方法来解决使用电子数字积分器和计算器(ENIAC)的裂变装置中的中子扩散和倍增问题。这后来发展成为 MCNP。

![Image of the ENIAC](img/a9e6b66d71feac9341a69948d37e9f30.png)

## **在物理科学中的应用**

蒙特卡罗 N 粒子(MCNP)是一个通用的、连续能量的、广义几何的、依赖于时间的、耦合的中子/光子/电子蒙特卡罗输运程序。它可以用于几种传输模式:仅中子、仅光子、仅电子、中子/光子组合传输，其中光子由中子相互作用产生、中子/光子/电子、光子/电子或电子/光子。

虽然术语可能会令人困惑，但假设对蒙特卡罗方法知之甚少，也没有 MCNP 的经验，朱迪思·f·布里斯米斯特认为，当然，通过实践，即使是新手也可以掌握概念(布里斯米斯特，2000)。

## **在金融领域的应用**

MC 方法已被证明是现代金融中一种有价值且灵活的计算工具。重点关注资产定价:基本证券及其基础状态变量通常被建模为连续时间随机过程。蒙特卡洛方法被用于评估以预期表示的证券价格只是一个时间问题(Boyle，Broadie，& Glasserman，1997)。由于 MC 方法在处理日益复杂的金融工具方面的灵活性，我们可以清楚地看到 MC 方法在衍生产品和其他金融产品定价中的必要性。本文的第三部分提供了一个在金融中使用蒙特卡罗方法的详细例子。

## **重要性抽样**

重要抽样是选择一个好的分布来模拟随机变量(Anderson E. C .，1999)。从直觉上讲，我们必须从重要区域获取样本，以便获得准确的结果。这是通过对样品中的重要区域进行加权来实现的；因此得名重要性抽样。与其名称的重要性相反，抽样本身并不是抽样，而是一种近似方法。现在让我们以直观的方式探索重要性抽样:

假设我们希望对某一因素进行分析，但没有相关数据可供我们进行分析，或者我们现有的数据不能提供足够的结果。然后，我们生成一个符合以下特性的随机样本:

设 g(x)为原始样本分布(如果存在)，h(x)为建议样本分布。

*   h(x)应该接近与|g(x)| 成正比
*   从 h(x) 中模拟数值应该很容易
*   对于可能实现的任何值 x，计算密度 h(x)应该是容易的。

遵守这些要求可能很难需要足够的时间投入，但在处理上述两个问题时证明是有效的。我选择在这个阶段包括重要性抽样，因为它对以后的讨论更有启发性，尤其是关于蒙特卡罗改进技术。我们会发现重要抽样和马尔可夫链之间有着重要的关系。

我们已经将蒙特卡洛定义为一种广泛使用的近似技术，并了解了它有趣而又有些悸动的历史(悸动是因为这个名字的本质是与炸弹构造联系在一起的)。从冯·诺依曼使用 ENIAC 到现代计算机使用，MC 在数据/过程的模拟和操作中发挥了重要作用，这对我们的生活方式以及如何与世界互动产生了巨大影响。

在本文的下一部分，我们将更深入地探讨 MC 中固有的其他组件，并讨论 Metropolis-Hasting 算法作为蒙特卡罗马尔可夫链过程的一个特例。

## **马氏链、中心极限定理和 Metropolis-Hastings**

在文章的前一部分，我给出了蒙特卡罗的一般概述，并介绍了重要性抽样。现在，我们通过对一些被广泛使用但却被误解或由于其重要性而被普遍忽视的概念给出严格的定义来进行更深入的探讨。此后，我们探讨了 Metropolis-Hastings 算法，它构成了许多马尔可夫链蒙特卡罗方法的基础。

## **马尔可夫链蒙特卡罗**

在普通蒙特卡罗之后不久，洛斯·阿拉莫斯发明了马尔可夫链，他使用计算来获得这种模拟。这些链通常是从各种算法中获得的，其中 Metropolis 算法是最早期的，也是最重要的，因为它为 Metropolis-Hasting 算法等更复杂的算法铺平了道路。由于蒙特卡洛积分从要求的分布中抽取样本，并形成样本平均值以逼近期望值，因此马尔可夫链蒙特卡洛通过长时间运行巧妙构建的马尔可夫链来抽取这些样本(吉尔克斯、理查森、&【施皮格尔哈特】

让我们在此给出一些重要术语和概念的严格定义(一些定义摘自 Geyer C . J:Markov Chain Monte Carlo 简介):

### **定义**

**马尔可夫链:** 一个序列 *X <sub>1</sub>* ， *X <sub>2</sub>* ， *X <sub>3</sub>* ，…某集合的随机元素的条件分布若为*X<sub>n+1</sub>*给定 *X 从这个定义中，我们看到，为了计算下一个随机变量，我们只需要当前的信息，而不需要我们当前所处的位置，从而大大减少了花费在寻找和计算时间上的时间。*

**可逆性:** 一个转移概率分布相对于初始分布是可逆的，如果，马尔可夫链的 *X <sub>1</sub>* ， *X <sub>2</sub>* ， *X <sub>3</sub>* ，… 对的分布是可交换的。可逆性简化了中心极限定理(CLT)的应用，因为当这个性质成立时，CLT 的条件要简单得多。

**平稳性:** 一个随机过程(x *<sub>t</sub>* : t 在参数空间的一个元素中)是平稳的如果所有的 *X <sub>t</sub>* 具有相同的均值、方差和自相关

**中心极限定理:** 为平稳的、不可约的、可逆的马氏链和![udash](img/81619832df098f76a516212a72556fb2.png)  和 以及方差σ  与σ  有限则![nroot](img/78dc7b1462eac87266f79aba207b6e59.png)  其中![udash](img/81619832df098f76a516212a72556fb2.png)  为样本估计。我们可以进一步用一种通用的方式解释如下:对于任意随机变量序列 *X <sub> 1 </sub>* 、 *X <sub> 2 </sub>* 、 *X <sub> 3 </sub>* 、…  用 *X <sub> 1 </sub>* 、 *X <sub> 2 </sub>* 、 *X <sub> 3 值得注意的是，各种形式的 CLT 的存在都有其特定的要求</sub>*

## **蒙特卡罗估计和中心极限定理**

为了使用 CLT 来估计蒙特卡罗误差(这里没有讨论，但同样重要)，我们需要方差的一致估计，或者至少是渐近分布已知的方差估计(Geyer，1992)。已经提出了许多方差估计方法，大多数来自时间序列文献，并且适用于任意平稳随机过程，而不仅仅适用于马尔可夫链(Geyer，1992)。我们现在来看一个标准时间序列的方法。

## **非重叠批量是指**

在非重叠批次均值下(批次:为 n 项马尔可夫链保守迭代的子序列 *X <sub>1</sub>* ， *X <sub>2</sub>* ，…。 *X <sub>T</sub> 同样，中心极限定理将适用于每一批。*

批次平均值由给出

![formula](img/86f77423fc411a6c4e0ea09205cd9e7a.png)

这个方差将用于计算我们的中心极限定理。

## **Metropolis-Hasting 算法**

Metropolis-Hastings 算法由以下步骤给出 x<sup>【t】</sup>

1 生成![Yt](img/10be48de565db09fa872947fb6146c60.png)

2 乘![xtplus1](img/42127db36edfd12a3677b9c4b87a2e25.png)

我们称 p(x，y) 为接受概率。通过执行这个过程，我们得到所谓的大都市加速马尔可夫链 *X <sub>1</sub>* ， *X <sub>2</sub>* ，…。*X<sub>T</sub>*同 *X <sub>T</sub>* 大致按(x) 分布。(f(x) 是我们可能认为我们理想的样本分布)对于大 T 。(Kroese，Taimre，& Botev，2011 年)。

Metropolis-Hasting 背后的主要目的是模拟一个马尔可夫链，使得这个链的平稳分布与目标分布一致。

尽管 MC 方法通常比传统数值方法更有效，但其实施可能非常困难，且在时间和分析上计算昂贵。黑斯廷斯提出了一个源于 Metropolis 等人(1953)的广义方法。这种采样方法的主要特点是

*   计算依赖于 p(x) 仅通过 p(x’)/p(x)形式的比值，其中 x’和 x 是样本点，不需要因式分解 p(x) 也不需要确定归一化常数

关于 Metropolis-Hastings 有更多的文献，但我们强调的在这一点上已经足够了。理想情况下，我们试图用 Metropolis 这样的算法做的事情是拿出一个尽可能接近现实的样本，从而确保在尽可能现实的设置下测试任何提议的模型。

到目前为止，我们已经收集了足够的理论知识来构建一个可用于投资的策略。在文章的最后一部分，我们将利用 uptil 现在开发的所有概念来评估它们的重要性。

## **金融应用**

在蒙特卡洛领域，存在大量的应用。在这最后一部分，我把所有以前的工作结合在一起，并把我们到目前为止收集的理论付诸实践。

## **应用 Metropolis-Hastings 算法**

从上一节中，我们推出了一种方法，通过这种方法，我们可以使用任意因子生成一个样本，这些因子组合起来可以相当准确地反映现实

为了绝对简单起见，我们将只考虑我们希望建模的一个变量，但该流程适用于资产组合或这些资产的衍生品，只需进行最小的调整。在这里，我们利用动态资产定价来估计均衡，并利用均值回归理论作为我们策略的基础来开发套利机会。我将忽略实际的计算，以便直观地理解这里开发的理论的用法:

*   假设资产 A 具有相当大的波动性，我们希望利用这一观察结果。我们拥有的算法使我们能够模拟我们自己的股票运动，并将其与 A 的运动相匹配。
*   假设布朗运动为我们的 q(x) (建议分布)我们应用 Metropolis-Hastings 算法记录所有观察值。

在这一点上，我们有两种可供选择的方法用于比较:

备选方案 1:由于我们有一个明确的流程，我们可以根据观察到的趋势直接绘制出这个伪趋势，然后根据价格差异做出交易决策。然后，我们构建一个程序，根据两者之间的关系做出买卖决定。

*   当生成的过程高于资产价格时，这将反映买入，因为我们假设价格将缩回到我们的模型中(记住，我们的模型给出了一个平稳分布，这意味着随着时间的推移，价格将收敛到这个稳定状态(Johannes & Polson，2002))
*   对于低于资产价格的生成流程，将执行卖出触发器。

备选方案 2:为了进一步加强我们的决策，我们可以使用基于生成的样本路径的回归模型。通过这样做，我们甚至能够假设资产 A 运动的未来趋势，同时了解和控制当前的价格波动。同样，在第一模型中应用的交易决策也可以使用回归模型作为基准来应用。

这是一个过于简化的模型，只给出了一种可能的用途。布朗运动的使用作为我们的 q 被包括在内，这是基于它的特性来模拟金融运动，并在其计算中包括噪声(Morters & Peres，2008)。此外，虽然从理论上讲，我们没有对 q 进行限制，但重要的是要注意，建议密度的选择通常会影响算法的性能。(约翰内斯&波尔森，2002 年，第 26 页)

## **障碍选项和重要性抽样**

在描述和使用选项时，我们几乎总是考虑普通选项，并假设这同样适用于外来类型。我会走一条稍微不同的路，考虑一个奇特的选择；准确地说是障碍选项。下面的例子是从 Kroese D，P Taime T 和 Botev Z，I 的《蒙特卡洛方法手册》中摘录的:

考虑一个下跌买入期权，有一个受监控的障碍，到期时的收益由给出

![eq1](img/b403d3382f1bae0a9c8fe8612d6fd4bc.png)

其中![eq2](img/0bc6604c2df15363bb0156a7498cce92.png)

用![zeq](img/0c18d31f293b483d53deb6a70cd4785b.png)和![tk](img/cdb87129ba45af311287143602c9bcef.png)来表示 *k* = 1，2，3，…。期权中出现正收益的情况很少，因此期权价格的计算很大程度上取决于这种情况的出现。因此，估计稳健概率是必要的，重要抽样可能会发挥巨大作用。

此外:为了获得一个好的阳萎抽样密度，我们使用了所谓的交叉熵方法。这其中包括获取一个格式的 pdf

![fz](img/b184d35f7969dba40bcdbe9e5aa5e09d.png)

其中![ez](img/fdc703c4f4a1c477cd441185e415d528.png) 标准正态随机向量ζ的 pdf。可以通过使用被称为“打了就跑”算法的 Metropolis-Hasting 算法的变体来获得所提出的 pdf 的进一步增强。

## **结论说明和总结**

Metropolis-Hastings 方法有一个巨大的应用，我们可能不会在单个博客系列中讨论它，尽管它只是在 20 世纪 90 年代才被普遍接受(Hitchocock，2012)。Metropolis-Hastings 算法的各种修改，包括独立采样器和随机漫步采样器，进一步提供更相关的预测。黑斯廷斯看到了位于大都市中心的马尔可夫链的转移矩阵，将他的目标分布呈现为马尔可夫链的π(x)的不变分布(Hitchocock，2012，第 155 页)，如前所述，这一特征重塑了许多学科。

在一天结束时，所有这些练习的全部目的是想出一个接近真实但在我们控制范围内的样本。考虑到这一点，存在许多旨在利用关于模型的已知信息来获得更准确估计值的方差缩减技术(Kroese & Rubinstein，2008)。我们在第二部分中简要地提到了一种这样的技术，即非重叠批处理方法。其他众所周知的可能提供适度方差减少的技术包括使用控制和/或算术随机变量、分层抽样(Kroese & Rubinstein，2008 年)和最受欢迎的重要性抽样。(克罗泽，塔米姆雷，&博特夫，2011 年)

Kroese 等人认为重要抽样是最重要的方差缩减技术之一(2011 年，第 362 页),更重要的是它能够找到罕见事件概率的估计值。与本系列中讨论的大多数主题一样，这里只给出了介绍性材料，在学术文献中可以找到大量采样方法的推导。

对于稳健的结果，包含交叉熵是有益的。交叉熵方法的目的是获得密度，使得该密度和最佳密度(实际)之间的距离尽可能小。加权重要性抽样是与金融市场最相关的一种变化，因为它将更多的权重分配给对过程有重要输入的因素。

综合运用所有这些方法将会大大提高回报，大幅降低风险，并有助于形成稳健的投资策略。

## **参考书目**

*   安德森(1999)。 *蒙特卡罗方法和重要性抽样。*
*   博伊尔，p .，布罗迪，m .，&格拉斯曼，P. (1997)。证券定价的蒙特卡罗方法。经济与控制学报，1267-1321。
*   Briesmeister，J. F. (2000 年)。*【MCNP 】-一个通用的蒙特卡罗 N 粒子输运代码。*
*   埃克哈特(1987 年)。 *斯坦乌兰、约翰·冯·诺依曼和蒙特卡洛法。* 从 ScienceMadness.org 获得的。
*   盖耶，C. J. (1992)。实用马尔可夫链蒙特卡罗。统计科学第 7 卷第 4 期，473-483 页。
*   吉尔克斯，W. R .，理查森，s .，&施皮格尔哈特，D. J .(未注明)。介绍马尔可夫链蒙特卡罗。
*   希区柯克博士(2012 年)。大都市加速算法的历史。，254-257 页。
*   约翰尼斯，m .，&波尔森，N. (2002)。 *MCMC 金融 e .T5】*
*   Kroese，D. P .，Tamimre，t .，& Botev，Z. I. (2011 年)。 *蒙特卡洛方法手册。* 新泽西霍博肯:约翰·威利&父子公司
*   Kroese，D. P .，& Rubinstein，R. Y. (2008 年)。 *模拟和蒙特卡洛法。* 新泽西:约翰·威利&父子公司
*   d . kro ese，t . taim re，& Botev，Z. I. (2011 年)。蒙特卡罗方法手册。新泽西:约翰·威利&的儿子们。
*   莫特斯，p .，&佩雷斯，Y. (2008 年)。 *布朗运动。*
*   麦克雷什博士(2004 年)。 *蒙特卡洛模拟和金融。*
*   罗泰利，F. (2015 年)。 *随机过程。* 比勒陀利亚。
*   舒斯特，E. F. (1974)。 *布冯的针实验。* 美国数学协会。
*   许，，张，张，(2010)。均值风险优化和投资组合选择的蒙特卡罗方法。南汉普顿大学。

*免责声明:这篇客座博文中提供的观点、意见和信息仅属于作者个人，并不代表 QuantInsti 的观点、意见和信息。本文中所做的任何陈述或共享的链接的准确性、完整性和有效性都不能得到保证。我们对任何错误、遗漏或陈述不承担任何责任。与侵犯知识产权相关的任何责任由他们承担。*