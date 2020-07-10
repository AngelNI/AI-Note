# Evaluate

<img src="https://s2.ax1x.com/2019/08/16/mZiNo8.png" alt="" border="0" />

**在介绍指标前必须先了解“混淆矩阵”：**

**混淆矩阵**

True Positive(真正，TP)：将正类预测为正类数

True Negative(真负，TN)：将负类预测为负类数

False Positive(假正，FP)：将负类预测为正类数误报 (Type I error)

False Negative(假负，FN)：将正类预测为负类数→漏报 (Type II error)

<img src="https://s2.ax1x.com/2019/08/16/mZiWYF.png" alt="" border="0" />

## **1、准确率（Accuracy）**

准确率(accuracy)计算公式为：

<img src="https://s2.ax1x.com/2019/08/16/mZi4SJ.png" alt="" border="0" />

注：准确率是我们最常见的评价指标，而且很容易理解，就是被分对的样本数除以所有的样本数，通常来说，正确率越高，分类器越好。准确率确实是一个很好很直观的评价指标，但是有时候准确率高并不能代表一个算法就好。比如某个地区某天地震的预测，假设我们有一堆的特征作为地震分类的属性，类别只有两个：0：不发生地震、1：发生地震。一个不加思考的分类器，对每一个测试用例都将类别划分为0，那那么它就可能达到99%的准确率，但真的地震来临时，这个分类器毫无察觉，这个分类带来的损失是巨大的。为什么99%的准确率的分类器却不是我们想要的，因为这里数据分布不均衡，类别1的数据太少，完全错分类别1依然可以达到很高的准确率却忽视了我们关注的东西。再举个例子说明下。在正负样本不平衡的情况下，准确率这个评价指标有很大的缺陷。比如在互联网广告里面，点击的数量是很少的，一般只有千分之几，如果用acc，即使全部预测成负类（不点击）acc也有 99% 以上，没有意义。因此，单纯靠准确率来评价一个算法模型是远远不够科学全面的。

## **2、精确率、精度（Precision）**

精确率(precision)定义为：

<img src="https://s2.ax1x.com/2019/08/16/mZiXfe.png" alt="" border="0" />

表示被分为正例的示例中实际为正例的比例.

## **3、召回率（Recall）**

召回率是覆盖面的度量，度量有多个正例被分为正例，recall=TP/(TP+FN)=TP/P=sensitive，可以看到召回率与灵敏度是一样的。

**灵敏度（sensitive）**

sensitive = TP/P，表示的是所有正例中被分对的比例，衡量了分类器对正例的识别能力。

## **4、综合评价指标（F-Measure）**

P和R指标有时候会出现的矛盾的情况，这样就需要综合考虑他们，最常见的方法就是F-Measure（又称为F-Score）。
F-Measure是Precision和Recall加权调和平均：

<img src="https://s2.ax1x.com/2019/08/16/mZFcjA.png" alt="" border="0" />



当参数α=1时，就是最常见的F1，也即

<img src="https://s2.ax1x.com/2019/08/16/mZF4N8.png" alt="mZF4N8.png" border="0" height = 100/>

可知F1综合了P和R的结果，当F1较高时则能说明试验方法比较有效。

## **5、ROC曲线：**

ROC（Receiver Operating Characteristic）曲线是以假正率（FP_rate）和真正率（TP_rate）为轴的曲线，ROC曲线下面的面积我们叫做AUC，如下图所示：

<img src="https://s2.ax1x.com/2019/08/16/mZFLBq.png" alt="" border="0" />

<img src="https://s2.ax1x.com/2019/08/16/mZkKvd.png" alt="" border="0" />

（1）曲线与FP_rate轴围成的面积（记作AUC）越大，说明性能越好，即图上L2曲线对应的性能优于曲线L1对应的性能。即：曲线越靠近A点（左上方）性能越好，曲线越靠近B点（右下方）曲线性能越差。

（2）A点是最完美的performance点，B处是性能最差点。

（3）位于C-D线上的点说明算法性能和random猜测是一样的–如C、D、E点。位于C-D之上（即曲线位于白色的三角形内）说明算法性能优于随机猜测–如G点，位于C-D之下（即曲线位于灰色的三角形内）说明算法性能差于随机猜测–如F点。

