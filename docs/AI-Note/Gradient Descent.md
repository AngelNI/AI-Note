# Gradient Descent

## 1.场景导入

梯度下降法的基本思想可以类比为一个下山的过程。假设这样一个场景：一个人被困在山上，需要从山上下来(i.e. 找到山的最低点，也就是山谷)。但此时山上的浓雾很大，导致可视度很低。因此，下山的路径就无法确定，他必须利用自己周围的信息去找到下山的路径。这个时候，他就可以利用梯度下降算法来帮助自己下山。具体来说就是，以他当前的所处的位置为基准，寻找这个位置最陡峭的地方，然后朝着山的高度下降的地方走，同理，如果我们的目标是上山，也就是爬到山顶，那么此时应该是朝着最陡峭的方向往上走。然后每走一段距离，都反复采用同一个方法，最后就能成功的抵达山谷。

<img src="https://s2.ax1x.com/2019/08/14/mk4Ilq.png" alt="mk4Ilq.png" border="0" />

## 2.基本概念

梯度下降法（gradient descent），又名最速下降法（steepest descent）是求解无约束最优化问题最常用的方法，它是一种迭代方法，每一步主要的操作是求解目标函数的梯度向量，将当前位置的负梯度方向作为搜索方向（因为在该方向上目标函数下降最快，这也是最速下降法名称的由来）。

梯度下降法特点：越接近目标值，步长越小，下降速度越慢

梯度下降可以用来解决机器学习算法的优化问题。

梯度下降不一定能够找到全局最优解，但有可能是一个局部最优解。如果损失函数是凸函数，梯度下降法得到的一定是全局最优解

##  3.梯度下降的相关概念

1.步长或学习效率(learning rare)：步长决定在梯度下降过程中，每一步沿梯度负方向前进的距离。

2.假设函数(hppothesis function)：也就是我们的模型学习到的函数 

3.损失函数(loss function): 损失函数是用来评估模型的好坏，通常用损失函数来度量拟合的程度，线性回归中损失函数通常为label和假设函数输出的差的平方。自己理解为（实际值-真实值）的平方。

## 1.4  梯度下降法

**Cost Function & Gradients**

计算代价函数和梯度的公式如下所示。

**注意**：代价函数用于线性回归，对于其他算法，代价函数是不同的，梯度必须从代价函数中推导出来。

**Cost**
$$

\begin{equation}
J(\theta) = 1/2m \sum_{i=1}^{m} (h(\theta)^{(i)} - y^{(i)})^2
\end{equation}

$$

**Gradient**