（4）虽然ROC曲线相比较于Precision和Recall等衡量指标更加合理，但是其在高不平衡数据条件下的的表现仍然过于理想，不能够很好的展示实际情况。

## **6、PR曲线：**

即，PR（Precision-Recall）曲线。

举个例子（例子来自Paper：Learning from eImbalanced Data）：
假设N_c>>P_c（即Negative的数量远远大于Positive的数量），若FP很大，即有很多N的sample被预测为P，因为FP_rate = FP/N_c，因此FP_rate的值仍然很小（如果利用ROC曲线则会判断其性能很好，但是实际上其性能并不好），但是如果利用PR，因为Precision综合考虑了TP和FP的值，因此在极度不平衡的数据下（Positive的样本较少），PR曲线可能比ROC曲线更实用。

## **补充**

### **1.MAP**

在了解MAP(Mean Average Precision)之前，先来看一下AP(Average Precision), 即为平均准确率。

对于AP可以用这种方式理解: 假使当我们使用google搜索某个关键词，返回了10个结果。当然最好的情况是这10个结果都是我们想要的相关信息。但是假如只有部分是相关的，比如5个，那么这5个结果如果被显示的比较靠前也是一个相对不错的结果。但是如果这个5个相关信息从第6个返回结果才开始出现，那么这种情况便是比较差的。这便是AP所反映的指标，与recall的概念有些类似，不过是“顺序敏感的recall”。

比如对于用户 uu, 我们给他推荐一些物品，那么 uu 的平均准确率定义为：

<img src="https://s2.ax1x.com/2019/08/16/mZAlz4.png" alt="" border="0" />

那么对于MAP(Mean Average Precision)，就很容易知道即为所有用户 u 的AP再取均值(mean)而已。那么则有:

<img src="https://s2.ax1x.com/2019/08/16/mZAwWD.png" alt="" border="0" height=80/>

### **2.NDCG**

#### **1.CG**

先从后两个字母CG(Cummulative Gain)说起, 直接翻译的话叫做“累计增益”。 在推荐系统中，CG即将每个推荐结果相关性(relevance)的分值累加后作为整个推荐列表(list)的得分。

<img src="https://s2.ax1x.com/2019/08/16/mZEFk6.png" alt="mZEFk6.png" border="0" height=100/>

#### 2.DCG

CG的一个缺点是没有考虑每个推荐结果处于不同位置对整个推荐效果的影响，例如我们总是希望相关性高的结果应排在前面。显然，如果相关性低的结果排在靠前的位置会严重影响用户体验， 所以在CG的基础上引入位置影响因素，即DCG(Discounted Cummulative Gain), “Discounted”有打折，折扣的意思，这里指的是对于排名靠后推荐结果的推荐效果进行“打折处理”:

<img src="https://s2.ax1x.com/2019/08/16/mZE0A0.png" alt="" border="0" />

#### 3.NDCG

DCG仍然有其局限之处，即不同的推荐列表之间，很难进行横向的评估。而我们评估一个推荐系统，不可能仅使用一个用户的推荐列表及相应结果进行评估， 而是对整个测试集中的用户及其推荐列表结果进行评估。 那么不同用户的推荐列表的评估分数就需要进行归一化，也即NDCG(Normalized Discounted Cummulative Gain)。

在介绍NDCG之前，还需要了解一个概念：IDCG. IDCG, 即Ideal DCG， 指推荐系统为某一用户返回的最好推荐结果列表， 即假设返回结果按照相关性排序， 最相关的结果放在最前面， 此序列的DCG为IDCG。因此DCG的值介于 (0,IDCG](0,IDCG] ，故NDCG的值介于(0,1].

对于用户 uu 的NDCG@k定义为： 

<img src="https://s2.ax1x.com/2019/08/16/mZE6c4.png" alt="" border="0" />

这里的 k表示推荐列表的大小。

那么，则有： 

<img src="https://s2.ax1x.com/2019/08/16/mZEWH1.png" alt="" border="0" />

<img src="https://s2.ax1x.com/2019/08/16/mZE4N6.png" alt="" border="0" />