$$
\begin{equation}
\frac{\partial J(\theta)}{\partial \theta_j} = 1/m\sum_{i=1}^{m}(h(\theta^{(i)} - y^{(i)}).X_j^{(i)}
\end{equation}
$$


**Gradients**


$$
\begin{equation} \theta_0: = \theta_0 -\alpha . (1/m .\sum_{i=1}^{m}(h(\theta^{(i)} - y^{(i)}).X_0^{(i)}) \end{equation}
$$

$$
\begin{equation} \theta_1: = \theta_1 -\alpha . (1/m .\sum_{i=1}^{m}(h(\theta^{(i)} - y^{(i)}).X_1^{(i)}) \end{equation}
$$

$$
\begin{equation} \theta_2: = \theta_2 -\alpha . (1/m .\sum_{i=1}^{m}(h(\theta^{(i)} - y^{(i)}).X_2^{(i)}) \end{equation}
$$

$$
\begin{equation} \theta_j: = \theta_j -\alpha . (1/m .\sum_{i=1}^{m}(h(\theta^{(i)} - y^{(i)}).X_0^{(i)}) \end{equation}
$$

值得注意的是，最初成本下降得更快，然后成本降低的收益就不那么多了。 我们可以尝试使用不同的学习速率和迭代组合，并得到不同学习率和迭代的效果会如何

1.先决条件：确认优化模型的损失函数

2.参数的初始化: 初始化假设函数的参数θ(注：θ是一个向量），算法中止距离ϵ以及步长α

3.算法过程：

（1） 初始化参数

（2）确定当前位置的损失函数的梯度

（3）确定是否所有梯度下降的距离都小于ϵ，如果小于则算法中止，当前为最后结果，否则，则重复步骤（4）

（4）更新所有的θ

## 1.5  梯度下降算法的更新方式

### 1.5.1.批量梯度下降法BGD

全量梯度下降法每次学习都使用整个训练集，因此每次更新都会朝着正确的方向进行，最后能够保证收敛于极值点，凸函数收敛于全局极值点，非凸函数可能会收敛于局部极值点，缺陷就是学习时间太长，消耗大量内存。

### 1.5.2随机梯度下降法（Stochastic Gradient Descent）

随机梯度下降法，其实和批量梯度下降法原理类似，区别在与求梯度时没有用所有的 mm 个样本的数据，而是仅仅选取一个样本 jj 来求梯度。对应的更新公式是：


$$
\theta_i = \theta_i - \alpha (h_\theta(x_0^{(j)}, x_1^{(j)}, ...x_n^{(j)}) - y_j)x_i^{(j)}
$$


优点：训练速度快

缺点：准确度下降，并不是全局最优，不易于并行实现。并且SGD伴随之一个问题是噪音较多，使SGD并不是每次 都向着整体最优的方向前进。



SGD方法的一个缺点是，其更新方向完全依赖当前的batch，因而其更新十分不稳定。 解决方法简单做法引入momentum（？？）

### 1.5.3小批量梯度下降法（Mini-batch Gradient Descent）

小批量梯度下降法是在上述的两种方法的性能之间取得一个折中，即训练比较快，而且也保证最终的参数准确率。

小批量梯度下降法是批量梯度下降法和随机梯度下降法的折衷，也就是对于 mm 个样本，我们采用 xx 个样子来迭代，1<x<m。一般可以取 x=10，当然根据样本的数据，可以调整这个 x 的值。对应的更新公式是：


$$
\theta_i = \theta_i - \alpha \sum\limits_{j=t}^{t+x-1},(h_\theta(x_0^{(j)},x_1^{(j)}, ...x_n^{(j)}) - y_j)x_i^{(j)}
$$

**三种梯度下降方式损失函数对比**

批量梯度下降

<img src="https://s2.ax1x.com/2019/08/15/mAuS2D.png" alt="" border="0" />

随机梯度下降

<img src="https://s2.ax1x.com/2019/08/15/mAnz8O.png" alt="" border="0" />

小批量梯度下降

<img src="https://s2.ax1x.com/2019/08/15/mAnxPK.png" alt="" border="0" />

## 1.6  补充——梯度下降优化

### 1.6.1  梯度下降调参必要性

1. 选择一个合适的学习速率是非常难的。学习速率太小会导致收敛慢，太大会阻碍收敛并导致损失函数在极小值周围波动甚至背离。

2. 尝试通过设置调度在训练时候调整训练速率，比方，模拟退火依照预先定义好的调度算法或者当相邻的迭代中目标变化小于一个阈值时候减小学习速率。可是这些调度和阈值须要预先设置，无法对数据集特征进行自适应。

3. 除此之外。对全部的參数更新都依照同一个学习速率也是一个问题。假设我们的数据非常稀疏而且我们的特征出现的次数不同。我们可能不会希望全部的參数以某种同样的幅度进行更新。而是针对非常少出现的特征进行一次大幅度更新。

4. 在神经网络中常见的极小化highly non-convex error functions的一个关键挑战是避免步入大量的suboptimal local minima。 

5. Dauphin等人觉得实践中的困难来自saddle points而非local minima。

   所谓saddle points是指那些维度梯度不一致的点。

   这些saddle points常常被一个相等误差的平原包围。导致SGD非常难摆脱，由于梯度在全部方向都近似于0。

   

   调参方法

   1.在数尺上进行超参数搜索

   2.选择合适的训练次数

   3.选择合适的梯度下降方法

   从粗到细分段调参

   一般先进行初步范围搜索，然后根据好结果出现的地方，再缩小范围进行更精细的搜索。

### 1.6.2  冲量梯度下降 Momentum

#### 1.6.2.1  导入

我们向山下丢一个小球就会涉及使用到momentum。小球在向山下滚动时候会积累动量滚动地越来越快（假设存在空气阻力，会一直加速到终端速度terminal velocity）。同样的事情会发生在參数更新上：momentum term会在更新方向同样的维度加速。会在更新方向不同的维度上减速。终于。我们更快地收敛并降低振荡。

<img src="https://s2.ax1x.com/2019/08/15/mAuNzF.png" alt="" border="0" />

<img src="https://s2.ax1x.com/2019/08/15/mAuaM4.png" alt="" border="0" />

Momentum是一种帮助SGD在相关方向进行加速并抑制振荡的方法

<a href="https://imgchr.com/i/mAutRU"><img src="https://s2.ax1x.com/2019/08/15/mAutRU.png" alt="" border="0" /></a>

学习效率对搜索大小影响

学习率较小时，收敛到极值的速度较慢。

学习率较大时，容易在搜索过程中发生震荡。

**冲量梯度下降图像**

<img src="https://s2.ax1x.com/2019/08/15/mAurIx.png" alt="mAurIx.png" border="0" />