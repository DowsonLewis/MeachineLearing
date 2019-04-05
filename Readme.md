
#                                       *Machine Learning Engineer*

##      机器学习工程师  笔记

- **Date@2018年7月--2018年12月**
- **Author@Dowson·Lewis**
- **Mail@lds12150019@163.com**

------

## 1.机器学习概述

机器学习是什么->>人工智能的一个重要学科分支多领域交叉学科->>数据驱动![4](C:\Users\Administrator\Pictures\Saved Pictures\4.jpg)

### 1.1认识机器学习

研究的是计算机怎样**模拟人类**的学习行为，以获取新的知识并重新组织已有的知识结构使之不断的完善自身

> 本质就是计算机从**数据**中**学习**出**规律和模式，**以应用在数据上做**预测**的任务。
>
> 作为一套数据驱动的方法，在**互联网、生物信息学、无人驾驶汽车、金融、交通**等领域有广泛的应用

### 1.2机器学习分类

![5](C:\Users\Administrator\Pictures\Saved Pictures\5.jpg)

分类问题（监督学习）--根据数据样本抽取出的特征，判定其属于**有限个类别中**的哪一个

回归问题（监督学习）--根据数据样本上抽取出的特征，预测**连续值**结果

聚类问题（无监督学习） --根据数据样本上抽取出的特征，挖掘数据的**关联**模式

强化学习 --研究如何基于环境而行动，以取得**最大化**的预期利益

> 机器学习专业术
>
> 监督学习（supervised learning)、无监督学习（unsupervised learning）、未见样本（unseen instance）、泛化（generalization)
>
> 训练集>>模型>>验证集
>
> 属性（attribute）、特征（feature）；特征向量（feature vector）、示例（instance）、样例（example）、标记空间、输出空间

### 1.3机器学习基本流程与工作环节

机器学习训练出的预测模型一定是围绕**算法**和**数据**展开的。模型的好坏取决于数据的质量

数据决定了模型效果的**上限**，而算法只是**逼近**这个极限![6](C:\Users\Administrator\Pictures\Saved Pictures\6.jpg)

> 数据预处理（占据**60-70%**时间）>>模型学习（占据20-30%时间）>>模型评估>>新样本预测

### 1.4机器学习中的评估指标

什么模型好？**泛化**能力强！换言之，**错误率低，精度高**。然而，我们手上没有未知的样本，如何可靠地进行评估？关键：获得可靠的“测试集数据"（test set）

测试集（用于评估）应该与训练集（用于模型学习）“**互斥**”

常见方法

留出法（hold-out） --全量数据集分为训练集和测试集

> 注 --保持数据分布**一致性**；多次**重复划分**；测试集不能太大，不能太小

k折交叉验证法（k-cross validation） --数据集分为若干等份，每次只拿一份充当测试集，剩下的训练模型，然后重新选择测试集，最后对若干个结果取均值

> 注 --对测试结果最好进行加权平均，具体权重要对数据进行分析，**样本赋权，权重取值**

自助法（boostrap）--有放回采样，每一次采取数据后再放回去。每个数据约有**36.8%的概率**不出现，或者约有**36.8%**的样本不会出现

性能度量（performance）--是衡量模型泛化能力的数值评价标准，反映了当前问题（任务需求）

>  注 --使用不同的性能度量可能会导致不同的评判结果。关于模型的好坏判断，不仅取决于**算法**和**数据**，还取决于当前**任务需求**。

查准率 vs.查全率  混淆矩阵  AUC（一条曲线下方的面积）

回归问题的常用性能度量 -- 平均绝对误差MAE、均方误差MSE、方根误差RMSE、R平方

### 1.5机器学习算法一览

根据是否有标签和分类回归的算法一览。

![7](C:\Users\Administrator\Pictures\Saved Pictures\7.jpg)

> 不同算法在尝试生成不同的**决策边界**，从而完成分类
>
> 回归类问题有不同拟合方式

### 如何学习机器学习工程师？

> **数学基础、算法理解、编程基础 >> 动手实践 >> 积累项目经验                                                                                                         

------

## 2.线性回归与逻辑回归

认识并理解两种模型>>连续值输出的线性模型与逻辑判断的逻辑回归模型

### 2.1线性回归

线性模型（linear model）试图学得一个通过属性的线性组合来进行**连续值**预测的函数![8](C:\Users\Administrator\Pictures\Saved Pictures\8.jpg)

应用模型 --放假预测例子（一元到多元的研究）![10](C:\Users\Administrator\Pictures\Saved Pictures\10.jpg)

![11](C:\Users\Administrator\Pictures\Saved Pictures\11.jpg)

损失函数（loss function）

我们把x到y的映射函数f记作θ的函数，**损失函数**定义为--
$$
J(\theta_0,\theta_1,\dots,\theta_n)=\frac{1}{2m}\sum_{i=1}^{m}(h_\theta(x^{(i)})-y^{i})^2
$$
转换成一个数学问题>>最小化损失函数>>均方差损失是一个凸函数

梯度下降 --逐步**迭代**减小损失函数（凸函数），如同下山，找准方向（斜率），每次迈进一小步，直至山底

一元的损失函数的梯度下降
$$
\theta_1:=\theta_1-\alpha\frac{d}{d\theta}J(\theta_1)
$$

> α是**超参数**，也被称为学习率或者步长，这个值对于梯度下降影响很大，值不能太大也不能太小

![12](C:\Users\Administrator\Pictures\Saved Pictures\12.jpg)

两个参数的情形  repeat until convergence{
$$
\theta_0:=\theta_0-\alpha_\frac{1}{m}\sum_{i=1}^{m}(h_\theta(x^{(i)})-y^{(i)})
$$

$$
\theta_1:=\theta_1-\alpha_\frac{1}{m}\sum_{i=1}^{m}(h_\theta(x^{(i)})-y^{(i)})*x^{(i)}
$$

​			}

​       分别对θ_0、θ_1求偏导，找到负梯度值最大点，根据学习率进行迭代

**欠拟合**与**过拟合**

欠拟合 >> 模型没有很好地捕捉到数据特征，不能够很好地拟合数据

过拟合 >> 把样本中的一些噪声特性也学习下来了，泛化能力差

> 实际工业界使用的各种模型都存在过拟合的风险>>
>
> - 更多的参数/特征，更复杂的模型，通常有更强的学习能力，但是更容易“失去控制”
> - 训练集中有一些噪声，不能够不代表全量真实数据的分布，死记硬背会丧失泛化能力

过拟合与**正则化**>>通知正则化添加参数“惩罚”，控制参数幅度限制参数搜索空间，减少过拟合风险。
$$
\lambda\sum_{j=1}^{n}\theta_j^2
$$
广义线性模型

> 有时候关系不一定是线性的，如何逼近y的衍生物？>>指数（exp）或者对数（log）变换处理

### 2.2逻辑回归

在逻辑回归（Logistic Regression）里，通常我们并不拟合样本分布，而是**确定决策边界**

sigmoid函数g(x)
$$
y=\frac{1}{1+e^{-z}}
$$
![13](C:\Users\Administrator\Pictures\Saved Pictures\13.jpg)

线性决策边界 
$$
h_\theta(x)=g(\theta_0+\theta_1x_1+\theta_2x_2)
$$
非线性决策边界
$$
h_\theta(x)=g(\theta_0+\theta_1x_1+\theta_2x_2+\theta_3x_1^2+\theta_4x_2^2+\cdots)
$$
损失函数 >>**~~均方差损失~~**（MSE）

逻辑回归的损失函数的输入若是概率，按照线性回归的思路进行的化将会是一个非凸函数，不能找到全局最小值，这不利于损失函数分析

对数损失/**二元交叉熵**损失与正则化
$$
J（\theta）=\frac{1}{m}\sum_{i=1}^{m}Cost(h_\theta(x^{(i)}),y^{(i)})
$$

$$
=-\frac{1}{m}[\sum_{i=1}^{m}logh_\theta(x^{(i)})+(1-y^{(i)}log(1-h_\theta(x^{(i)})]
$$

添加**L2**型正则化项
$$
J(\theta)=[-\frac{1}{m}\sum_{i=1}^{m}logh_\theta(x^{(i)})+(1-y^{(i)}log(1-h_\theta(x^{(i)})]+\frac{\lambda}{2m}\sum_{j=1}^{n}\theta_j^2
$$
这个损失函数就是一个**凸函数**，依旧可以用**梯度下降**
$$
\theta_j:=\theta_j-\alpha\frac{\partial}{\partial\theta_j}J(\theta)
$$

> 多分类 -->one vs. one       one vs. rest

### 2.3工程应用经验

LR弱于SVM/GBDT/RandomForest...?

模型本身并**没有**好坏之分

1. LR能以概率的形式输出结果，而非只是0，1判定
2. LR的**可解释性强，可控度**高
3. 训练快，特征工程（feature engineering）之后**效果赞**
4. 因为结果是概率，可以做**排序**模型
5. 添加特征非常**简单**

应用

> CTR预估/推荐系统的learning to rank/搜索引擎的广告/电商搜索排序/新闻app的推荐和排序

样本处理

- 样本特征处理>>离散化后用独热向量编码处理成0，1值/幅度缩放
- 处理大样本量>>试试spark MLlib/试试采样
- 注意样本的平衡>>对样本分布敏感/欠采样，过采样/修改损失函数，给不同权重

> 工具包与库
>
> Liblinear >> https://www.csie.ntu.edu.tw/~cjlin/liblinear/
>
> Spark MLlib >>http://spark.apache.org/docs/latest/mllib-linear-methods.html#logistic-regression
>
> **Scikit-learn**>> **http://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LogisticRegression.html**

### 2.4线性回归示例

```python
线性回归示例
# %load ../../standard_import.txt
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

from sklearn.linear_model import LinearRegression
from mpl_toolkits.mplot3d import axes3d

pd.set_option('display.notebook_repr_html', False)
pd.set_option('display.max_columns', None)
pd.set_option('display.max_rows', 150)
pd.set_option('display.max_seq_items', None)
 
#%config InlineBackend.figure_formats = {'pdf',}
%matplotlib inline  

import seaborn as sns
sns.set_context('notebook')
sns.set_style('white')
```

```python
data = np.loadtxt('linear_regression_data1.txt', delimiter=',')   

X = np.c_[np.ones(data.shape[0]),data[:,0]]
y = np.c_[data[:,1]]

plt.scatter(X[:,1], y, s=30, c='r', marker='x', linewidths=1)
plt.xlim(4,24)
plt.xlabel('Population of City in 10,000s')
```

![2](C:\Users\Administrator\Pictures\Saved Pictures\2.png)

```python
# 计算损失函数
def computeCost(X, y, theta=[[0],[0]]):
    m = y.size
    J = 0
    h = X.dot(theta)
    J = 1.0/(2*m)*(np.sum(np.square(h-y)))
    return J
 computeCost(X,y)
```

32.072733877455676

```python
# 画出每一次迭代和损失函数变化
theta , Cost_J = gradientDescent(X, y)
print('theta: ',theta.ravel())

plt.plot(Cost_J)
plt.ylabel('Cost J')
plt.xlabel('Iterations');
```

('theta: ', array([-3.63029144,  1.16636235]))

![3](C:\Users\Administrator\Pictures\Saved Pictures\3.png)

```python
xx = np.arange(5,23)
yy = theta[0]+theta[1]*xx

# 画出我们自己写的线性回归梯度下降收敛的情况
plt.scatter(X[:,1], y, s=30, c='r', marker='x', linewidths=1)
plt.plot(xx,yy, label='Linear regression (Gradient descent)')

# 和Scikit-learn中的线性回归对比一下 
regr = LinearRegression()
regr.fit(X[:,1].reshape(-1,1), y.ravel())
plt.plot(xx, regr.intercept_+regr.coef_*xx, label='Linear regression (Scikit-learn GLM)')

plt.xlim(4,24)
plt.xlabel('Population of City in 10,000s')
plt.ylabel('Profit in $10,000s')
plt.legend(loc=4);
```

![4](C:\Users\Administrator\Pictures\Saved Pictures\4.png)

```python
# 预测一下人口为35000和70000的城市的结果
print(theta.T.dot([1, 3.5])*10000)
print(theta.T.dot([1, 7])*10000)
```

[ 4519.7678677]

[ 45342.45012945]

### 2.5逻辑斯特回归示例

```python
逻辑回归示例
# %load ../../standard_import.txt
import pandas as pd
import numpy as np
import matplotlib as mpl
import matplotlib.pyplot as plt

from scipy.optimize import minimize

from sklearn.preprocessing import PolynomialFeatures

pd.set_option('display.notebook_repr_html', False)
pd.set_option('display.max_columns', None)
pd.set_option('display.max_rows', 150)
pd.set_option('display.max_seq_items', None)
 
#%config InlineBackend.figure_formats = {'pdf',}
%matplotlib inline

import seaborn as sns
sns.set_context('notebook')
sns.set_style('white')
```

```python
def loaddata(file, delimeter):
    data = np.loadtxt(file, delimiter=delimeter)
    print('Dimensions: ',data.shape)
    print(data[1:6,:])
    return(data)
```

```python
def plotData(data, label_x, label_y, label_pos, label_neg, axes=None):
    # 获得正负样本的下标(即哪些是正样本，哪些是负样本)
    neg = data[:,2] == 0
    pos = data[:,2] == 1
    
    if axes == None:
        axes = plt.gca()
    axes.scatter(data[pos][:,0], data[pos][:,1], marker='+', c='k', s=60, linewidth=2, label=label_pos)
    axes.scatter(data[neg][:,0], data[neg][:,1], c='y', s=60, label=label_neg)
    axes.set_xlabel(label_x)
    axes.set_ylabel(label_y)
    axes.legend(frameon= True, fancybox = True);
```

```python
data = loaddata('data1.txt', ',')
X = np.c_[np.ones((data.shape[0],1)), data[:,0:2]]
y = np.c_[data[:,2]]
plotData(data, 'Exam 1 score', 'Exam 2 score', 'Pass', 'Fail')
```

![5](C:\Users\Administrator\Pictures\Saved Pictures\5.png)

```python
#定义sigmoid函数
def sigmoid(z):
    return(1 / (1 + np.exp(-z)))

#定义损失函数
def costFunction(theta, X, y):
    m = y.size
    h = sigmoid(X.dot(theta))  
    J = -1.0*(1.0/m)*(np.log(h).T.dot(y)+np.log(1-h).T.dot(1-y))           
    if np.isnan(J[0]):
        return(np.inf)
    return J[0]

#求解梯度
def gradient(theta, X, y):
    m = y.size
    h = sigmoid(X.dot(theta.reshape(-1,1)))
    
    grad =(1.0/m)*X.T.dot(h-y)

    return(grad.flatten())
    
initial_theta = np.zeros(X.shape[1])
cost = costFunction(initial_theta, X, y)
grad = gradient(initial_theta, X, y)
print('Cost: \n', cost)
print('Grad: \n', grad)
```

('Cost: \n', 0.69314718055994518)
('Grad: \n', array([ -0.1       , -12.00921659, -11.26284221]))

```python
res = minimize(costFunction, initial_theta, args=(X,y), jac=gradient, options={'maxiter':400})
res
```

 status: 0
  success: True
​     njev: 28
​     nfev: 28
 hess_inv: array([[  3.24739469e+03,  -2.59380769e+01,  -2.63469561e+01],
​       [ -2.59380769e+01,   2.21449124e-01,   1.97772068e-01],
​       [ -2.63469561e+01,   1.97772068e-01,   2.29018831e-01]])
​      fun: 0.20349770158944075
​        x: array([-25.16133401,   0.20623172,   0.2014716 ])
  message: 'Optimization terminated successfully.'
​      jac: array([ -2.73305312e-10,   1.43144026e-07,  -1.58965802e-07])



```python
plt.scatter(45, 85, s=60, c='r', marker='v', label='(45, 85)')
plotData(data, 'Exam 1 score', 'Exam 2 score', 'Admitted', 'Not admitted')
x1_min, x1_max = X[:,1].min(), X[:,1].max(),
x2_min, x2_max = X[:,2].min(), X[:,2].max(),
xx1, xx2 = np.meshgrid(np.linspace(x1_min, x1_max), np.linspace(x2_min, x2_max))
h = sigmoid(np.c_[np.ones((xx1.ravel().shape[0],1)), xx1.ravel(), xx2.ravel()].dot(res.x))
h = h.reshape(xx1.shape)
plt.contour(xx1, xx2, h, [0.5], linewidths=1, colors='b');
```

![6](C:\Users\Administrator\Pictures\Saved Pictures\6.png)

```python
data2 = loaddata('data2.txt', ',')
# 拿到X和y
y = np.c_[data2[:,2]]
X = data2[:,0:2]
# 画个图
plotData(data2, 'Microchip Test 1', 'Microchip Test 2', 'y = 1', 'y = 0')
```

![7](C:\Users\Administrator\Pictures\Saved Pictures\7.png)

```python
poly = PolynomialFeatures(6)
XX = poly.fit_transform(data2[:,0:2])
# 看看形状(特征映射后x有多少维了)
XX.shape
```

(118.28)

```python
# 定义损失函数
def costFunctionReg(theta, reg, *args):
    m = y.size
    h = sigmoid(XX.dot(theta))
    
    J = -1.0*(1.0/m)*(np.log(h).T.dot(y)+np.log(1-h).T.dot(1-y)) + (reg/(2.0*m))*np.sum(np.square(theta[1:]))
    
    if np.isnan(J[0]):
        return(np.inf)
    return(J[0])
# 定义梯度
def gradientReg(theta, reg, *args):
    m = y.size
    h = sigmoid(XX.dot(theta.reshape(-1,1)))
      
    grad = (1.0/m)*XX.T.dot(h-y) + (reg/m)*np.r_[[[0]],theta[1:].reshape(-1,1)]
        
    return(grad.flatten())

initial_theta = np.zeros(XX.shape[1])
costFunctionReg(initial_theta, 1, XX, y)
```

0.69314718055994529

```python
fig, axes = plt.subplots(1,3, sharey = True, figsize=(17,5))

# 决策边界，咱们分别来看看正则化系数lambda太大太小分别会出现什么情况
# Lambda = 0 : 就是没有正则化，这样的话，就过拟合咯
# Lambda = 1 : 这才是正确的打开方式
# Lambda = 100 : 卧槽，正则化项太激进，导致基本就没拟合出决策边界

for i, C in enumerate([0.0, 1.0, 100.0]):
    # 最优化 costFunctionReg
    res2 = minimize(costFunctionReg, initial_theta, args=(C, XX, y), jac=gradientReg, options={'maxiter':3000})
    
    # 准确率
    accuracy = 100.0*sum(predict(res2.x, XX) == y.ravel())/y.size    

    # 对X,y的散列绘图
    plotData(data2, 'Microchip Test 1', 'Microchip Test 2', 'y = 1', 'y = 0', axes.flatten()[i])
    
    # 画出决策边界
    x1_min, x1_max = X[:,0].min(), X[:,0].max(),
    x2_min, x2_max = X[:,1].min(), X[:,1].max(),
    xx1, xx2 = np.meshgrid(np.linspace(x1_min, x1_max), np.linspace(x2_min, x2_max))
    h = sigmoid(poly.fit_transform(np.c_[xx1.ravel(), xx2.ravel()]).dot(res2.x))
    h = h.reshape(xx1.shape)
    axes.flatten()[i].contour(xx1, xx2, h, [0.5], linewidths=1, colors='g');       
    axes.flatten()[i].set_title('Train accuracy {}% with Lambda = {}'.format(np.round(accuracy, decimals=2), C))
```

![8](C:\Users\Administrator\Pictures\Saved Pictures\8.png)

------

## 3.树模型初步与进阶

决策树模型（Decision Tree Model)是以**模拟**人类**决策过程**思想的模型![15](C:\Users\Administrator\Pictures\Saved Pictures\15.jpg)

### 3.1决策树与分类

#### 3.1.1决策树模型概述

决策树基于“树”结构进行决策

> 每个“内部结点”对应于某个属性是的“测试”
>
> 每个分支对应于该测试的一种可能结果（即该属性的某个取值）
>
> 每个“叶结点”对应于一个“预测结果”

学习过程>>通过对训练样本的**分析**来确定“**划分属性**”

预测过程>>将测试示例从**根结点**开始，沿着**划分**属性所构成的“判定测试序列”下行，直到叶结点

决策树简史

第一个决策树算法>>CLS（Concept Learning System）（1966）

使决策树受到关注、成为机器学习**主流技术**的算法>>ID3 （1979）

最**常用**的决策树算法>>C4.5（1993）

可以用于**回归任务**的决策树算法>>CART(Classification and Regression Tree)(1984)

基于决策树的**最强大**算法>>RF（Random Forest）

#### 3.1.2算法流程与最佳属性选择

总体流程>>**“分而治之”**

三种停止条件>>

- 当前结点包含的样本全属于同一类别，无需划分；
- 当前属性集为空，或是所有样本在所有属性上取值相同，无法划分；
- 当前结点包含的样本集合为空，不能划分。

**信息熵**（entropy）是度量样本集合**“纯度”**最常用的一个指标，假定当前样本集合D中第k类样本中所占的比例为p_k,则D的信息熵定义为
$$
Ent(D)=-\sum_{k=1}^{|y|}p_klog_2p_k
$$
Ent(D)的值越小，则D的纯度约高

**信息增益**直接以信息熵为基础，计算当前划分对信息熵所造成变化

信心增益（information gain）>>ID3中使用>>以属性a对数据集D进行划分所获得的信息增益为
$$
Gain(D,a)=Ent(D)-\sum_{v=1}^{V}\frac{|D^V|}{|D|}End(D^V)
$$
信息增益的问题>>对取值数目较多的属性有所偏好

**信息增益率**（gain ratio）>>C4.5中使用
$$
Gain\_ratio(D,a)=\frac{Gain(D,a)}{IV(a)}
$$

$$
其中 IV（a)=-\sum_{v=1}^{V}\frac{|D^v|}{|D|}log_2\frac{|D^v|}{|D|}
$$



~~属性a的可能取值数目越多，即V越大，则IV（a）的值通常就越大~~

> 启发式>>先从候选划分属性中找出信息增益高出平均水平的，再从中选取出增益率最高的

**基尼指数**（gini index）>>CART中使用
$$
Gini(D)=\sum_{k=1}^{|y|}\sum_{k^\prime}p_kp_{k^\prime}=1-\sum_{k=1}^{|y|}p_k^2
$$
反映了从D中随机抽取俩个个样例，其类别标记不一致的概率

Gini(D)越小，数据集D的纯度越高

属性a的基尼指数>>
$$
Gini\_index(D,a)=\sum_{v=1}^{V}\frac{|D^v|}{|D|}Gini(D^v)
$$
在候选属性集合中，选取那个使**划分后基尼指数最小**的属性

基尼指数、熵、分类误差率三者之间的关系![16](C:\Users\Administrator\Pictures\Saved Pictures\16.jpg)

熵与**信息论**视角

二分类视角看CART

- 每一个产生分支的过程就是一个二分类过程
- 这个过程叫做“决策树桩”>>decision stump
- 一棵CART是由许多决策树桩拼接起来的
- decision stump是只有一层的决策树

![17](C:\Users\Administrator\Pictures\Saved Pictures\17.jpg)

信息论视角理解>>对于多分叉树的情况，用信息论的视角来观察>>机器学习其实是**破解密码**的过程

![18](C:\Users\Administrator\Pictures\Saved Pictures\18.jpg)

![19](C:\Users\Administrator\Pictures\Saved Pictures\19.jpg)

**三种不同的决策树**

- ID3>>取值多的属性，更容易使数据更纯，其信息增益更大；训练得到的是一棵庞大且深度浅的树-->不合理
- C4.5>>采用信息增益率替代信息增益
- CART>>以基尼系数替代熵；最小化不纯度，而不是最大化信息增益

#### 3.1.3剪枝与控制过拟合

为了尽可能正确分类训练样本，有可能造成分支过多，造成过拟合

剪枝>>通过**主动去掉**一些分支来降低过拟合的风险

基本策略>>

- 预剪枝（prt-prining)>>提前终止某些分支的生长
- 后剪枝（post-pruning>>生成一棵完全树，再“回头”剪枝

剪枝过程中需评估剪枝前后决策树的优劣>>使用之前提到的“留出法”进行评估

预剪枝 vs. 后剪枝

时间开销

- 预剪枝>>训练时间开销**降低**，测试时间开销**降低**
- 后剪枝>>训练时间开销**增加**，测试时间开销**降低**

过/欠拟合风险

- 预剪枝>>过拟合风险**降低**，欠拟合风险增加
- 后剪枝>>过拟合风险**降低**，欠拟合风险基本不变

泛化性能

**后剪枝通常优于预剪枝**

#### 3.1.4案例讲解

```python
#把需要的工具包import进来
#用于数据处理和分析的工具包
import pandas as pd
#引入用于数据预处理/特征工程的工具包
from sklearn import preprocessing
#import决策树建模包
from sklearn import tree
```

```python
#读取数据
adult_data = pd.read_csv('./DecisionTree.csv')
#看一下数据
adult_data.head(5)
adult_data.info()
adult_data.columns
```

```python
#区分一下特征（属性）和目标
feature_columns = [u'workclass', u'education', u'marital-status', u'occupation', u'relationship', u'race', u'gender', u'native-country']
label_column = ['income']
```

```python
#区分特征和目标列
features = adult_data[feature_columns]
label = adult_data[label_column]
```

```python
#特征处理/特征工程
features = pd.get_dummies(features)
```

```python
#构建模型
#初始化一个决策树分类器
clf = tree.DecisionTreeClassifier(criterion='entropy', max_depth=4)
#用决策树分类器拟合数据
clf = clf.fit(features.values, label.values)
clf
clf.predict(features.values
```

DecisionTreeClassifier(class_weight=None, criterion='entropy', max_depth=4,
​            max_features=None, max_leaf_nodes=None,
​            min_impurity_decrease=0.0, min_impurity_split=None,
​            min_samples_leaf=1, min_samples_split=2,
​            min_weight_fraction_leaf=0.0, presort=False, random_state=None,
​            splitter='best')

array([' <=50K', ' <=50K', ' <=50K', ..., ' <=50K', ' <=50K', ' >50K'], dtype=object)

```python
#可视化一下这棵决策树
import pydotplus
from IPython.display import display, Image
dot_data = tree.export_graphviz(clf, 
                                out_file=None, 
                                feature_names=features.columns,
                                class_names = ['<=50k', '>50k'],
                                filled = True,
                                rounded =True
                               )
graph = pydotplus.graph_from_dot_data(dot_data)
display(Image(graph.create_png()))
```

![10](C:\Users\Administrator\Pictures\Saved Pictures\10.png)

### 3.2分类回归树与随机森林

分类树有时候是会有连续值的，这时候需要另外的解决方案了，也就是在前面讲的决策树回归问题扩展到连续值决策树回归问题

#### 3.2.1连续值和缺省值的处理

**连续值处理**

基本思路>>**连续属性离散化**

常见做法>>二分法（bi-partition）

- n个属性值可形成（n-1）个候选划分
- 把候选划分之当作离散属性处理，寻找最佳属性

**缺失值处理**

现实应用中，经常会遇到属性值缺失的现象

只使用没有缺失值的样本就会造成数据的**极大浪费**

如果使用带缺失值的样例，需解决几个问题>>如何进行划分属性选择？给定划分属性，若样本在该属性上的值缺失，如何进行划分？

基本思路>>**样本赋权，权重划分**

- 一棵决策树对应一个“规则集”
- 每个从根结点到叶结点的分支路劲对应于一条规则

#### 3.2.2回归树模型

![20](C:\Users\Administrator\Pictures\Saved Pictures\20.jpg)

**递归二分** 

**自顶向下**的**贪婪式递归**方案

> - 自顶向下>>从所有样本开始，不断从当前位置，把样本切分到2个分支里
> - 贪婪>>每一次的划分，只考虑当前最优，而不回过头考虑之前的划分

选择切分的维度（特征）x_j,以及切分点s使得划分后的树RSS结果最小
$$
R_1(j,s)=\{x|x_j<s\}
$$

$$
R_2(j,s)=\{x|x_j\ge s\}
$$

$$
RSS=\sum_{x_i\in R_1(j,s)}(y_i-\bar{y_{R_1}})^2+\sum_{x_i\in R_2(j,s)}(y_i-\bar{y_{R_2}})^2
$$

![21](C:\Users\Administrator\Pictures\Saved Pictures\21.jpg)

**回归树剪枝**

如果让回归树充分生长，同样会有过 拟合的风险

> 解决办法>>添加L2正则化衡量
>
> 考虑剪枝后得到的子树{T_α}，其中α是正则化项的系数，当我固定一个α后，最佳的T_α就是使得下列式子值最小的子树
> $$
> \sum_{m=1}^{|T|}\sum_{x_i\in Rm}(y_i-\bar{(y_{R_2})})^2+\alpha|T|
> $$
> 其中|T|是回归树叶子节点的个数
>
> 其中的α可以通过 交叉验证去选择

#### 3.2.3bagging与随机森林

在介绍强大的RandomForest(随机森林)之前，我们先介绍一下Bootstraping和Bagging

Bootstraping>>名字来自成语“pull up by your own bootstraps”，意思是依靠你自己的资源，称为**自助法**，它是一种有**放回的抽样**方法，是非参数统计中的一种重要的估计统计量方差进而进行区间估计的统计方法。

> 1. 采用重采样技术从原始样本中抽取一定数量（自己给定）的样本，此过程允许重复抽样
> 2. 根据抽出的样本计算给定的统计量T。
> 3. 重复上述N次（一般大于1000），得到N个统计量T。
> 4. 计算上述N个统计量T的样本方差，得到统计量的方差

Bootstrap是现代统计学**较为流行**的一种统计方法，在小样本时效果很好。通过**方差的估计可以构造置信区间**等，其运用范围得到进一步**延伸**。

**Bagging思想**

Bagging是bootstrap aggregating的缩写，使用了上述的bootstraping思想。

> Bagging降低过拟合风险，提高泛化能力

![22](C:\Users\Administrator\Pictures\Saved Pictures\22.jpg)

**随机森林**

RandomForest(随机森林)是一种**基于树模型**的**Bagging的优化**版本。核心思想依旧是bagging，但是做了一些独特的改进。

> RF使用了CART决策树作为基学习器，具体过程如下
>
> - 输入为样本集D={（x1,y1）(x2,y2),(x3,y3),...,(xm,ym)}
>
> 对于t=1,2...,T;
>
> 1. 对训练集进行第t次随机采样，共采集m次，得到包含m个样本的采样集D_m
> 2. 用采样集D_m训练第m个决策树模型G_m(x)，在训练决策树模型的节点的时候，在节点上所有的样本特征中选择一部分样本特征，在这些随机选择的部分样本特征选择一个最优的特征来做决策树的左右子树划分
>
> - 分类场景，则T个基模型（决策树）投出最多票数的类别作为最终类别。回归场景，T个基模型（回归树）得到的回归结果进行算术平均得到的值最为最终的模型输出

![23](C:\Users\Administrator\Pictures\Saved Pictures\23.jpg)

#### 3.2.4案例讲解

```python
#加载工具包
import pandas as pd
from sklearn import preprocessing
from sklearn import tree
from sklearn.datasets import load_iris

#载入数据和设置标签（属性)并查看这些标签，数据是包里自带的一种花卉的识别
iris = load_iris()
dir(iris)
iris_feature_name = iris.feature_names
iris_features = iris.data
iris_target_name = iris.target_names
iris_target = iris.target
iris_feature_name
iris_features[:5,:]
iris_target_name
iris_target
iris_features.shape
```

```python
#构建模型
clf = tree.DecisionTreeClassifier(max_depth=4)
clf = clf.fit(iris_features, iris_target)
clf
```

DecisionTreeClassifier(class_weight=None, criterion='gini', max_depth=4,
​            max_features=None, max_leaf_nodes=None,
​            min_impurity_decrease=0.0, min_impurity_split=None,
​            min_samples_leaf=1, min_samples_split=2,
​            min_weight_fraction_leaf=0.0, presort=False, random_state=None,
​            splitter='best')

```python
#可视化这棵决策树
import pydotplus
from IPython.display import Image, display
dot_data = tree.export_graphviz(clf,
                                out_file = None,
                                feature_names = iris_feature_name,
                                class_names = iris_target_name,
                                filled=True,
                                rounded=True
                               )
graph = pydotplus.graph_from_dot_data(dot_data)
display(Image(graph.create_png()))
```

![11](C:\Users\Administrator\Pictures\Saved Pictures\11.png)

### 3.3最大熵与EM算法

#### 3.3.1统计学基础回顾

几个概念解释

先验概率>>根据**以往经验和分析得到的概率**，如全概率公式，它往往作为“由因求果”问题中的“因”出现。

后验概率>>依据得到“结果”信息所计算出的最有可能是那种事件发生的，如贝叶斯公式中的，是“**执果寻因**”问题中的“因”。后验概率可以根据通过贝叶斯公式，用先验概率和似然函数计算出来。

贝叶斯定理>>假设B1,B2,...,Bn互斥且构成一个完全事件，已知他们的概率P（Bi）,i=1,2,3,...,n,现观察到某事件A与B1，B2，...，Bn相伴随机出现，且已知条件概率P（A|Bi）求P（Bi|A）
$$
P(B_i|A)=\frac{P(B_i)P(A|B_i)}{\sum_{j=1}^{n}P(B_j)P(A|B_j)}
$$
极大似然估计(MLE)>>已知某个随机样本满足某种概率分布，但是其中**具体的参数不清楚**，参数估计就是通过若干次试验，观察其结果，利用**结果推出参数的大概**值。最大似然估计是建立在这样的思想上：已知某个参数能使这个样本出现的概率最大，我们当然不会再去选择其他小概率的样本，所以干脆就把这**个参数作为估计的真实值**。
$$
L(x_1,x_2,\dots,x_n;\theta_1,\theta_2,\dots,\theta_k)=\prod_{i=1}^{n}f(x_i;\theta_1,\theta_2,\dots,\theta_k)
$$

> 求最大似然函数估计值的一般步骤：
> 1） 写出似然函数；
> 2） 对似然函数取对数，得到对数似然函数；
> 3） 对对数似然函数进行求导，解logL(θ1,θ2,...,θk)=∑ni=1f(xi;θ1,θ2,...,θk)得到驻点；
> 4） 分析驻点是极大值点。

#### 3.3.2熵

**信息**>>i(x)=-log(p(x))概率是对**确定性**的度量，那么信息就是就是对不确定性的度量

**独立事件的信息**>>如果两个事件X和Y独立，即P(XY)=P(X)P(Y)，假定x和y的信息量分别为i(x)和i(y)，则二者同时发生的信息量应该为i(x^y)=i(x)+i(y)

熵>>对随机变量平**均不确定性**的度量。一个系统越是有序，信息熵就越低；反之，一个系统越是混乱，信息熵就越高。所以说，信息熵可以被认为是系统有序化程度的一个度量。不确定性越大，熵值越大；若随机变量退化成定值，熵为0。熵是**自信息有序化**的期望。
$$
H（X）=-\sum_{x\in X}P(x)logP(x)
$$
![24](C:\Users\Administrator\Pictures\Saved Pictures\24.jpg)



**互信息**>>i(y,x)=i(x,y)

**平均互信息**>>决策树中的“信息增益”其实就是平均互信息I（X,Y）

![25](C:\Users\Administrator\Pictures\Saved Pictures\25.jpg)

#### 3.3.3最大熵模型

最大熵理论>>在无外力作用下，食物总是**朝着最混乱**的方向发展。事物是约束和自由的统一体。事物总是在约束下争取最大的自由权，这其实也是自然界的根本原则。在已知条件下，**熵最大的事物，最可能接近它的真实状态**。最大熵原理的一个基本假设就是>>认为已知的事物是一种约束，未知的条件是均匀分布且没有偏见的。

最大熵原理是统计学的一般原理，也是概率模型学习的一个准则。最大熵原则认为，学习概率模型时，在所有可能的概率模型中，**熵最大的模型就是最好的模型**。

最大熵原理进行机器学习-->比如用最大条件熵求最大条件概率

​	1.定义条件熵>>最大熵的目标是定义一个熵，条件熵实际上就是要找的模型。	最大化条件熵得到的结果是要找到一个条件概率对应的分布，条件概率的分布就是要求的模型，所以，要求的就是条件概率，可以用条件熵定义目标函数。条件熵最大的时候对应的条件概率就是要求的条件概率。
$$
H（y|x）=-\sum_{(x,y)\in z}p(y,x)log_2p(y|x)
$$
​	2.模型目的>>找到条件熵。公式中P*表示理想概率，公式表示最大化条件熵对应的自变量
$$
p^*(y|x)=arg\max{p(y|x)\in P}H(y|x)
$$
​	3.定义特征函数>>把其他约束条件携程期望相等的形式。
$$
f_i(x,y)\in \{0,1\}  \quad i=1,2,\dots,m
$$
​	4.约束条件>>定义
$$
\sum_{y\in Y}p(y|x)=1
$$

$$
E(f_i)=\bar{E(f_i)}\quad i=1,2,\dots,m
$$

其中，
$$
\bar{E(f_i)}=\sum_{(x,y)\in Z}\bar{p}(x,y)f_i(x,y)=\frac{1}{N}\sum_{(x,y)\in T}f_i(x,y)\quad N=|T|
$$

$$
{E(f_i)}=\sum_{(x,y)\in Z}{p}(x,y)f_i(x,y)=\sum_{(x,y)\in Z}p(x)p(y|x)f_i(x,y)
$$

#### 3.3.4EM算法

EM算法直观解释

**期望最大化算法**，假如从来没打过枪的小明和狩猎很多年的猎人在森林中发现了一只猎物，两人同时开了一枪，猎物死亡，问这一枪是谁打出的？

这个问题由于只开了一枪，所以命中猎物的最大可能就是猎人。这里面就包含了EM思想，因为只有猎人开了这一枪，猎物才会有极大可能会死亡。

现在，换个问题，有两个人，小明和小花，我们不知道他们谁是猎人，谁是小白，现在他们一共开了100枪，打死了100只兔子中的20只，现在就需要判断每一只打死的兔子是谁打死的？

对这个问题进行分析，首先这个问题求解要先知道小明和小花的命中分布，还要知道这个命中兔子的分布，这样才能求出每个兔子最有可能是被谁打死的，但是问题的关键就是在这儿，即没有给出小明小花的命中分布，也没有给出兔子命中的分布，好像就是一个鸡生蛋，蛋生鸡的问题，这似乎是进入了一个死循环了，但是，仔细分析就会发现这样一个现象，这个命中率分布暗含了小明和小花的命中率分别为P,Q,由于不知道他们的具体分布，但是我们知道它们肯定都属于高斯分布，因此，我们可以先随便设定一对初始的PQ分布，代入到期望表达式中，算出命中结果的最大似然结果，如果和现有结果有很大出入，则重新调整PQ，重新计算，直到PQ的值不再变化或者收敛于某一个值附近。

**算法整体框架**

Repeat until convergence{

​	(E-step)For each i,set
$$
Q_i(z^{(i)}):=p(z^{(i)}|x^{(i)}\theta)
$$
​	(M-step) Set 
$$
\theta:=arg \max_{x^{(i)}}\sum_{i}\sum_{z^{(i)}}Q_i(z^{(i)})log\frac{p(x^{(i)},z^{(i)});\theta)}{Q_i(z^{(i)})}
$$
}

推导过程见html文件>>EM的推导以及python实现

```python
#代码实现EM算法
import numpy as np
ys = np.array([(5,5), (9,1), (8,2), (4,6), (7,3)])
thetas = np.array([[0.6, 0.4], [0.5, 0.5]])  # 初始化两个theta
pis =np.array([0.5,0.5])  # 随手拿出A还是B硬币的概率都设为0.5

tolerance = 0.01
max_iter = 100

loglike_old = 0
for i in range(max_iter):
    E_c1 = []
    E_c2 = []
    EcY_1 = []
    EcY_2 = []
    loglike_new = 0
    # E步骤: 
    for i in range(len(ys)):

        # multinomial log likelihood （对于这个案例，我们用的是伯努利）
        log_k1 = np.sum([ys[i]*np.log(thetas[0])])  #  \log [\theta_k^{y_{oi}} (1-\theta_k)^{n - y_{oi}} ]  
        log_k2 = np.sum([ys[i]*np.log(thetas[1])])  #  \log [\theta_k^{y_{oi}} (1-\theta_k)^{n - y_{oi}} ] 

        # 得到 c_ik 的期望
        denom = np.exp(log_k1) * pis[0] + np.exp(log_k2) * pis[1]
        E_ci1 = np.exp(log_k1) * pis[0] / denom
        E_ci2 = np.exp(log_k2) * pis[1] / denom

        # 更新完整的 log likelihood  
        # 我们只在这一步检查它是否converge，并不更新theta 
        loglike_new += E_ci1 * log_k1 + E_ci2 * log_k2
        E_c1.append(E_ci1)
        E_c2.append(E_ci2)

    # M步骤：
    for i in range(len(ys)):
        EcY_1.append(E_c1[i] * ys[i] )  
        EcY_2.append(E_c2[i] * ys[i] )
    thetas[0] = np.sum(EcY_1, 0)/np.sum(EcY_1)
    thetas[1] = np.sum(EcY_2, 0)/np.sum(EcY_2)
    print("Iteration: %d" % (i+1))
    print("theta_A = %.2f, theta_B = %.2f, difference in loglike = %.2f" % (thetas[0,0], thetas[1,0], loglike_new - loglike_old))

    if np.abs(loglike_new - loglike_old) < tolerance:
        break
    loglike_old = loglike_new
```

Iteration: 5
theta_A = 0.71, theta_B = 0.58, difference in loglike = -32.69
Iteration: 5
theta_A = 0.75, theta_B = 0.57, difference in loglike = 1.43
Iteration: 5
theta_A = 0.77, theta_B = 0.55, difference in loglike = 0.50
Iteration: 5
theta_A = 0.78, theta_B = 0.53, difference in loglike = 0.43
Iteration: 5
theta_A = 0.79, theta_B = 0.53, difference in loglike = 0.26
Iteration: 5
theta_A = 0.79, theta_B = 0.52, difference in loglike = 0.12
Iteration: 5
theta_A = 0.80, theta_B = 0.52, difference in loglike = 0.05
Iteration: 5
theta_A = 0.80, theta_B = 0.52, difference in loglike = 0.02
Iteration: 5
theta_A = 0.80, theta_B = 0.52, difference in loglike = 0.01

------

## 4.支持向量机初步与进阶

Support Vectot Machine

### 4.1支持向量机（上）

基本形式>>**SVM是一个有监督的二分类线性的凸优化模型**

扩展形式>>

- 有监督二分类非线性分类模型
- 有监督多分类（线性/非线性）分类模型
- 有监督线性回归模型（SVR）
- 基于核函数的SVM/SVR

#### 4.1.1二分类线性可分支持向量机

线性模型>>特征的线性组合进行分类

表达式
$$
f(x)=w^Tx+b
$$
核心想法>>**最大间隔分类器**

- 离数据最远的线性分类器最安全
- 离数据最远的线性分类器最容易泛化

SVM是线性模型中的一种

与逻辑回归对比，逻辑回归给出的是一个概率值，损失函数是一个交叉熵的表达式，等价于最大似然函数/交叉熵损失函数。正则项是一个L2型正则项，目标函数的形式都是一个损失函数+正则项

SVM的**预测函数**
$$
y=sgn（w^Tx)
$$
SVM的损失函数(分类误差)>>**Hinge损失函数**(铰链曲线)
$$
L（x,y）=max\{0,1-yw^Tx\}
$$
SVM的正则化
$$
|w|_2^2
$$
除了防止模型过拟合外，还对应于分类决策面的间隔

SVM的目标函数
$$
l(x,y)=\frac{1}{n}max\{0,1-y_iw^Tx_i\}+\frac{\lambda}{2}|w|_2^2
$$
要点

> 模型形式>>线性模型
>
> 损失函数>>Hinge损失函数
>
> 正则项>>L2正则防止过拟合，最大化分类间隔

与逻辑回归的对比

![38](C:\Users\Administrator\Pictures\Saved Pictures\38.jpg)

总结

![39](C:\Users\Administrator\Pictures\Saved Pictures\39.jpg)

#### 4.1.2二分类线性不可分支持向量机

线性SVM几何解释

数据到分类器的间隔>>最大问题最小化，前提是所有数据点被正确分类

约束优化形式
$$
min|w|_2^2
$$

$$
s.t. \quad y_iw^Tx_i\ge1,\forall i\in[n]
$$

非约束优化形式
$$
minl(x,y)=\frac{1}{n}\sum_{i=1}^{n}max\{0,1-y_iw^Tx_i\}+\frac{\lambda}{2}|w|_2^2
$$
SVM 的**约束优化问题等价于约束优化问题**

**松弛变量**

引入松弛变量\epsilon_i；允许线性不可分的点到分类器距离小于零
$$
y_iw^Tx_i\ge1-\epsilon_i,
$$

$$
\epsilon_i\ge0\quad\forall i\in[n]
$$



![40](C:\Users\Administrator\Pictures\Saved Pictures\40.jpg)

- 线性可分与线性不可分统一的形式
- SVM是数据自适应的
- 本质是一个凸优化问题，二次规划
- 可以转换为二次规划一般形式求解，也可以用梯度下降法求解

#### 4.1.3多分类支持向量机

**One vs One**

训练**k(k-1)/2**个二分类器f_i,j(x)

f_i,j(x)预测x预测是第i类的可能性大于第j类的可能性

时间复杂度O(n^2)

使用全部的k(k-1)/2个分类器

预测x为胜利次数最多的类别

优点>>适用性广，LibSVM默认的实现方法

​		对于所有二分类器都可以使用

缺点>>训练时刻和测试时刻的时间复杂度都很高

**One vs All**

训练时刻>>训练**k个**二分类器f_i(x)

f_i(x)预测x属于第i类的分数

使用全部k个分类器

预测x为得分最高的类别

缺点>>适用性有限，要求f_i(x)表示x属于第i类的一个打分

​		多使用于概率分类器，例如逻辑回归

优点>>事件复杂度低O(k)

#### 4.1.3SVM工具包

**LibSVM**>>https://www.csie.ntu.edu.tw/~cjlin/libsvm/

支持多种编程语言，提供命令行使用接口

支持线性/非线性SVM，支持分类和回归

目前最流行并且高效的SVM开源实现

**SVMLight**>>http://svmlight.joachims.org/

C/C++实现

支持基于SVM的结构预测以及半监督SVM

支持基于SVM的排序算法

**Scikit-learn**>>http://scikit-learn.org/stable/modules/svm.html

Python实现，轻量级，接口简单，适合科研使用

支持线性/非线性，分类/回归 SVM

### 4.2支持向量机（下）

#### 4.2.1SVM对偶形式

- 目标函数是关于w是**二次函数**
- 约束条件关于w是**线性函数**
- 核心是二次凸优化问题（Quadratic Programming)
  - **光滑**优化函数
  - **局部最优解即全局最优解**

**凸集合(Convex set）**

**凸函数(Convex)**
$$
\lambda f(x)+(1-\lambda)f(x')\ge f(\lambda x+(1-\lambda) x')) \quad for\quad\lambda\in[0,1]
$$
凸优化问题的一般优化形式
$$
minimizef(x)
$$

$$
subject\quad to\quad c_i(x)\le0\quad \forall i
$$

**Lagrange乘子法**>>将约束优化转换为非约束优化

- 为每一个不等式约束引入一个Lagrange乘子𝜆 𝑗Lagrange乘子𝜆 𝑗 ≥ 0,∀𝑗 ∈ [𝑛]
- 将原来的minimize问题变为一个minimax问题
- 通过Lagrange乘子法将约束优化问题转换为非约束优化问题

$$
\min_x\max_{\lambda_i\ge0}\quad f(x)+\sum_{i=1}^{n}\lambda_ic_i(x)
$$

$$
P(Primal)\quad \min_x\max_{\lambda_i\ge0}\quad f(x)+\sum_{i=1}^{n}\lambda_ic_i(x)
$$

$$
D(Dual)\quad\max_{\lambda_i\ge0}\min_x\quad f(x)+\sum_{i=1}^{n}\lambda_ic_i(x)
$$

**Lagrange函数**
$$
\mathcal{L}(X,\lambda)=f(x)+\sum_{i=1}^{n}\lambda_ic_i(x)
$$
**对偶理论（Duality Theory)**
$$
\min_x\max_\lambda\mathcal{L}(x,\lambda)=\max_x\min_x \mathcal{L}(x,\lambda)
$$
定义对偶函数
$$
g(\lambda)=\min_x\mathcal{L}(x,\lambda)
$$
对于凸优化问题（convex optimization problems),可以通过求解对偶问题的最优解来解决原问题

![41](C:\Users\Administrator\Pictures\Saved Pictures\41.jpg)

![42](C:\Users\Administrator\Pictures\Saved Pictures\42.jpg)

#### 4.2.2核函数以及核技巧

特征映射

将输入数据从低纬空间映射到高维空间的函数变换，使得变换后的数据更加容易处理（分类/回归）
$$
\phi(x)=(x_1^2,2^\frac{1}{2}x_1x_2,x_2^2)
$$

$$
\phi(x)\cdot\phi(x')=(x_1x_1'+x_2x_2')^2
$$

多项式特征变换

更高维的多项式变换会引入更多的特征，极大增加计算复杂度

核函数

**关键想法**>>我们不需要显式地计算出特征映射，只需要变换后特征的内积！

• 核函数隐式地定义了一个特征映射：∃𝜙,s.t., 𝐾(x,x ′) = 𝜙(x) ∙ 𝜙(x ′)
• 核函数的计算在原空间：计算复杂度低
![43](C:\Users\Administrator\Pictures\Saved Pictures\43.jpg)

![44](C:\Users\Administrator\Pictures\Saved Pictures\44.jpg)

#### 4.2.3非线性支持向量机

如何将线性支持向量机扩展为非线性支持向量机

步骤>>

1. 将线性内积（线性核函数）替换为K(xi,xj)
2. 新模型在变换后的空间仍然是线性模型
3. 新模型在原空间相对于x是非线性模型
4. 计算复杂度较小-->只需计算核矩阵K=K_ij=K(xi,xj)

- 凸二次规划问题
- 可以球的全局最优解
- 和线性SVM对偶问题的形式几乎一样，只是将核函数换了

**SMO算法**

SMO算法是Coordinate ascent算法一个特例

- 坐标上升算法

- 适用于光滑优化问题

- 优化多个变量

- 每次仅优化其中一个变量，固定其他所有变量不变，直至算法收敛
- 目前SVM求解的最快算法，也是LibSVM的默认实现算法，通常远快于梯度下降算法

#### 4.2.4支持向量回归

回归损失函数的一般框架

回归损失函数
$$
l(y,f(x))=\frac{1}{n}\sum_{i=1}^{n}l(y_i,f(x_i))
$$
正则化
$$
\Omega(f)=\frac{1}{2}|w|_2^2
$$
回归约束优化问题
$$
\min\quad\frac{\lambda}{2}|w|_2^2+\frac{C}{n}\sum_{i=1}^{n}l(\epsilon_i)
$$

$$
s.t\quad\epsilon_i=y_i-w^Tx_i,\forall i\in[n]
$$

**L2损失函数**>>Ridge Regression

![45](C:\Users\Administrator\Pictures\Saved Pictures\45.jpg)

**L1损失函数**>>Median Regression

![46](C:\Users\Administrator\Pictures\Saved Pictures\46.jpg)

**\epsilon-insensitive损失函数**>>支持向量回归

![47](C:\Users\Administrator\Pictures\Saved Pictures\47.jpg)

> **性质**
>
> 鲁棒性（健壮性好）
>
> 对异常值（Outlier)不敏感
>
> 可以用与SVM同样的优化算法进行优化（多一倍的变量）

## 5.实战之特征工程和模型调优

![48](C:\Users\Administrator\Pictures\Saved Pictures\48.jpg)

### 5.1机器学习中的特征工程

机器学习中**最重要**的环节，时间占比超过50%

#### 5.1.1特征工程与意义

特征>>数据中抽取出来的对**结果预测有用的信息**>>表达

特征工程是使用专业背景知识和技巧处理数据，使得特征能在 机器学习算法上发挥更好的作用的过程

意义

- 更好的特征意味着更强的灵活度
- 更好的特征意味着只需用简单模型
- 更好的特征意味着更好的结果

实际上

- 跑数据，各种map-reduce,hive SQL,数据仓库搬砖
- 数据清洗，数据清洗，数据清洗。。。
- 分析业务，分析case，找特征，找特征。。。
- 简单可解释性好的模型为主，甚至一招LR打天下。。。

![49](C:\Users\Administrator\Pictures\Saved Pictures\49.jpg)

应用

某搜索引擎厂，广告部门点击率预估问题

- 2周内可以完成一次特征迭代，有效的情况下AUC特征约1-2%
- 一个月左右完成模型的小优化，很多时候AUC提升只有千分之五左右

阿里天池与kaggle比赛

- 大于50%的时间花在分析业务场景，挖掘有效特征上
- 特征有效的情况下，借助于基本模型，轻松进top10%

#### 5.1.2基本数据处理

**数据采集**

- 哪些数据对最后的结果预测有帮助？
- 数据我们能够采集到吗？
- 线上实时计算的时候获取是否快捷？
- 埋点和数据打标存储会有同学配合

**数据清洗**

1. garbage in,garbage out

2. 算法大多数时候就是一个加工机器，枝与最后的产品（成品）如何，取决于原材料的好坏

3. 实际这个过程会花掉一大部分时间，而且它会使得你对于业务的理解非常透彻

4. 数据清洗做的事情=>去掉脏数据

   > 单维度考量
   >
   > 组合或统计属性判定
   >
   > 统计方法
   >
   > 补齐可对应的缺省值

**数据采样**

分类问题中，很多情况下，正负样本是不均衡的

大多数模型对正负样本是比较**敏感**的（比如LR）

随机采样和分层抽样

> 处理办法
>
> - 正样本>>负样本，且量都挺大>>下采样
> - 正样本>>负有昂白，量不大
> - 采集更多的数据
> - 过采样/oversampling(比如图像识别中的镜像和旋转)
> - 修改损失函数/loss function

#### 5.1.3常见特征工程

**数值型**

幅度调整/归一化/标准化

Scaling/Normalization/Standardization

![50](C:\Users\Administrator\Pictures\Saved Pictures\50.jpg)

**统计值**

max,min,mean,std

![51](C:\Users\Administrator\Pictures\Saved Pictures\51.jpg)

**离散化**

分桶/分箱（等距划分/等频划分）

![52](C:\Users\Administrator\Pictures\Saved Pictures\52.jpg)

高次与四则运算特征

**类别型**

**one-hot编码/哑变量**

![53](C:\Users\Administrator\Pictures\Saved Pictures\53.jpg)

**Hash与聚类处理**

![54](C:\Users\Administrator\Pictures\Saved Pictures\54.jpg)

**统计类别比例，转成数值型**

![55](C:\Users\Administrator\Pictures\Saved Pictures\55.jpg)

**时间型**

既可以看作连续值，也可以看作离散值

连续值

- 持续时间（单页浏览时长）
- 间隔时间（上次购买/点击离现在的时间）

离散值

1. 一天中的哪个时间段
2. 一周中星期几
3. 一年中哪个星期
4. 一年中哪个季度
5. 工作日/周末

**其他类型**

**词袋/bag of words**

**word2vec**

**工具>>google word2vec gensim**

文本数据预处理后，去掉停用词，剩下的次组成的list，在词库中的映射稀疏向量

**文本型**

使用**Tf-idf特征**

> TF-IDF是一种统计方法，用以评估一字词对于一个文件集或一个语料库中的其中一份文件的重要程度。字词的重要性随着它在文件中出现的次数成正比增加 ，但同时会随着它在语料库中出现的频率成反比下降
>
> TF>>Term Frequency
>
> - TF(t)=(词t在当前文中出现次数)/（t在全部文档中出现次数）
>
> IDF
>
> - IDF（t)=ln(总文档树)/含t的文档数）
> - TF-IDF权重=TF（t)*IDF(t)

**统计特征**

- **加减平均**
- **分位线**
- **次序型**
- **比例类**

![56](C:\Users\Administrator\Pictures\Saved Pictures\56.jpg)![57](C:\Users\Administrator\Pictures\Saved Pictures\57.jpg)

**简单组合特征>>拼接型**

**模型特征组合**

#### 5.1.4特征选择方法

意义

> 冗余>>部分业主的相关度太高了，消耗计算性能
>
> 噪声>>部分特征是对预测结果有负影响

特征选择 VS 降维

> 前者剔除原本特征里和结果预测关系不大的，后者做降维操作，但是保存大部分信息
>
> SVD或者PCA确实也能解决一定的高维度问题

**过滤式（filter)特征选择**

评估单个特征和结果之间的相关程度，排序留下Top10相关的特征部分

Pearson相关系数，互信息，距离相关度

缺点>>没有考虑到特征之间的关联作用，可能把 有用的关联特征误剔除

```python
X_new = SelectKBest(chi2,k=2).fit_transform(X,y)
X_new.shape
```

**包裹式（Wrapper)特征选择**

把特征选择看作一个特征自己搜索问题，筛选各种特征自子集，用模型评估效果

典型的包裹式算法为“递归特征删除算法”（recursive feature elimination algorithm)

```python
rfe = RFE(Ir,n_feature_to_select=1)
rfe.fit(X,Y)
```

**嵌入式（Embedded)特征**

根据模型来分析特征的重要性（有别于上面分方式，是从生产的模型权重等）

最常见的方式为用正则化方式来做特征选择

举个例子，最早在电商用LR做CTR预估，在3-5亿维的系数特征上用L1正则化的LR模型。剩余2-3千万的feature，意味着其他的feature重要度不够

```python
lsvc = linearSVC(C=0.01,penalty='L1',dual=False).fit(X,y)
model = SelectFromModel(lsvc,prefit=True)
X_new = model.transform(X)
X_new.shape
```

### 5.2机器学习中的特征工程实操篇

```python
#加载工具包 导入数据
import pandas as pd

df_train = pd.read_csv('train.csv')
df_train.info()         #了解数据
df_train.describe()     #数据基本信息
```

基本数据处理

```python
#0缺失值处理
#methon1 fillna填充
df_train['Age'].fillna(value=df_train['Age'].mean())

#methon2 sklearn的Imputer填充
from sklearn.preprocessing import Imputer
imp=Imputer(missing_values='NaN',strategy='mean',axis=0)
age = imp.fit_transform(df_train[['Age']].values)
```

```python
#数值型
#0幅度变换
# 取对数等变换
import numpy as np
log_age = df_train['Age'].apply(lambda x:np.log(x))

# 幅度缩放、归一化等
from sklearn.preprocessing import MinMaxScaler
mm_scaler = MinMaxScaler()
age_trans = mm_scaler.fit_transform(df_train[['Fare']])

from sklearn.preprocessing import StandardScaler
std_scaler = StandardScaler()
age_trans = std_scaler.fit_transform(df_train[['Fare']])

#统计值
# 最大最小值
max_age = df_train['Age'].max()
min_age = df_train['Age'].min()

# 分位数
age_quarter_1 = df_train['Age'].quantile(0.25)
age_quarter_3 = df_train['Age'].quantile(0.75)

#四则运算
df_train.loc[:,'family_size'] = df_train['SibSp']+df_train['Parch']+1
df_train.head()

#高次特征与交叉特征
from sklearn.preprocessing import PolynomialFeatures
poly = PolynomialFeatures(degree=2)
poly_fea = poly.fit_transform(df_train[['SibSp','Fare']])
poly_fea.shape

#离散化
df_train.loc[:,'fare_cut'] = pd.cut(df_train['Fare'],5)
df_train.loc[:,'fare_qcut'] = pd.qcut(df_train['Fare'],5)

#One-Hot encoding/独热向量编码
df_train.info()
embarked_oht = pd.get_dummies(df_train[['Embarked']])
embarked_oht.head()
fare_qcut_oht = pd.get_dummies(df_train[['fare_qcut']])
fare_qcut_oht.head()

#时间型
#日期处理
car_sales = pd.read_csv('car_data.csv')	
car_sales.head()
car_sales.loc[:,'date'] = pd.to_datetime(car_sales['date_t'], format="")
car_sales.head()
car_sales.info()


#取出关键时间信息
# 取出几月份
car_sales.loc[:,'month'] = car_sales['date'].dt.month
# 取出几号
car_sales.loc[:,'dom'] = car_sales['date'].dt.day
# 取出一年当中第几天
car_sales.loc[:,'doy'] = car_sales['date'].dt.dayofyear
# 取出星期几
car_sales.loc[:,'dow'] = car_sales['date'].dt.dayofweek
car_sales.head()
```

文本型

```python
#词袋模型
from sklearn.feature_extraction.text import CountVectorizer
vectorizer = CountVectorizer()
corpus = [
        'This is the first document.',
        'This is the second second document.',
        'And the third one.',
        'Is this the first document?'
        ]
X = vectorizer.fit_transform(corpus)                     vectorizer.get_feature_names()
X.toarray()
```

![58](C:\Users\Administrator\Pictures\Saved Pictures\58.jpg)

```python
#TF-IDF
from sklearn.feature_extraction.text import TfidfVectorizer
tfidf_vectorizer = TfidfVectorizer()
tfidf_X = tfidf_vectorizer.fit_transform(corpus)
tfidf_vectorizer.get_feature_names()
tfidf_X.toarray()
```

![59](C:\Users\Administrator\Pictures\Saved Pictures\59.jpg)

```python
#组合特征
# 借助于条件判断实现
df_train.loc[:,'alone'] = (df_train['SibSp']==0)&(df_train['Parch']==0)
```

```python
#特征选择
#过滤式
from sklearn.datasets import load_iris
from sklearn.feature_selection import SelectKBest

iris = load_iris()
X, y = iris.data, iris.target
X.shape

'''(150,4)'''

X_new = SelectKBest(k=2).fit_transform(X, y)
X_new.shape
```

(150,2)

```python
#包裹式/Wrapper
from sklearn.feature_selection import RFE

from sklearn.ensemble import RandomForestClassifier
rf = RandomForestClassifier()
rfe = RFE(estimator=rf, n_features_to_select=2)

X_rfe = rfe.fit_transform(X,y)
X_rfe.shape
```

(150,2)

```python
#嵌入式/Embedded
from sklearn.feature_selection import SelectFromModel
from sklearn.svm import LinearSVC

lsvc = LinearSVC(C=0.01, penalty="l1", dual=False).fit(X, y)
model = SelectFromModel(lsvc, prefit=True)
X_embed = model.transform(X)
X_embed.shape
```

(150,3)

### 5.3机器学习中的模型调优与融合

#### 5.3.1建模与调参

数据预处理回顾

![60](C:\Users\Administrator\Pictures\Saved Pictures\60.jpg)

**超参数的影响**

正则化强度为例、\lambda必须合适

K折交叉验证数据分布

> 测试集是不能用来训练的，就像是学习的期末考试一样
>
> 训练集中划分K分，其中取其中的一份作为验证集

```python
sklearn.linear_model.LogisticRegression

class sklearn.linear_model.LogosticRegression(penalty='I2',
                                              dual=False,
                                              tol=0.0001,
                                              C=1.0,
                                              fit_intercept=True,
                                              intercept_scaling=1,
                                              class_weight=None,
                                              random_state=None,
                                              solver='liblinear',
                                              max_iter=100,
                                              multi_class='ovr',
                                              verbose=0,
                                              warm_start=False,
                                              n_jobs=1)
```

网格搜索（Grid Search)

网格搜索+交叉验证=候选参数集中最佳参数

不同C和gamma组成参数字典

网格搜索检查验证得分结果

![61](C:\Users\Administrator\Pictures\Saved Pictures\61.jpg)

```python
sklearn.model_selection.GridSearchCV

class sklearn.model_selection.GridSearchCV(estimator,
											param_grid,
											scoring=None,
											fit_params=None,
                                            n_job=1,
                                            lib=True,
                                            cv=None,
                                            verbose=0,
                                            pre_dispatch='2*n_jobs',
                                            error_score='raise',
                                            return_train_score='warn'
                                            )

param_grid = [
    {'C':[1,10,100,1000],'kernel':['linear']},
    {'C':[1,10,100,1000],'gamma':[0.001,0.0001],'kernel':['rbf']}
]
```

#### 5.3.2模型状态与调优

模型状态

过拟合（overfitting/high variance)--“你想太多了”

欠拟合（underfitting/high bias)--“你太天真了”

模型状态验证工具-->学习曲线

![62](C:\Users\Administrator\Pictures\Saved Pictures\62.jpg)

不同模型状态处理

**过拟合**

- 找更多的数据来学习
- 增大正则化系数
- 减少特征个数（不是太推荐）

> 注意>>不要以为降维可以解决过拟合问题

**欠拟合**（模型复杂度不够）

- 找更多的特征
- 减少正则化系数

**线性模型的权重分析**

对线性或者线性kernel的model

- Linear Regression
- Logistic Regression
- LinearSVM

对权重绝对值高/低的特征

- 做更细化的工作
- 特征组合

**Bad-case分析**

分类问题

- 哪些训练样本分错了？
- 我们那部分特征使得它做了这个判定？
- 这些bad case有没有共性
- 是否有还没挖掘的特征

回归问题

- 哪些样本预测距离差距大，为什么？
- .......

#### 5.3.3模型融合

Model ensemble

Ensemble Learning是一组individual learner的组合

- 如果individual learner同质，称为**base learner**
- 如果individual learner异质，称为**component learner**

为什么

- 统计上，假设空间h的平均更接近真实假设f
- 计算上，迭代求解可能找到局部最优解，多个局部最优解的平均更接近全局最优解
- 表现上，真实假设f可能布长已知的假设空间H内平均可能更接近H外的真实假设f

简单来说，我们信奉几条信条

**1.群众的力量是伟大的，集体智慧是惊人的**

- Voting投票器
- Bagging
- 随机森林/Random forest

**2.站在巨人的肩膀上，能看得更远**

- 模型stacking
- blending

**3.一万小时定律**

- Boosting

Voting投票器>>单个模型很难控制过拟合，多数表决

```python
sklearn.ensemble.VotingClassifier

class skearn.ensemble.VotingClassifier(estimators,
                                       voting='hard',
                                       weights=None,
                                       n_jobs=1,
                                       flatten_transform=None
                                       )
```

Bagging>>少给点题，别让它直接把所有题目背下来；多找几个同学做题，综合一下他们的答案

```python
sklearn.ensemble.BaggingClassifier

class sklearn.ensenble.BaggingClassifier(base_estimator=None,
                                        n_estimators=10,
                                        max_sample=1.0,
                                        max_features=1.0,
                                        bootstrap=True,
                                        bootstrap_features=False,
                                        oob_score=False,
                                        warm_start=False,
                                        n_jobs=1,
                                        random_state=None,
                                        verbose=0									
                                        )
```

RF（随机森林）是一种基于树模型的Bagging的优化版本，对每棵树构建的时候，特征也会做采样处理

**Stacking**

用上层estimator结果作为下一层特征，基于上一层模型训练出的结果再次进行训练

**Blending**

弱化版的Stacking，相当于对结果做线性加权

![63](C:\Users\Administrator\Pictures\Saved Pictures\63.jpg)

**Boosting**

- 重复迭代和训练
- 每次分配给分错的样本更高的权重
- 最简单的分类器的叠加

![64](C:\Users\Administrator\Pictures\Saved Pictures\64.jpg)

![65](C:\Users\Administrator\Pictures\Saved Pictures\65.jpg)

回归问题

![66](C:\Users\Administrator\Pictures\Saved Pictures\66.jpg)



**Bagging vs. Boosting**

![67](C:\Users\Administrator\Pictures\Saved Pictures\67.jpg)

#### 5.3.4应用实践

```python
import pandas as pd

#投票器模型融合
from sklearn import model_selection
from sklearn.linear_model import LogisticRegression
from sklearn.tree import DecisionTreeClassifier
from sklearn.svm import SVC
from sklearn.ensemble import VotingClassifier
import warnnings

warnings.filterwarning('ignore')

array =df.valuse

X = array[:,0:8]
Y = array[:,8]
kfold = model_seleaction.KFold(n_splits=5,random_state=2018)

#创建投票器的子模型
estimators = []
model_1 = LogisticRegression()
estimators.append('logistic',model_1)

model_2 = DecisionTreeClassifier()
estimators.append('dt',model_2)

model_3 = SVC()
estimators.append('svm',model_3)

ensemble = VotingClassifier(estimators)
result = model_selection.cross_val_score(ensenble,X,Y,cv=kfold)

print(result.mean())
```

```python
#Bagging
from sklearn.ensemble import BaggingClassifier

dt = DecisionTreeClassifier()
num = 100
kfold = model_selection.KFold(n_splits=5,random_state=2018)
model = BaggingClassifier(base_estimator=dt,n_estimators=num,random_stats=2018)
result = model_selection.cross_val_score(model,X,Y,cv=kfold)

print(result.mean())
```

```python
#RandomForest
from sklearn.ensemble import RandomForestClassifier
num_tree = 100
max_feature_num = 3
kfolf = model_selection.KFlod(n_splits=5,random_state=2018)
model = RandomForestClassifier(n_estimators=num_trees,max_feature=max_feature_num)
result = model_selection.cross_val_score(model,X,Y,cv=kfold)
```

```python
#Adaboost
from sklearn.ensemble import AdaBoostClassifier

num_trees = 25
kfolf = model_selection.KFlod(n_splits=5,random_state=2018)
model = AdaBoostClassifier(n_estimators=num_trees,max_feature=max_feature_num)
result = model_selection.cross_val_score(model,X,Y,cv=kfold)

print(result.mean())
```

## 6.无监督算法

不需要标签，典型应用>>数据压缩，图像分割，数据层次化组织，数据预分类

### 6.1聚类算法

计算机将数据进行抱团操作，或者进行分类

#### 6.1.1聚类算法

**Partitioning Clustering**(平铺聚类)

- K-means/K-medoids
- Gaussian Mixture Model(高斯混合模型)
- Spectral Clustering(谱聚类)
- Centroid-based Clustering...

**Hierarchical Clustering**（层次聚类）

- Single-linkage
- Complete-linkage
- Connectivity-based Clustering...

数据压缩-->对数据按照相似性进行组织，相似的数据在一个类中，距离较远的数据在不同类中，每个类中只存储一个数据

图像分割>>K个颜色重绘图像

数据层次化组织>>二叉树，每个内部节点代表一个Cluster,每个叶节点代表一个数据

#### 6.1.2 K-means/K-medoids算法

**K-means算法**

直观理解

- 寻找k个聚类中心，使得数据到聚类中心的距离最小
- 将每个数据点分配到距离最近的聚类中心

$$
\min_{\mu_1,\dots,\mu_k}\sum_{i=1}^{n}\min_{j=1,\dots,k}||x_i-\mu_j||^2
$$

Voronoi分割，每个分割中心表示一个聚类中心

初始化>>对每个cluster，任意选择空空中一个点作为中心

迭代直至收敛

**最优聚类中心>>所有数据的中心**（算数平均值）

缺点

- 聚类中心μ不一定属于数据集
- K-means由于使用了L2距离函数，容易被outlier和noisy data影响

**K-medoids算法**

- 限制聚类中心必须来自数据点
- 使用L1函数作为距离函数
  - 相似的想法Ridge Regression->Lasso

初始化>>任意选择数据集中一个点作为聚类中心

比较

![90](C:\Users\Administrator\Pictures\Saved Pictures\90.jpg)

#### 6.1.3 K-means的扩展--Soft K-means

K-meas**新视角**
$$
\min_{{\{\mu_j\}},\{r_{ij}\}}\sum_{i=1}^{n}\sum_{j=1}^{k}r_{ij}||x_i-\mu_j||^2
$$

$$
s.t.\quad\forall i\in[n],\sum_{j=1}^{k}r_{ij}=1,r_{ij}\in\{0,1\}
$$

分配步骤>>将每一个数据点分配至距离最近的中心
$$
\forall i\in[n],r_{ij}=1\quad iff\quad j=argmin_j'||x_i-\mu_{j'}|| 
$$
重拟合步骤>>对于每一个cluster，选择离其他点最近的点作为新的中心
$$
\mu_j=\frac{\sum_{i=1}^{n}r_{ij}x_i}{\sum_{i=1}^{n}r_{ij}}
$$
加权版本的质心公式

那么Soft K-means算法
$$
\forall i\in[n],0\le r_{ij}\le1,\sum_{j=1}^{k}r_{ij}=1
$$
**高斯混合模型**

Gaussian Mixture Model for Clustering(a.k.a Soft K-means Clustering)

![91](C:\Users\Administrator\Pictures\Saved Pictures\91.jpg)

对比

![92](C:\Users\Administrator\Pictures\Saved Pictures\92.jpg)

![93](C:\Users\Administrator\Pictures\Saved Pictures\93.jpg)

#### 6.1.4层次聚类

**Single-Linkage算法**

- 构造一棵二叉树
- 二叉树的叶结点代表数据
- 二叉树的每一个内部节点代表一个cluster

初始化>>算法将每个数据看成一个类别

迭代直至**只有一个类**

- 选择距离**最近**的两个类进行合并
- 将**被合并**的两个类从现有类中删除
- 将合并后得到的**新类加入现有类**中

$$
Single-Linkage---d(S_i,S_j)=\min_{x_i\in S_i,x_j\in S_j}||x_i-x_j||
$$

$$
Complete-Linkage---d(S_i,S_j)=\max_{x_i\in S_i,x_j\in S_j}||x_i-x_j||
$$

事件复杂度O(n^3)，可以用优先队列的数据结构对算法加速>>O(n^2logn)

**如何从层次聚类中获得扁平聚类>>在扁平分类树上切一刀就可以**

### 6.2降维与度量学习

**Dimensionality resuction**

#### 6.2.1降维介绍

高维空间向低维空间的转换，有以下应用

- 数据可视化
- 数据压缩
- 数据预处理 

**线性降维**                   

- **主成分分析（PCA）**
- 非负矩阵分解（NMF）
- 线性判别分析（Linear Discriminant Analysis)

**非线性降维**

- **IsoMap**
- Locally Linear Embedding(LLE)
- 自编码器（Auto-encoder）

#### 6.2.2主成分分析PCA

![94](C:\Users\Administrator\Pictures\Saved Pictures\94.jpg)

![95](C:\Users\Administrator\Pictures\Saved Pictures\95.jpg)

PCA可以用一个两层线性神经网络来刻画

![96](C:\Users\Administrator\Pictures\Saved Pictures\96.jpg)

确定投影矩阵W

最小化数据x以及它的的重构向量y之间的距离(**最小化重构误差**)

求数据矩阵X所对应的协方差矩阵（**最大化压缩后数据的协方差**）

并求出特征值以及对应的特征向量

![97](C:\Users\Administrator\Pictures\Saved Pictures\97.jpg)

#### 6.2.3 IsoMap算法

IsoMap是非线性降维算法，由MIT Tenebaum教授等人于2000年提出

> A Global Geometric Framework for Nonlinear Dimensionality Reduction,Science 290,(2000),2319-2323

![98](C:\Users\Administrator\Pictures\Saved Pictures\98.jpg)

主要想法>>用**局部的欧式距离来近似局部测地距离**

目标>> 两个点之间的测地距离近似等于降维之后的直线距离

![99](C:\Users\Administrator\Pictures\Saved Pictures\99.jpg)

本质问题>>给定一个距离矩阵D，Dij代表第i个和第j个数据点之间的距离，求一个低维嵌入方法V，使得V_i和V_j之间的直线距离近似Dij

#### 6.2.4 Multidimendional Scaling(MDS)

问题>>

给定一个距离矩阵D，Dij代表第i个和第j个数据点之间的距离,求一个低纬嵌入方法V，使得Vi和Vj之间的直线距离近似Dij
$$
\min_{V_1,\dots ,V_j}\sum_{i<j}(||V_i-V_j||_2-D_{ij})^2
$$

> 注意
>
> 上述问题的最优解不唯一，对矩阵V的平移、旋转、镜面变换等正交变换不改变||Vi-Vj||2
>
> MDS通常通过数值优化方法来进行求解，包括
>
> - 一阶方法，基于梯度下降的方法
> - 二阶方法，拟牛顿法

![100](C:\Users\Administrator\Pictures\Saved Pictures\100.jpg)

![101](C:\Users\Administrator\Pictures\Saved Pictures\101.jpg)

![102](C:\Users\Administrator\Pictures\Saved Pictures\102.jpg)

### 6.3关联规则挖掘

Association Rule

#### 6.3.1关联规则挖掘概述

数据挖掘的一个子领域

- If/then语句
- X->Y
- Support,Confidence,Lift

典型应用

- 分析以及预测网络用户行为
- 银行投资分析
- 无信息
- 信用卡分析

**关联规则**

![103](C:\Users\Administrator\Pictures\Saved Pictures\103.jpg)

> 总共可能有多少个不同的关联规则
>
> **(2^n-1)^2**

![105](C:\Users\Administrator\Pictures\Saved Pictures\104.jpg)

![105](C:\Users\Administrator\Pictures\Saved Pictures\105.jpg)

![105](C:\Users\Administrator\Pictures\Saved Pictures\106.jpg)

![105](C:\Users\Administrator\Pictures\Saved Pictures\107.jpg)

#### 6.3.2购物篮分析与频繁度挖掘

![108](C:\Users\Administrator\Pictures\Saved Pictures\108.jpg)

如果有N个物品，列表法复杂的**O(m*2^n)**

#### 6.3.3 Apriori算法

![109](C:\Users\Administrator\Pictures\Saved Pictures\109.jpg)

![110](C:\Users\Administrator\Pictures\Saved Pictures\110.jpg)

![111](C:\Users\Administrator\Pictures\Saved Pictures\111.jpg)

![112](C:\Users\Administrator\Pictures\Saved Pictures\112.jpg)

![113](C:\Users\Administrator\Pictures\Saved Pictures\113.jpg)

![114](C:\Users\Administrator\Pictures\Saved Pictures\114.jpg)

#### 6.3.4 FP-Growth算法

![115](C:\Users\Administrator\Pictures\Saved Pictures\115.jpg)

![116](C:\Users\Administrator\Pictures\Saved Pictures\116.jpg)

![116](C:\Users\Administrator\Pictures\Saved Pictures\117.jpg)

![116](C:\Users\Administrator\Pictures\Saved Pictures\118.jpg)

![116](C:\Users\Administrator\Pictures\Saved Pictures\119.jpg)

![116](C:\Users\Administrator\Pictures\Saved Pictures\120.jpg)



![116](C:\Users\Administrator\Pictures\Saved Pictures\121.jpg)



![116](C:\Users\Administrator\Pictures\Saved Pictures\122.jpg)

![116](C:\Users\Administrator\Pictures\Saved Pictures\123.jpg)

![116](C:\Users\Administrator\Pictures\Saved Pictures\125.jpg)

![126](C:\Users\Administrator\Pictures\Saved Pictures\126.jpg)

![126](C:\Users\Administrator\Pictures\Saved Pictures\127.jpg)

![126](C:\Users\Administrator\Pictures\Saved Pictures\128.jpg)

![126](C:\Users\Administrator\Pictures\Saved Pictures\129.jpg)

## 7.概率机器学习模型初步与进阶

以**概率**的思想来解决问题

### 7.1贝叶斯网络

核心是**贝叶斯**方程

#### 7.1.1朴素贝叶斯

贝叶斯方程
$$
P(B|A)=\frac{P(A|B)P(B)}{P(A)}
$$
朴素贝叶斯的定义

1. 设x={a1,a2,...am}为一个待分类项，a为x的一个特征属性
2. 有类别集合C={y1,y2,...,yn}
3. 计算 P(y1|x),P(y2|x),...,P(yn|x)
4. 取最大的那一个P

全概率公式
$$
P（y_i|x)=P(y_j)*\prod_{j}P(x_j|y_j)
$$
通俗讲，贝叶斯就是寻找拥有这些特征的最有可能的标签

#### 7.1.2贝叶斯网络与有向分离

贝叶斯网络

Bayesian Network，又称信念网络（Belief Network)，或有向无环图模型（directed acyclic graphical model)是一种**概率图**模型。它是一种模拟人类推理过程中因果关系的不确定性处理模型，其**网络拓扑结果是一个有向无环图**（DAG）

若两个节点间以一个单箭头连接在一起，表示其中一个节点是“因（Parents)”,另一个是“果（children）”,两节点就会产生一个条件概率值

连接两个节点的箭头代表此两个随机变量是具有**因果关系**，或非条件独立

![68](C:\Users\Administrator\Pictures\Saved Pictures\68.jpg)

因为a导致b,a和b导致c,所以有
$$
P（a,b,c)=P(c|a,b)*P(b|a)P(a)
$$
有向分离

**有向分离**（D-Separation)是一种用来判断变量是否田间独立的图形化方法，换言之，对于一个DAG（有向无环图）E，D-Separation方法可以快速的判断出两个节点之间是否田间独立的。

我们根据贝叶斯网络的三种形式一一讲解

形式一>>head-to-head

![69](C:\Users\Administrator\Pictures\Saved Pictures\69.jpg)

形式二>>tail-to-tail

![70](C:\Users\Administrator\Pictures\Saved Pictures\70.jpg)

形式三>>head-to tail

![71](C:\Users\Administrator\Pictures\Saved Pictures\71.jpg)

#### 7.1.3马尔科夫模型

**马尔科夫链**-指数学中具有马尔科夫性质的**离散事件随机过程**，在给定当前知识或信息的情况下，过去（即当前以前的历史状态）对于预测将来（即当前以后的未来状态)是无关的

意义>>每个状态的转移只依赖于之前的n个状态，这个过程被称为1个n阶模型，其中n是影响转移状态的数目。最简单的马尔科夫过程就是一阶过程，用数字表达式表示就是下面的样子
$$
P（X_{n+1}=x|X_1=x_1,X_2=x_2,\dots,X_n=x_n)=P(X_{n+1}=x|X_n=x_n)
$$
示例

假设天气阴晴表**转移矩阵**
$$
P=\begin{bmatrix}
0.9&0.1\\
0.5&0.5\\
\end{bmatrix}
$$
从今天（晴或者阴）开始，在遥远的未来的某天，阴晴的概率分布是什么
$$
q=\lim_{n\rightarrow+\infty}P^n=(0.833\quad0.167)
$$

$$
P^{\infty}=\begin{bmatrix}
0.833&0.167\\
0.833&0.167\\
\end{bmatrix}
$$

$$
(1\quad0)P^{\infty}=(0\quad1)P^{\infty}
$$

不管今天阴晴，很多天之后的阴晴分布收敛到一个固定分布，这个固定分布叫**稳态分布**

很久的未来，每一天天气都是q=(0.833  0.167)的一个样本点

至此，马尔科夫过程定义分为以下三个部分

1. 状态>>晴天、阴天
2. 初始向量>>定义系统在时间为0的时候的状态的概率
3. 状态转移矩阵>>每种天气转换的概率，所有的能被这样描述的系统都是一个马尔科夫过程

#### 7.1.4实战案例

朴素贝叶斯算法的python实现

```python
#导入模块
import pandaa as pd
import numpy as np

# 新建一个DataFrame
data = pd.DataFrame()

# 把Y定义好
data['Gender'] = ['male','male','male','male','female','female','female','female']

# 并给定他们的属性
data['Height'] = [6,5.92,5.58,5.92,5,5.5,5.42,5.75]
data['Weight'] = [180,190,170,165,100,150,130,150]
data['Foot_Size'] = [12,11,12,10,6,8,7,9]

#创建一个要预测的数据
person = pd.DataFrame()

# Create some feature values for this single row
person['Height'] = [6]
person['Weight'] = [130]
person['Foot_Size'] = [8]

#计数
# 男人的总数
n_male = data['Gender'][data['Gender'] == 'male'].count()

# 女人的总数
n_female = data['Gender'][data['Gender'] == 'female'].count()

# 全部的人数
total_ppl = data['Gender'].count()

#计算两个最简单的概率
P_male = n_male/total_ppl
P_female = n_female/total_ppl

from IPython.display import Image

Image(filename='NB_calculation.png') 
```

![48](C:\Users\Administrator\Pictures\Saved Pictures\48.png)

```python
data_means = data.groupby('Gender').mean()

data_variance = data.groupby('Gender').var()

# 计算各种统计值
# 男人的Means
male_height_mean = data_means['Height'][data_variance.index == 'male'].values[0]
male_weight_mean = data_means['Weight'][data_variance.index == 'male'].values[0]
male_footsize_mean = data_means['Foot_Size'][data_variance.index == 'male'].values[0]

# 男人的Variance
male_height_variance = data_variance['Height'][data_variance.index == 'male'].values[0]
male_weight_variance = data_variance['Weight'][data_variance.index == 'male'].values[0]
male_footsize_variance = data_variance['Foot_Size'][data_variance.index == 'male'].values[0]

# 女人的Means
female_height_mean = data_means['Height'][data_variance.index == 'female'].values[0]
female_weight_mean = data_means['Weight'][data_variance.index == 'female'].values[0]
female_footsize_mean = data_means['Foot_Size'][data_variance.index == 'female'].values[0]

# 女人的Variance
female_height_variance = data_variance['Height'][data_variance.index == 'female'].values[0]
female_weight_variance = data_variance['Weight'][data_variance.index == 'female'].values[0]
female_footsize_variance = data_variance['Foot_Size'][data_variance.index == 'female'].values[0]
```

```python
#定义P（x|y)的概率
def p_x_given_y(x, mean_y, variance_y):

    p = 1/(np.sqrt(2*np.pi*variance_y)) * np.exp((-(x-mean_y)**2)/(2*variance_y))

    return p
```

```python
# 假设测试数据是男人概率是
P_male * \
p_x_given_y(person['Height'][0], male_height_mean, male_height_variance) * \
p_x_given_y(person['Weight'][0], male_weight_mean, male_weight_variance) * \
p_x_given_y(person['Foot_Size'][0], male_footsize_mean, male_footsize_variance)

'''6.1970718438780782e-09'''
```

```python
# 假设测试数据是女人，概率是：
P_female * \
p_x_given_y(person['Height'][0], female_height_mean, female_height_variance) * \
p_x_given_y(person['Weight'][0], female_weight_mean, female_weight_variance) * \
p_x_given_y(person['Foot_Size'][0], female_footsize_mean, female_footsize_variance)

'''0.00053779091836300176'''
# 比较一下两者，知道该选谁~
```

### 7.2隐马科夫链模型HMM

Hidden Markov Model

#### 7.2.1隐马科夫链

马科夫链的缺陷

前后关系的缺失，带来了信息的缺失

比如我们的股市，如果只是观测市场，我们只能知道当天的价格、成交量等信息，但是我们并不知道当前股市处于什么样的状态（牛市、熊市、震荡、反弹等等），在这种情况下我们有两个状态集合，一个可以观察到的状态集合（股市价格成交量状态等）和一个隐藏的状态集合（股市状况）



我们希望能找到一个算法可以根据股市价格成交量状况和马尔科夫假设来预测股市的状况。在上面的这些情况下，可以观察到的状态序列和隐藏的状态序列是概率相关的。

于是我们可以将这种类型的过程建模为有一个**隐藏的马尔科夫过程**和 一个与这个隐藏马尔科夫过程**概率相关的并且可以观察到的状态集合**，就是隐马科夫模型。

隐马尔科夫模型是一种统计模型（类似于EM算法），用来描述一个含有隐含未知参数的马尔科夫过程。其难点是从可观察的参数中确定该过程的隐含参数，然后利用这些参数来做进一步的分析。

以掷色子为例

![74](C:\Users\Administrator\Pictures\Saved Pictures\74.jpg)

![72](C:\Users\Administrator\Pictures\Saved Pictures\72.jpg)

转移示意图

![73](C:\Users\Administrator\Pictures\Saved Pictures\73.jpg)

隐马尔科夫链三大问题

1. 知道骰子有几种（隐含状态数量），每种骰子是什么（转换概率），根据掷骰子掷出的结果（可见状态链），我想知道每次掷出的是哪种骰子（隐含状态链）
2. 知道骰子有几种（隐含状态数量），每种骰子是什么（转换概率），根据掷骰子掷出的结果（可见状态链），想知道掷出这个结果的概率
3. 知道骰子有几种（隐含状态数量），不知道每种骰子是什么（转换概率），观测到很多次掷骰子的结果（可见状态链），想反推出每种骰子是什么（转换概率）> >EM模型

对应地

1. **Evaluation验证**>>给定观测序列和模型参数，计算出具体的一个概率值                                                                                                                                                                                                                                                                                                                            
2. **Recognition识别**>>给定观测序列和模型参数，推算出属于哪一个隐含状态
3. **Trainning训练**>>只给定观测序列，反推出模型和下一次的概率值

初始概率分布称为π

状态转移矩阵称为A

观测量的概率分布称为B（喷射层）

#### 7.2.2隐马科夫解法

**对于问题一**

**遍历算法**/向前算法/向后算法

穷举算法--全概率分布
$$
P（O|Q,\lambda)=\prod_{t=1}^{T}P(O_t|q_t,\lambda)=\prod_{t=1}^{T}b_{q_t}o_t
$$

$$
P(Q|\lambda)=P(q_1)\prod_{t=2}^{T}P(q_t|q_{t-1})=\pi_{q_1}\prod_{t=2}^{T}\part q_{t-1}q_t
$$

复杂度O（2TN^T)

遍历算法/**向前算法**/向后算法

定义一个α用来表示时间t之前的状态，然后用每个状态分别计算概率，最后把概率叠加起来即可
$$
\alpha_j(t)=P(O_1O_2\dots O_t,q_t=S_j|\lambda)
$$
式中
$$
\alpha_j(1)=\pi_jb_jo_1\quad j\in[1,N]
$$

$$
\alpha_j(t+1)=(\sum_{i=1}^{N}\alpha_i(t)\part_{ij})b_jo_{t+1}\quad t\in[1,T-1]
$$

$$
P(O|\lambda)=\sum_{i=1}^{N}P(O,q_T=S_i|\lambda)=\sum_{i=1}^{N}\alpha_i(T)
$$



复杂度O（TN^2）

遍历算法/向前算法/**向后算法**

定义一个反馈变量β，在最后时间t时计算出概率，然后推回到初始状态
$$
\beta_i(t)=P(O_{t+1}O_{t+2}\dots O_T|q_t=Si,\lambda)
$$
式中
$$
\beta_i(T)=1\quad1\in[1,N]
$$

$$
\beta_i(t-1)=\sum_{j=1}^{N}a_{ij}b_jo_t\beta_j(t)\quad t\in[2,T]
$$

复杂度O（TN^2）

**对于问题二**

Viterbi算法（最优路径算法）

找到最好的single sequence，也就是计算P(Q|O,λ）最大

定义δ为
$$
\delta_j(t)\max_{q_1,q_2,\dots,q_{t-1}}P（q_1q_2,\dots q_t=j,O_1O_2\dots O_t|\lambda)
$$
式中
$$
\delta_j(t)=\pi_jb_jo_1\quad j\in[1,N]
$$

$$
\delta_j(t+1)=(\max_i\delta_i(t)a_{ij})b_jo_{t+1}\quad t\in[1,T-1]
$$

**对于问题三**

Baum-Welch算法

与EM算法类似

![75](C:\Users\Administrator\Pictures\Saved Pictures\75.jpg)

![76](C:\Users\Administrator\Pictures\Saved Pictures\76.jpg)

![77](C:\Users\Administrator\Pictures\Saved Pictures\77.jpg)

#### 7.2.3隐马科夫应用

**词性标注**

自动对一句话中的词进行POS（Part of Speech）

中文比英文多了一个分词操作

e.g.     the/DET cat/N sat/V on/P the/DET mat/N ./.

为什么

- 为句法分析parsing做预处理
- 用一个有效的信息来强化语料
- 在一个陌生的语料环境中去猜测一个词的意思

![78](C:\Users\Administrator\Pictures\Saved Pictures\78.jpg)

![79](C:\Users\Administrator\Pictures\Saved Pictures\79.jpg)

![80](C:\Users\Administrator\Pictures\Saved Pictures\80.jpg)

![81](C:\Users\Administrator\Pictures\Saved Pictures\81.jpg)

![82](C:\Users\Administrator\Pictures\Saved Pictures\82.jpg)

![83](C:\Users\Administrator\Pictures\Saved Pictures\83.jpg)

![84](C:\Users\Administrator\Pictures\Saved Pictures\84.jpg)

使用HMM进行词性标注

用NLTK自带的Brown词库进行学习

```python
import nltk
import sys
from nltk.corpus import brown

# 预处理词库
#给词们加上开始和结束符号
#用（START,START）(END,END)来表示
brown_tag_word = []
for sent in brown.tagged.sents():
    #先加开头
    brown_tags_words.append(("START","START"))
    #为了省事儿，我们把tag都省略成前两个字母
    brown_tags_words.extend([(tag[:2],word) for (word,tag) in sent])
    #加个结尾
    brown_tags_words.append("END","END")
    
#词统计
#Conditional frequency distribution
cfd_tagwords = nltk.ConditionalFreqDist(brown_tags_words)
#conditional probability distribution
cpd_tagwords = nltk.ConditionalProDist(cfd_tagwords,nltk.MLEProbDist)

# 计算隐层的马可夫链
#取出所有的tag
brown_tags = [tag for (tag,word) in brown_tags_words]

#count(t_i-1,t_i)
#biggram的意思是，前后两个一组，连在一起
cfd_tags = nltk.ConditionalFreqDist(nltk.bigram(brown_tags))
#P(ti|t{i-1})
cpd_tags = nltk.ConditionalProDist(cfd_tags,nltk.MLEProDist)

#一些有趣的结果
#e.g.I want to race [pp vb to vb]
#P(START)*P(PP|START)*P(I|PP)*P(VB|PP)*P(want|VB)*P(TO|VB)*P(to|TO)*P(VB|TO)*P(race|VB)*P(END|VB)
prob_tagsequence = cpd_tags["START"].prob("PP")*cpd_tagwords["PP"].prob('I')*cpd_tag["PP"].prob("VB")*cpd_tagwords["VB"].prob('want')*cpd_tag["VB"].prob("TO")*cpd_tagwords["TO"].prob('to')*cpd_tag["TO"].prob("VB")*cpd_tagwords["VB"].prob('race')*cpd_tag["VB"].prob("END")

# ViterBi实现
#如果我们手上有一句话，怎么最大最符合的tag是哪组呢
distinct_tags = set(brown_tags)
#然后随便找句话
sentence = ["I","want","to","race"]
sentlen = len(sentence)

#加下了，开始维特比
viterbi = []
#回溯器,把所有tagX前一个Tag记下来
backpointer = []

first_viterbi = {}
first_backpointer = {}
for tag in distinct_tags:
    if tag =='START':continue
    first_viterbi[tag] = cpd_tags["START"].prob(tag)*cpd_tagwords[tag].prob(sentence[0])
    first_backpointer[tag] = "START"
    
print(first_viterbi)
print(first_backpointer)

#保存到Viterbi和Backpointer
viterbi.append(first_viterbi)
backpointer.append(first_backpointer)

#先看一下目前最好的tag是啥
currbest = max(first_viterbi.key(),key = lambda tag:first_viterbi[tag])
print("word","'"+sentence[0]+"'","current best two-tag sequence:",first_backpointer[currbest],currbest)

for wordindex in range(1,len(sentence)):
    this_viterbi = {}
    this_backpointer = {}
    prev_viterbi = viterbi[-1]
	for tag in distinct_tags:
        if tag == "START":continue
        best_previous = max(prev_viterbi.key(),
                            key = lambda prevtag:        prev_viterbi[prevtag]*cpd_tags[prevtag].prob(tag)*cpd_tagwords[tag].prob(sentence[wordindex])
        this_viterbi[tag] = prev_viterbi[best_previous]*cpd_tags[best_previous].prob(tag)*cpd_tagwords[tag].prob(sentence[wordindex])
        this_viterbi[tag] = best_previous
                            
 currbest = max(this_viterbi.key(),key = lambda tag:this_viterbi[tag])
print('WORD',"'"+sentence[wordindex]+"'","current best two-tag sequence:",this_backpointer[currbest],currbest)
               
viterbi.append(this_viterbi)
backpointer.append(this_backpointer)
                            
#最终，回溯所有的回溯点，此时最好的tag就是backpointer里面的current best
current_best_tag = best_previous
for bp in backpointer:
    best_tagsequence.append(bp[current_best_tag])
    current_best_tag = bp[current_best_tag]
```

显示结果

```python
best_tagsequence.rcverse()
print("The sentence was:",end='')
for w in sentence:print(w,end="")
print("\n")
print("The best tag sequence is:",end="")
for t in best_tagsequcence:print(t,end="")
print("\n")
print("The probability of the tag sequecne is:",prob_tagsequence)
```

### 7.3主题模型

把一篇文章按照主题分类，无监督模型

#### 7.3.1主题模型理论

![85](C:\Users\Administrator\Pictures\Saved Pictures\85.jpg)

LDA(Latent Dirichlet Allocation)

是一种无监督的贝叶斯模型

是一种主题模型，它可以将文档集中每篇文档的主题按照概率分布的形式给出。同时它是一种无监督学习算法，在训练时不需要手工标注的训练集，需要的仅仅是文档集以及指定主题的数量k即可，此外LDA另一个优点则是，对于每一个主题均可找出一个词语来描述它

是一种典型的**词袋模型**，即它认为一篇文档是由一组词构成的一个集合，词与词之间没有顺序以及先后的关系。一篇文档可以包含**多个主题**，文档每一个词都由其中一个主题生成

--wikipedia维基百科

- 用概率作为【可信度】
- 每次看到新数据，就更新【可信度】
- 需要一个模型来解释数据的生产

**先验，后验与似然**

后验 	=	 先验	×	似然

一篇文章的每个词，都是以一定概率选择了某个主题，并从这个主题以一定概率选择某个词语而组成的

P（单词|文档）=P（单词|主题）*P(主题|文档)

对于语料库中的每篇文档，LDA等一了如下生成过程（generative process)

- 对每一篇文档，从主题分布中抽取一个主题；
- 从上述被抽到的主题所对应的单词分布抽取一个单词；
- 重复上述过程直至生成一个“符合这个主题的文档”

核心公式
$$
P(w|d)=P(w|t)*P(t|d)
$$
以Topic作为中间层，可以通过当前的θd和φt给出了文档d中出现单词w的概率，其中p(t|d)利用θd计算得到，p(w|t)利用φt计算得到

实际上，利用当前的θd和φt，我们可以为一个文档中的一个单词计算它对应一个Topic时的p(w|d),然后根据这些结果来更新这个词应该对应的topic。然后，如果这个更新改变了这个单词对应的topic，就会反过来影响θd和φt

#### 7.3.2主题模型算法

**Unigram model**
$$
p(w)=\prod_{n=1}^{N}p(w_n)
$$
**Mixture of unigram model**
$$
p(W)=p(z_1)\prod_{n=1}^{N}p(w_n|z_1)+\dots+p(z_k)\prod_{n=1}^{N}p(w_n|z_k)=\sum_{z}p(z)\prod_{n=1}^{N}p(w_n|z)
$$
**PLSA模型**

上面的mix unigram模型中，一篇文章只给了 一个主题，但是现实生活中，一篇文章可能有多个主题，只不过出现的概率不一样，PLSA过程与EM算法类似

![86](C:\Users\Administrator\Pictures\Saved Pictures\86.jpg)

![87](C:\Users\Administrator\Pictures\Saved Pictures\87.jpg)

![88](C:\Users\Administrator\Pictures\Saved Pictures\88.jpg)

**LDA模型**

LDA就是在PLSA的基础上加层贝叶斯框架，即LDA就是PLSA的贝叶斯版本

![89](C:\Users\Administrator\Pictures\Saved Pictures\89.jpg)

PLSA跟LDA的本质区别在于它们去估计未知参数所采用的思想不同，前者用的是频率派思想，后者用的是贝叶斯派思想

#### 7.3.3实战案例

```python
import numpy as np
import pandas as pd
import re

df = pd.read_csv("HillaryEmails.csv")
# 原邮件数据中有很多Nan的值，直接扔了。
df = df[['Id','ExtractedBodyText']].dropna()

def clean_email_text(text):
    text = text.replace('\n'," ") #新行，我们是不需要的
    text = re.sub(r"-", " ", text) #把 "-" 的两个单词，分开。（比如：pre-processing ==> pre processing）
    text = re.sub(r"\d+/\d+/\d+", "", text) #日期，对主体模型没什么意义
    text = re.sub(r"[0-2]?[0-9]:[0-6][0-9]", "", text) #时间，没意义
    text = re.sub(r"[\w]+@[\.\w]+", "", text) #邮件地址，没意义
    text = re.sub(r"/[a-zA-Z]*[:\//\]*[A-Za-z0-9\-_]+\.+[A-Za-z0-9\.\/%&=\?\-_]+/i", "", text) #网址，没意义
    pure_text = ''
    # 以防还有其他特殊字符（数字）等等，我们直接把他们loop一遍，过滤掉
    for letter in text:
        # 只留下字母和空格
        if letter.isalpha() or letter==' ':
            pure_text += letter
    # 再把那些去除特殊字符后落单的单词，直接排除。
    # 我们就只剩下有意义的单词了。
    text = ' '.join(word for word in pure_text.split() if len(word)>1)
    return text

docs = df['ExtractedBodyText']
docs = docs.apply(lambda s: clean_email_text(s))  

doclist = docs.values

from gensim import corpora, models, similarities
import gensim

stoplist = ['very', 'ourselves', 'am', 'doesn', 'through', 'me', 'against', 'up', 'just', 'her', 'ours', 
            'couldn', 'because', 'is', 'isn', 'it', 'only', 'in', 'such', 'too', 'mustn', 'under', 'their', 
            'if', 'to', 'my', 'himself', 'after', 'why', 'while', 'can', 'each', 'itself', 'his', 'all', 'once', 
            'herself', 'more', 'our', 'they', 'hasn', 'on', 'ma', 'them', 'its', 'where', 'did', 'll', 'you', 
            'didn', 'nor', 'as', 'now', 'before', 'those', 'yours', 'from', 'who', 'was', 'm', 'been', 'will', 
            'into', 'same', 'how', 'some', 'of', 'out', 'with', 's', 'being', 't', 'mightn', 'she', 'again', 'be', 
            'by', 'shan', 'have', 'yourselves', 'needn', 'and', 'are', 'o', 'these', 'further', 'most', 'yourself', 
            'having', 'aren', 'here', 'he', 'were', 'but', 'this', 'myself', 'own', 'we', 'so', 'i', 'does', 'both', 
            'when', 'between', 'd', 'had', 'the', 'y', 'has', 'down', 'off', 'than', 'haven', 'whom', 'wouldn', 
            'should', 've', 'over', 'themselves', 'few', 'then', 'hadn', 'what', 'until', 'won', 'no', 'about', 
            'any', 'that', 'for', 'shouldn', 'don', 'do', 'there', 'doing', 'an', 'or', 'ain', 'hers', 'wasn', 
            'weren', 'above', 'a', 'at', 'your', 'theirs', 'below', 'other', 'not', 're', 'him', 'during', 'which']

texts = [[word for word in doc.lower().split() if word not in stoplist] for doc in doclist]

dictionary = corpora.Dictionary(texts)
corpus = [dictionary.doc2bow(text) for text in texts]

lda = gensim.models.ldamodel.LdaModel(corpus=corpus, id2word=dictionary, num_topics=20)
lda.print_topics(num_topics=20, num_words=5)
```

[(0, '0.010*nuclear + 0.006*us + 0.005*american + 0.005*iran + 0.005*also'),
 (1,
  '0.019*labour + 0.016*dialogue + 0.015*doc + 0.015*strategic + 0.014*press'),
 (2, '0.007*mr + 0.007*us + 0.006*would + 0.006*new + 0.004*israel'),
 (3,
  '0.013*israel + 0.011*israeli + 0.011*settlements + 0.007*settlement + 0.006*one'),
 (4, '0.012*us + 0.007*diplomacy + 0.006*state + 0.005*know + 0.005*would'),
 (5, '0.045*call + 0.021*yes + 0.020*thx + 0.010*ops + 0.009*also'),
 (6,
  '0.012*obama + 0.009*percent + 0.008*republican + 0.007*republicans + 0.006*president'),
 (7,
  '0.069*pm + 0.036*office + 0.027*secretarys + 0.021*meeting + 0.020*room'),
 (8, '0.008*would + 0.006*party + 0.006*new + 0.005*said + 0.005*us'),
 (9, '0.007*us + 0.006*would + 0.005*state + 0.005*new + 0.005*netanyahu'),
 (10, '0.007*kurdistan + 0.006*email + 0.006*see + 0.005*us + 0.005*right'),
 (11,
  '0.007*health + 0.007*haitian + 0.006*people + 0.005*would + 0.005*plan'),
 (12, '0.012*see + 0.009*like + 0.009*back + 0.008*im + 0.008*would'),
 (13, '0.009*new + 0.007*fyi + 0.006*draft + 0.006*speech + 0.005*also'),
 (14,
  '0.006*military + 0.006*afghanistan + 0.005*security + 0.005*said + 0.005*government'),
 (15, '0.033*ok + 0.028*pls + 0.023*print + 0.014*call + 0.011*pis'),
 (16,
  '0.015*state + 0.008*sounds + 0.007*us + 0.006*department + 0.005*sorry'),
 (17, '0.053*fyi + 0.012*richards + 0.006*us + 0.005*like + 0.004*defenses'),
 (18, '0.043*pm + 0.021*fw + 0.018*cheryl + 0.015*mills + 0.014*huma'),
 (19, '0.012*clips + 0.007*read + 0.006*tomorrow + 0.006*see + 0.005*send')]

```php
作业
    接下来：
通过

lda.get_document_topics(bow)
或者

lda.get_term_topics(word_id)
两个方法，我们可以把新鲜的文本/单词，分类成20个主题中的一个。

但是注意，我们这里的文本和单词，都必须得经过同样步骤的文本预处理+词袋化，也就是说，变成数字表示每个单词的形式。

To all the little girls watching...never doubt that you are valuable and powerful & deserving of every chance & opportunity in the world.

I was greeted by this heartwarming display on the corner of my street today. Thank you to all of you who did this. Happy Thanksgiving. -H

Hoping everyone has a safe & Happy Thanksgiving today, & quality time with family & friends. -H

Scripture tells us: Let us not grow weary in doing good, for in due season, we shall reap, if we do not lose heart.

Let us have faith in each other. Let us not grow weary. Let us not lose heart. For there are more seasons to come and...more work to do

We have still have not shattered that highest and hardest glass ceiling. But some day, someone will

To Barack and Michelle Obama, our country owes you an enormous debt of gratitude. We thank you for your graceful, determined leadership

Our constitutional democracy demands our participation, not just every four years, but all the time

You represent the best of America, and being your candidate has been one of the greatest honors of my life

Last night I congratulated Donald Trump and offered to work with him on behalf of our country

Already voted? That's great! Now help Hillary win by signing up to make calls now

It's Election Day! Millions of Americans have cast their votes for Hillary—join them and confirm where you vote

We don’t want to shrink the vision of this country. We want to keep expanding it

We have a chance to elect a 45th president who will build on our progress, who will finish the job

I love our country, and I believe in our people, and I will never, ever quit on you. No matter what
```

## 8.电商推荐系统

### 8.1概述

定义->>

一种数学定义

- 设C为全体用户集合
- 设S为全部商品/推荐内容集合
- 设μ是评判把Si推荐给Ci的好坏评价函数
- 推荐是对于c\inC,找到s\in S,使得μ最大,即

$$
\forall c\in C,S_c'=arg \max(\mu(c,s)),s\in S
$$

​	部分场景是Top N推荐

一般情况下,推荐系统的任务是->>

根据用户的

> - 历史行为
> - 社交关系
> - 兴趣点
> - 所处上下文环境

去**判断用户的当前需求/感兴趣的item**

思路

思路变更

> 分类导航页->>雅虎
>
> 搜索引擎->>谷歌,必应,度娘

但是,人总是期望计算机尽量多地服务

> 我们不愿意去想搜索词
>
> 希望系统自动挖掘自己的兴趣点
>
> 希望系统能够我们惊喜

意义

**商家收益**

- Netflix,每年2/3的观看电影from推荐
- Google news,最贱系统能带来额外38%的点击
- 亚马孙,每年35%的销售额都来源于它的推荐
- 头条,板书以上新闻和广告点击来源于推荐
- 京东,一年推荐和广告带来几亿的营收

**对用户而言**

- 找到好玩的东西
- 帮助决策
- 发现新鲜事物
- ...

**对商家而言**

- 提供个性化服务
- 提高信任度和粘度
- 增加营收

### 8.2推荐系统与评估

准确度

打分系统

Top N推荐

设R(u)为根据训练建立的模型在测试集上的推荐

T(u)为测试集上用户的选择

**准确率 vs. 召回率->>**
$$
Precision=\frac{\sum_{u \in U}|R(u) \cap T(U)|}{\sum_{u \in U}|R(u)|}
$$

$$
Recall=\frac{\sum_{u \in U}|R(u) \cap T(U)|}{\sum_{u \in U}|T(u)|}
$$

**覆盖率->>**

表示对物品长尾的发掘能力(推荐系统希望消除马太效应)
$$
Coverage=\frac{|U_{u\in U}R(u)|}{|I|}
$$

$$
H=-\sum_{i=1}^{n}p(i)logp(i)
$$

**多样性->>**

优秀的推荐系统能保证推荐结果列表中物品的丰富性(两两之间的差异性)

设s(i,j)表示物品i和j之间的相似度,多样性表示如下
$$
Diversity(R(u))=1-\frac{\sum_{i,j\in R(u),i\neq j}s(i,j)}{\frac{1}{2}|R(u)|(|R(u)|-1)}
$$

$$
Diversity=\frac{1}{U}\sum_{u\in U}Diversity(R(u))
$$

**新颖度->>**

商品给用户的新鲜感(推荐他们不知道的商品)

**惊喜度->>**

推荐和用户历史兴趣不相似,却满意的

**信任度->>**

提供可靠的推荐理由

**实时性->>**

实时更新程度

### 8.3基于内容的推荐系统

基于用户喜欢的物品的属性/内容进行推荐

需要分析内容,无需考虑用户与用户之间的关联

通常使用在文本相关产品上进行推荐

物品通过内容(比如关键词)关联->>

- 电影题材->>爱情/探险/动作/喜剧/悬疑
- 标志特征->>黄晓明/王宝强...
- 年代->>1995,2018...
- 关键词

基于比对物品内容进行推荐

对于每个要推荐的内容,我们需要建立一份资料->>**权重,TF-IDF**

需要对用户也建立一份资料->>**权重向量**

计算匹配度->>**余弦距离公式**

### 8.4协同过滤推荐系统

协同过滤是一种基于"近邻"的推荐算法

根据用户在物品上的行为找到物品或者用户的"近邻"

![](C:\Users\Administrator\Pictures\Saved Pictures\155.jpg)

**基于用户的协同过滤(user-based CF)**

- 基于用户头共同行为的物品,计算用户相似度
- 找到"近邻",在近邻在新物品的评价(打分)加权推荐

![](C:\Users\Administrator\Pictures\Saved Pictures\156.jpg)

**基于物品的协同过滤(item-based CF)**

![](C:\Users\Administrator\Pictures\Saved Pictures\157.jpg)

相似度/距离的定义

- 欧式距离

$$
dist(X,Y)=(\sum_{i=1}^{n}|x_i-y_i|^p)^\frac{1}{q}
$$

- Jaccard相似度
  $$
  J(A,B)=\frac{|A\cap B|}{|A\cup B|}
  $$

- 余弦相似度
  $$
  cos(\theta)=\frac{a^Tb}{|a|\cdot|b|}
  $$

- Pearson相似度
  $$
  \frac{\sum_{i=1}^{n}(X_i-\mu_X)(Y_i-\mu_Y)}{\sqrt{\sum_{i=1}^{n}(X_i-\mu_X)^2}\sqrt{\sum_{i=1}^{n}(Y_i-\mu_Y)^2}}
  $$




![](C:\Users\Administrator\Pictures\Saved Pictures\158.jpg)

![](C:\Users\Administrator\Pictures\Saved Pictures\159.jpg)

![](C:\Users\Administrator\Pictures\Saved Pictures\160.jpg)

**基于用户的协同过滤**

一个用户序列μ,i=1...,n,一个物品序列p,j=1,...,m

nXm得分矩阵v,每个元素V表示用户对物品的打分

计算用户i和用户j之间的相似度/距离
$$
Sim(i,j)=cos(\overrightarrow{i},\overrightarrow{j})=\frac{\overrightarrow{i}*\overrightarrow{j}}{||\overrightarrow{i}||*||\overrightarrow{j}||}
$$
选取Top K推荐或者加权预测得分
$$
r_{xi}=\frac{\sum_{j\in N(i;x)}s_{ij}\cdot r_{xj}}{\sum_{j\in{N(i;x)}}s_{ij}}
$$
![](C:\Users\Administrator\Pictures\Saved Pictures\161.jpg)

![](C:\Users\Administrator\Pictures\Saved Pictures\162.jpg)

协同过滤优缺点

优点

- 基于用户行为,因此对推荐内容无需先验知识
- 只需要用户和商品关联矩阵即可,结构简单
- 在用户行为丰富的情况下,效果好

缺点

- 需要大量的显性/隐形用户行为
- 需要通过完全相同的商品关联,相似的不行
- 假定用户的兴趣完全取决于之前的行为,而和当前上下文环境无关
- 在数据稀疏的情况下受影响,可以考虑二度关联

**关于冷启动问题**

对于新用户

没有历史行为,协同过滤无法计算

- 从推荐热门的商品开始,手机一些反馈信息
- 在用户注册时手机一下信息
- 通过互动游戏等采集一些用户喜好相关信息

对于新商品

- 根据商品的属性,基于内容相似度推荐

### 8.5隐语义模型

我们有用户评分矩阵,其中部分位置是空着的(没打分)

 我们希望尽量正确地填满未打分的项(预测得分)

主要想法是,应该有一些隐藏的因素,影响用户的打分

- 比如电影->>演员\题材\主题\年代...
- 不一定是人直接可理解的隐藏因子
- 找到隐藏因子,可以对user和item进行关联

我们假定->>

- 隐藏因子的个数小于user和item树
- 因为如果每个user都关联大于一个独立的隐藏因子,那就没法做预测了

![](C:\Users\Administrator\Pictures\Saved Pictures\163.jpg)

![](C:\Users\Administrator\Pictures\Saved Pictures\164.jpg)

- 相比之下,CF简单、直接、可解释性强
- 隐语义模型能更好地挖掘用户和物品隐藏关联关系
- 隐语义模型覆盖度更好

![](C:\Users\Administrator\Pictures\Saved Pictures\165.jpg)

![](C:\Users\Administrator\Pictures\Saved Pictures\166.jpg)

![](C:\Users\Administrator\Pictures\Saved Pictures\167.jpg)

隐语义模型进一步优化
$$
e_{ij}^2=(r_{ij}-\sum_{k=1}^{K}p_{ik}q_{kj})^2+\frac{\beta}{2}\sum_{k=1}^{K}(||P||^2+||Q||^2)
$$
![](C:\Users\Administrator\Pictures\Saved Pictures\168.jpg)

![](C:\Users\Administrator\Pictures\Saved Pictures\169.jpg)

![](C:\Users\Administrator\Pictures\Saved Pictures\170.jpg)

![](C:\Users\Administrator\Pictures\Saved Pictures\171.jpg)

### 8.6协同过滤与LFM算法实现

协同过滤推荐

```python
#构造一份打分数据集，可以去movielens下载真实的数据做实验
users = {"小明": {"中国合伙人": 5.0, "太平轮": 3.0, "荒野猎人": 4.5, "老炮儿": 5.0, "我的少女时代": 3.0, "肖洛特烦恼": 4.5, "火星救援": 5.0},
         "小红":{"小时代4": 4.0, "荒野猎人": 3.0, "我的少女时代": 5.0, "肖洛特烦恼": 5.0, "火星救援": 3.0, "后会无期": 3.0},
         "小阳": {"小时代4": 2.0, "中国合伙人": 5.0, "我的少女时代": 3.0, "老炮儿": 5.0, "肖洛特烦恼": 4.5, "速度与激情7": 5.0},
         "小四": {"小时代4": 5.0, "中国合伙人": 3.0, "我的少女时代": 4.0, "匆匆那年": 4.0, "速度与激情7": 3.5, "火星救援": 3.5, "后会无期": 4.5},
         "六爷": {"小时代4": 2.0, "中国合伙人": 4.0, "荒野猎人": 4.5, "老炮儿": 5.0, "我的少女时代": 2.0},
         "小李":  {"荒野猎人": 5.0, "盗梦空间": 5.0, "我的少女时代": 3.0, "速度与激情7": 5.0, "蚁人": 4.5, "老炮儿": 4.0, "后会无期": 3.5},
         "隔壁老王": {"荒野猎人": 5.0, "中国合伙人": 4.0, "我的少女时代": 1.0, "Phoenix": 5.0, "甄嬛传": 4.0, "The Strokes": 5.0},
         "邻村小芳": {"小时代4": 4.0, "我的少女时代": 4.5, "匆匆那年": 4.5, "甄嬛传": 2.5, "The Strokes": 3.0}
        }
        
# 定义距离计算函数
#这是一个纯手写版本的距离计算函数集，但是大家可以在scipy当中找到更便捷的库内置计算函数

from math import sqrt
def euclidean_dis(rating1, rating2):
    """计算2个打分序列间的欧式距离. 输入的rating1和rating2都是打分dict
       格式为{'小时代4': 1.0, '疯狂动物城': 5.0}"""
    distance = 0
    commonRatings = False 
    for key in rating1:
        if key in rating2:
            distance += (rating1[key] - rating2[key])^2
            commonRatings = True
    #两个打分序列之间有公共打分电影
    if commonRatings:
        return distance
    #无公共打分电影
    else:
        return -1


def manhattan_dis(rating1, rating2):
    """计算2个打分序列间的曼哈顿距离. 输入的rating1和rating2都是打分dict
       格式为{'小时代4': 1.0, '疯狂动物城': 5.0}"""
    distance = 0
    commonRatings = False 
    for key in rating1:
        if key in rating2:
            distance += abs(rating1[key] - rating2[key])
            commonRatings = True
    #两个打分序列之间有公共打分电影
    if commonRatings:
        return distance
    #无公共打分电影
    else:
        return -1

def cos_dis(rating1, rating2):
    """计算2个打分序列间的cos距离. 输入的rating1和rating2都是打分dict
       格式为{'小时代4': 1.0, '疯狂动物城': 5.0}"""
    distance = 0
    dot_product_1 = 0
    dot_product_2 = 0
    commonRatings = False
    
    for score in rating1.values():
        dot_product_1 += score^2
    for score in rating2.values():
        dot_product_2 += score^2
        
    for key in rating1:
        if key in rating2:
            distance += rating1[key] * rating2[key]
            commonRatings = True
    #两个打分序列之间有公共打分电影
    if commonRatings:
        return 1-distance/sqrt(dot_product_1*dot_product_2)
    #无公共打分电影
    else:
        return -1

def pearson_dis(rating1, rating2):
    """计算2个打分序列间的pearson距离. 输入的rating1和rating2都是打分dict
       格式为{'小时代4': 1.0, '疯狂动物城': 5.0}"""
    sum_xy = 0
    sum_x = 0
    sum_y = 0
    sum_x2 = 0
    sum_y2 = 0
    n = 0
    for key in rating1:
        if key in rating2:
            n += 1
            x = rating1[key]
            y = rating2[key]
            sum_xy += x * y
            sum_x += x
            sum_y += y
            sum_x2 += pow(x, 2)
            sum_y2 += pow(y, 2)
    # now compute denominator
    denominator = sqrt(sum_x2 - pow(sum_x, 2) / n) * sqrt(sum_y2 - pow(sum_y, 2) / n)
    if denominator == 0:
        return 0
    else:
        return (sum_xy - (sum_x * sum_y) / n) / denominator
```

查找最近邻

```python
def computeNearestNeighbor(username, users):
    """在给定username的情况下，计算其他用户和它的距离并排序"""
    distances = []
    for user in users:
        if user != username:
            #distance = manhattan_dis(users[user], users[username])
            distance = pearson_dis(users[user], users[username])
            distances.append((distance, user))
    # 根据距离排序，距离越近，排得越靠前
    distances.sort()
    return distances

#推荐 nearest/Top K neighbors
def recommend(username, users):
    """对指定的user推荐电影"""
    # 找到最近邻
    nearest = computeNearestNeighbor(username, users)[0][1]

    recommendations = []
    # 找到最近邻看过，但是我们没看过的电影，计算推荐
    neighborRatings = users[nearest]
    userRatings = users[username]
    for artist in neighborRatings:
        if not artist in userRatings:
            recommendations.append((artist, neighborRatings[artist]))
    results = sorted(recommendations, key=lambda artistTuple: artistTuple[1], reverse = True)
    for result in results:
        print result[0], result[1]
        
recommend('六爷',users)
'''
肖洛特烦恼 5.0
后会无期 3.0
火星救援 3.0
'''
```

LFM算法

```python
#  Latent Factor Model
# 这里手写了一个矩阵分解来完成一个LFM模型，矩阵分解的过程和PPT中提到的公式是一致的

import numpy

#手写矩阵分解
#现在有很多很方便对高维矩阵做分解的package，比如libmf, svdfeature等
def matrix_factorization(R, P, Q, K, steps=5000, alpha=0.0002, beta=0.02):
    Q = Q.T
    for step in xrange(steps):
        for i in xrange(len(R)):
            for j in xrange(len(R[i])):
                if R[i][j] > 0:
                    eij = R[i][j] - numpy.dot(P[i,:],Q[:,j])
                    for k in xrange(K):
                        P[i][k] = P[i][k] + alpha * (2 * eij * Q[k][j] - beta * P[i][k])
                        Q[k][j] = Q[k][j] + alpha * (2 * eij * P[i][k] - beta * Q[k][j])
        eR = numpy.dot(P,Q)
        e = 0
        for i in xrange(len(R)):
            for j in xrange(len(R[i])):
                if R[i][j] > 0:
                    e = e + pow(R[i][j] - numpy.dot(P[i,:],Q[:,j]), 2)
                    for k in xrange(K):
                        e = e + (beta/2) * (pow(P[i][k],2) + pow(Q[k][j],2))
        if e < 0.001:
            break
    return P, Q.T


#读取user数据并用张量分解进行打分

R = [
     [5,3,0,1],
     [4,0,3,1],
     [1,1,0,5],
     [1,0,0,4],
     [0,1,5,4],
    ]

R = numpy.array(R)

N = len(R)
M = len(R[0])
K = 2

P = numpy.random.rand(N,K)
Q = numpy.random.rand(M,K)

nP, nQ = matrix_factorization(R, P, Q, K)
nR = numpy.dot(nP, nQ.T)
```

->>>np

array([[ 0.37354361,  2.22462978],
​       [ 0.39373358,  1.77277479],
​       [ 2.23851893,  0.37239595],
​       [ 1.790099  ,  0.37770254],
​       [ 1.81217012,  0.51692472]])

->>>nQ

array([[ 0.08507765,  2.22384553],
​       [ 0.20967412,  1.30417772],
​       [ 2.39991489,  1.15741951],
​       [ 2.20229125,  0.07765447]])

->>>nR

array([[ 5.14097676,  2.65847204,  4.37686383,  1.01929774],
​       [ 3.74778917,  1.93782362,  3.2635803 ,  0.86660675],
​       [ 1.1444558 ,  0.58372427,  3.76229652,  4.95573083],
​       [ 0.94547292,  0.48244748,  3.03458474,  3.96930106],
​       [ 3.13052819,  1.61288469,  4.71770071,  4.10201949]])

->>>R

array([[5, 3, 0, 1],
​       [4, 0, 3, 1],
​       [1, 1, 0, 5],
​       [1, 0, 0, 4],
​       [0, 1, 5, 4]])

## 9.机器学习工具与案例讲解

实战案例>>**Scikit-learn**

### 9.1常用机器学习工具实战

#### 9.1.1本章概述

- Scikit-learn板块
- Scikit-learn解决问题流程
- Kaggle分类与回归案例

#### 9.1.2 Scikit-learn板块

Scikit-learn是常用的python工具库,涵盖大多数机器学习算法的实现

流程>>导航与算法指南>>不同板块,对应的参数API细节(数据预处理,特征抽取,各种模型)

**模型调优与超参数选择**>>**评估方法**

**模型融合与增强**

**模型评估**

![130](C:\Users\Administrator\Pictures\Saved Pictures\130.jpg)

#### 9.1.3 Scikit-learn解决问题流程

一般路径

![131](C:\Users\Administrator\Pictures\Saved Pictures\131.jpg)

![132](C:\Users\Administrator\Pictures\Saved Pictures\132.jpg)

**另一种视图的机器学习路径**

![133](C:\Users\Administrator\Pictures\Saved Pictures\133.jpg)

![134](C:\Users\Administrator\Pictures\Saved Pictures\134.jpg)

**超参数的选择**(国外大神总结)

![135](C:\Users\Administrator\Pictures\Saved Pictures\135.jpg)

上述表格仅供参考,具体问题还是要具体分析

#### 9.1.4Kaggle分类与回归问题案例

AI电力能耗预测大赛线性模型实现

![136](C:\Users\Administrator\Pictures\Saved Pictures\136.jpg)

案例数据来源于江苏镇江扬中市的高新区企业历史近2年的用电量，希望能够根据历史数据去精准预测未来一个月每一天的用电量，这是一个很典型的时序数据回归类问题，我们来看看如何用数据驱动的建模方法去完成这样一个预测

```python
from sklearn import preprocessing

import numpy as np
import pandas as pd

#load data_1
data_1 = pd.read_csv('./zhenjiang_power.csv')

#data outline
data_1.info()
data_1.describe()

'''return the frame and outline of data_1 '''

#load data_2
data_2 = pd.read.csv('./zhengjiang_power_9.csv')
```

```python
# 目标：预测未来一个月每一天整个高新区的用电量
train_df = train_df[['record_date', 'power_consumption']].groupby('record_date').agg('sum')

train_df.head()
```

<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>power_consumption</th>
    </tr>
    <tr>
      <th>record_date</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2015-01-01</th>
      <td>2900575.0</td>
    </tr>
    <tr>
      <th>2015-01-02</th>
      <td>3158211.0</td>
    </tr>
    <tr>
      <th>2015-01-03</th>
      <td>3596487.0</td>
    </tr>
    <tr>
      <th>2015-01-04</th>
      <td>3939672.0</td>
    </tr>
    <tr>
      <th>2015-01-05</th>
      <td>4101790.0</td>
    </tr>
  </tbody>
</table>
</div>

```python
#重置表格头
train_df = train_df.reset_index()
train_df.head()
```

<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>record_date</th>
      <th>power_consumption</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2015-01-01</td>
      <td>2900575.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2015-01-02</td>
      <td>3158211.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2015-01-03</td>
      <td>3596487.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2015-01-04</td>
      <td>3939672.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2015-01-05</td>
      <td>4101790.0</td>
    </tr>
  </tbody>
</table>
</div>

```python
%matplotlib inline
train_df['power_consumption'].plot()

#可以plot图形中的细节和重置表格的标签
%matplotlib inline
train_df[(train_df['record_date']>='2015-09-01')&(train_df['record_date']<='2015-10-31')]['power_consumption'].plot()

%matplotlib inline
tmp_df = train_df[(train_df['record_date']>='2015-09-01')&(train_df['record_date']<='2015-10-31')].copy()
tmp_df = tmp_df.set_index(['record_date'])
tmp_df['power_consumption'].plot()
```

至此,已经完成了对训练数据的整理,现在开始设置测试数据

```Python
#生成一张2016年的10月份用电量的空表
test_df = pd.date_range('2016-10-01', periods=31, freq='D')
test_df = pd.DataFrame(test_df)

#第一列设置为日期
test_df.columns = ['record_date']
#第二列设置为用电量,并初始化为0
test_df.loc[:,'power_consumption'] = 0

#把训练数据和测试数据拼接到一起,做特征工程
total_df = pd.concat([train_df, test_df])
```



```Python
#特征工程
#构造时间特征
total_df.loc[:,'dow'] = total_df['record_date'].apply(lambda x:x.dayofweek)
total_df.loc[:,'dom'] = total_df['record_date'].apply(lambda x:x.day)
total_df.loc[:,'month'] = total_df['record_date'].apply(lambda x:x.month)
total_df.loc[:,'year'] = total_df['record_date'].apply(lambda x:x.year)

#构造周末特征,初始化为0
total_df.loc[:,'weekend'] = 0
total_df.loc[:,'weekend_sat'] = 0
total_df.loc[:,'weekend_sun'] = 0

total_df.loc[(total_df['dow']>4),'weekend'] = 1
total_df.loc[(total_df['dow']==5),'weekend_sat'] = 1
total_df.loc[(total_df['dow']==6),'weekend_sun'] = 1

#添加一个月4周的信息
def week_of_month(day):
    if day in range(1,8):
        return 1
    if day in range(8,15):
        return 2
    if day in range(15,22):
        return 3
    else:
        return 4
total_df.loc[:,'week_of_month'] = total_df['dom'].apply(lambda x:week_of_month(x))

#添加上中下旬
def period_of_month(day):
    if day in range(1,11):
        return 1
    if day in range(11,21):
        return 2
    else:
        return 3
total_df.loc[:,'period_of_month'] = total_df['dom'].apply(lambda x:period_of_month(x))

#添加上下半月信息
def period2_of_month(day):
    if day in range(1,16):
        return 1
    else:
        return 2
total_df.loc[:,'period2_of_month'] = total_df['dom'].apply(lambda x:period2_of_month(x))
```

<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>record_date</th>
      <th>power_consumption</th>
      <th>dow</th>
      <th>dom</th>
      <th>month</th>
      <th>year</th>
      <th>weekend</th>
      <th>weekend_sat</th>
      <th>weekend_sun</th>
      <th>week_of_month</th>
      <th>period_of_month</th>
      <th>period2_of_month</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2015-01-01</td>
      <td>2900575.0</td>
      <td>3</td>
      <td>1</td>
      <td>1</td>
      <td>2015</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2015-01-02</td>
      <td>3158211.0</td>
      <td>4</td>
      <td>2</td>
      <td>1</td>
      <td>2015</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2015-01-03</td>
      <td>3596487.0</td>
      <td>5</td>
      <td>3</td>
      <td>1</td>
      <td>2015</td>
      <td>1</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2015-01-04</td>
      <td>3939672.0</td>
      <td>6</td>
      <td>4</td>
      <td>1</td>
      <td>2015</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2015-01-05</td>
      <td>4101790.0</td>
      <td>0</td>
      <td>5</td>
      <td>1</td>
      <td>2015</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>

```
#添加法定节假日信息
total_df.loc[:,'festival'] = 0

#以中国国庆为例,这个需要做统计
total_df.loc[(total_df.month==10)&(total_df.dom<8), 'festival']=1
```

<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>record_date</th>
      <th>power_consumption</th>
      <th>dow</th>
      <th>dom</th>
      <th>month</th>
      <th>year</th>
      <th>weekend</th>
      <th>weekend_sat</th>
      <th>weekend_sun</th>
      <th>week_of_month</th>
      <th>period_of_month</th>
      <th>period2_of_month</th>
      <th>festival</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2015-01-01</td>
      <td>2900575.0</td>
      <td>3</td>
      <td>1</td>
      <td>1</td>
      <td>2015</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2015-01-02</td>
      <td>3158211.0</td>
      <td>4</td>
      <td>2</td>
      <td>1</td>
      <td>2015</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2015-01-03</td>
      <td>3596487.0</td>
      <td>5</td>
      <td>3</td>
      <td>1</td>
      <td>2015</td>
      <td>1</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2015-01-04</td>
      <td>3939672.0</td>
      <td>6</td>
      <td>4</td>
      <td>1</td>
      <td>2015</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2015-01-05</td>
      <td>4101790.0</td>
      <td>0</td>
      <td>5</td>
      <td>1</td>
      <td>2015</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>

```python
#  独热向量编码
#查看所有的标签
total_df.columns

'''
Index(['record_date', 'power_consumption', 'dow', 'dom', 'month', 'year',
       'weekend', 'weekend_sat', 'weekend_sun', 'week_of_month',
       'period_of_month', 'period2_of_month', 'festival'],
      dtype='object')
'''

var_to_encoding = [u'dow', u'dom', u'month', u'year',u'week_of_month', u'period_of_month',  u'period2_of_month']

#建立一个新的表格,用独热处理后的标签
dummy_df = pd.get_dummies(total_df, columns=var_to_encoding)
```

<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>record_date</th>
      <th>power_consumption</th>
      <th>weekend</th>
      <th>weekend_sat</th>
      <th>weekend_sun</th>
      <th>festival</th>
      <th>dow_0</th>
      <th>dow_1</th>
      <th>dow_2</th>
      <th>dow_3</th>
      <th>...</th>
      <th>year_2016</th>
      <th>week_of_month_1</th>
      <th>week_of_month_2</th>
      <th>week_of_month_3</th>
      <th>week_of_month_4</th>
      <th>period_of_month_1</th>
      <th>period_of_month_2</th>
      <th>period_of_month_3</th>
      <th>period2_of_month_1</th>
      <th>period2_of_month_2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2015-01-01</td>
      <td>2900575.0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>...</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2015-01-02</td>
      <td>3158211.0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2015-01-03</td>
      <td>3596487.0</td>
      <td>1</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2015-01-04</td>
      <td>3939672.0</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2015-01-05</td>
      <td>4101790.0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 67 columns</p>
</div>

```python
#  分离训练集和测试集
train_X = dummy_df[dummy_df.record_date<'2016-10-01']
train_y = dummy_df[dummy_df.record_date<'2016-10-01']['power_consumption']
test_X = dummy_df[dummy_df.record_date>='2016-10-01']

#将训练集中的日期和用电量都丢弃
drop_columns = ['record_date','power_consumption']
train_X = train_X.drop(drop_columns, axis=1)
test_X = test_X.drop(drop_columns, axis=1)

train_X.columns

'''
Index(['weekend', 'weekend_sat', 'weekend_sun', 'festival', 'dow_0', 'dow_1',
       'dow_2', 'dow_3', 'dow_4', 'dow_5', 'dow_6', 'dom_1', 'dom_2', 'dom_3',
       'dom_4', 'dom_5', 'dom_6', 'dom_7', 'dom_8', 'dom_9', 'dom_10',
       'dom_11', 'dom_12', 'dom_13', 'dom_14', 'dom_15', 'dom_16', 'dom_17',
       'dom_18', 'dom_19', 'dom_20', 'dom_21', 'dom_22', 'dom_23', 'dom_24',
       'dom_25', 'dom_26', 'dom_27', 'dom_28', 'dom_29', 'dom_30', 'dom_31',
       'month_1', 'month_2', 'month_3', 'month_4', 'month_5', 'month_6',
       'month_7', 'month_8', 'month_9', 'month_10', 'month_11', 'month_12',
       'year_2015', 'year_2016', 'week_of_month_1', 'week_of_month_2',
       'week_of_month_3', 'week_of_month_4', 'period_of_month_1',
       'period_of_month_2', 'period_of_month_3', 'period2_of_month_1',
       'period2_of_month_2'],
      dtype='object')
'''
```

```python
# 开始建模
from sklearn.linear_model import RidgeCV

linear_reg = RidgeCV(alphas=[0.2,0.5,0.8], cv=5)
linear_reg.fit(train_X,train_y)

'''
RidgeCV(alphas=[0.2, 0.5, 0.8], cv=5, fit_intercept=True, gcv_mode=None,
    normalize=False, scoring=None, store_cv_values=False)
'''
linear_reg.score(train_X, train_y)

'''
0.53740406366344451
'''

#进行结果预测
predictions = linear_reg.predict(test_X)

#保存这个结果到csv文件中
test_df.loc[:,'power_consumption'] = predictions
test_df.to_csv('linear_reg.csv', index=None)
```

树模型解决

```python
#不需要进行独热向量编码

#分离训练集和测试集
train_X = total_df[total_df.record_date<'2016-10-01']
train_y = total_df[total_df.record_date<'2016-10-01']['power_consumption']
test_X = total_df[total_df.record_date>='2016-10-01']

#同样丢掉无关的特征
drop_columns = ['record_date','power_consumption']
train_X = train_X.drop(drop_columns, axis=1)
test_X = test_X.drop(drop_columns, axis=1)

train_X.columns

'''
Index([u'dow', u'dom', u'month', u'year', u'weekend', u'weekend_sat',
       u'weekend_sun', u'week_of_month', u'period_of_month',
       u'period2_of_month', u'festival'],
      dtype='object')
'''

#建立数模型
import sklearn
from sklearn.ensemble import RandomForestRegressor
from sklearn.model_selection import GridSearchCV

#参数指令字典
param_grid = {'n_estimators':[5,10,20,50,100,200],
             'max_depth':[3,5,7],
             'max_features':[0.6,0.7,0.8]}
rf = RandomForestRegressor()

#交叉验证
grid = GridSearchCV(rf, param_grid=param_grid, cv=3, n_jobs=8)
grid.fit(train_X, train_y)

'''
GridSearchCV(cv=3, error_score='raise',
       estimator=RandomForestRegressor(bootstrap=True, criterion='mse', max_depth=None,
           max_features='auto', max_leaf_nodes=None,
           min_impurity_decrease=0.0, min_impurity_split=None,
           min_samples_leaf=1, min_samples_split=2,
           min_weight_fraction_leaf=0.0, n_estimators=10, n_jobs=1,
           oob_score=False, random_state=None, verbose=0, warm_start=False),
       fit_params=None, iid=True, n_jobs=8,
       param_grid={'n_estimators': [5, 10, 20, 50, 100, 200], 'max_features': [0.6, 0.7, 0.8], 'max_depth': [3, 5, 7]},
       pre_dispatch='2*n_jobs', refit=True, return_train_score='warn',
       scoring=None, verbose=0)
'''

#获取最好的参数
grid.best_params_
'''
{'max_depth': 3, 'max_features': 0.8, 'n_estimators': 5}
'''

#应用这个最好的参数
rf_reg = grid.best_estimator_

#特征重要度分析
rf_reg.feature_importances_
'''
array([0.05642289, 0.04012714, 0.68898076, 0.10781648, 0.00488546,
       0.        , 0.04207349, 0.        , 0.        , 0.        ,
       0.0596938 ])
'''

print('特征排序：')
feature_names=[u'dow', u'dom', u'month', u'year', u'weekend', u'weekend_sat',u'weekend_sun', u'week_of_month', u'period_of_month',u'period2_of_month', u'festival']
feature_importances = rf_reg.feature_importances_
indices = np.argsort(feature_importances)[::-1]

for index in indices:
    print("feature %s (%f)" %(feature_names[index], feature_importances[index]))
    
'''
特征排序：
feature month (0.688981)
feature year (0.107816)
feature festival (0.059694)
feature dow (0.056423)
feature weekend_sun (0.042073)
feature dom (0.040127)
feature weekend (0.004885)
feature period2_of_month (0.000000)
feature period_of_month (0.000000)
feature week_of_month (0.000000)
feature weekend_sat (0.000000)
'''

predictions = rf_reg.predict(test_X)
predictions
'''
array([3676626.82941598, 3688647.38712507, 3676626.82941598,
       3676626.82941598, 3676626.82941598, 3676626.82941598,
       3676626.82941598, 3959030.8660525 , 3688647.38712507,
       3959030.8660525 , 3959030.8660525 , 3959030.8660525 ,
       3959030.8660525 , 3959030.8660525 , 3959030.8660525 ,
       3732825.96847705, 3959030.8660525 , 3959030.8660525 ,
       3959030.8660525 , 3959030.8660525 , 3959030.8660525 ,
       3959030.8660525 , 3732825.96847705, 3959030.8660525 ,
       3959030.8660525 , 3959030.8660525 , 3959030.8660525 ,
       3959030.8660525 , 3959030.8660525 , 3732825.96847705,
       3959030.8660525 ])
'''
#保存这个结果
test_df.loc[:,'power_consumption'] = predictions
test_df.to_csv('tree_model_reg.csv', index=None)
```

**用朴素贝叶斯完成语种检测**

```python
in_f = open('data.csv')
lines = in_f.readlines()
in_f.close()
dataset = [(line.strip()[:-3], line.strip()[-2:]) for line in lines]

#用sklearn自带的函数分割训练集与测试集
from sklearn.model_selection import train_test_split
x, y = zip(*dataset)
x_train, x_test, y_train, y_test = train_test_split(x, y, random_state=1)

len(x_train)

'''
6799
'''

'''
模型要有好效果，数据质量要保证
我们用正则表达式，去掉噪声数据
'''
import re

def remove_noise(document):
    noise_pattern = re.compile("|".join(["http\S+", "\@\w+", "\#\w+"]))
    clean_text = re.sub(noise_pattern, "", document)
    return clean_text.strip()

remove_noise("Trump images are now more popular than cat gifs. @trump #trends http://www.trumptrends.html")

'''
'Trump images are now more popular than cat gifs.'
'''

```

文本当中有很多不同粒度的基本单元(字母、字、词、短语)

语种判断：拉丁字母以不同的顺序去组合

对于不同粒度的基本单元去做一个统计：

- 字母粒度：d(0) e(1) r(2) w(3) e(1) ...

词袋模型

我是中国人，我爱我的祖国 => 我 是 中国 人 ，我 爱 我 的 祖国 => (我:3 是:1 中国:1 人:1 爱:1)

词表：4w个词
[0,0,0..0]
[3,1,0,1...]

语言模型 n-gram

李雷喜欢韩梅梅	

[李雷，喜欢，韩梅梅，李雷 喜欢， 喜欢 韩梅梅]

韩梅梅喜欢李雷

[李雷，喜欢，韩梅梅，韩梅梅 喜欢， 喜欢 李雷]

```python
from sklearn.feature_extraction.text import CountVectorizer

vec = CountVectorizer(
    lowercase=True,     # lowercase the text
    analyzer='char_wb', # tokenise by character ngrams
    ngram_range=(1,2),  # use ngrams of size 1 and 2
    max_features=1000,  # keep the most common 1000 ngrams
    preprocessor=remove_noise
)
vec.fit(x_train)

def get_features(x):
    vec.transform(x)
    
sen_vector = vec.transform(['10 der welt sind bei'])
sen_vector

vec.vocabulary_

from sklearn.naive_bayes import MultinomialNB
classifier = MultinomialNB()
classifier.fit(vec.transform(x_train), y_train)

classifier.score(vec.transform(XTest), yTest)

'''
0.9770621967357741
'''
```

能在1500句话上，训练得到准确率97.7%的分类器，效果还是不错的。

如果加大语料，准确率会非常高。

规范化,写成一个类

```python
#规范化,写成一个类

import re

from sklearn.feature_extraction.text import CountVectorizer
from sklearn.model_selection import train_test_split
from sklearn.naive_bayes import MultinomialNB


class LanguageDetector():

    def __init__(self, classifier=MultinomialNB()):
        self.classifier = classifier
        self.vectorizer = CountVectorizer(ngram_range=(1,2), max_features=1000, preprocessor=self._remove_noise)

    def _remove_noise(self, document):
        noise_pattern = re.compile("|".join(["http\S+", "\@\w+", "\#\w+"]))
        clean_text = re.sub(noise_pattern, "", document)
        return clean_text

    def features(self, X):
        return self.vectorizer.transform(X)

    def fit(self, X, y):
        self.vectorizer.fit(X)
        self.classifier.fit(self.features(X), y)

    def predict(self, x):
        return self.classifier.predict(self.features([x]))

    def score(self, X, y):
        return self.classifier.score(self.features(X), y)
    
    
 in_f = open('data.csv')
lines = in_f.readlines()
in_f.close()
dataset = [(line.strip()[:-3], line.strip()[-2:]) for line in lines]
x, y = zip(*dataset)
x_train, x_test, y_train, y_test = train_test_split(x, y, random_state=1)

language_detector = LanguageDetector()
language_detector.fit(x_train, y_train)
print(language_detector.predict('This is an English sentence'))
print(language_detector.score(x_test, y_test))   
```

['en']
0.977062196736

**用机器学习方法完成中文文本分类**

```python
import jieba     #jieba是针对中文分词的库
import pandas as pd
df_technology = pd.read_csv("./data/technology_news.csv", encoding='utf-8')
df_technology = df_technology.dropna()

df_car = pd.read_csv("./data/car_news.csv", encoding='utf-8')
df_car = df_car.dropna()

df_entertainment = pd.read_csv("./data/entertainment_news.csv", encoding='utf-8')
df_entertainment = df_entertainment.dropna()

df_military = pd.read_csv("./data/military_news.csv", encoding='utf-8')
df_military = df_military.dropna()

df_sports = pd.read_csv("./data/sports_news.csv", encoding='utf-8')
df_sports = df_sports.dropna()

technology = df_technology.content.values.tolist()[1000:21000]
car = df_car.content.values.tolist()[1000:21000]
entertainment = df_entertainment.content.values.tolist()[:20000]
military = df_military.content.values.tolist()[:20000]
sports = df_sports.content.values.tolist()[:20000]
```

**分词与中文文本处理**

```python
#加载停用词
stopwords=pd.read_csv("data/stopwords.txt",index_col=False,quoting=3,sep="\t",names=['stopword'], encoding='utf-8')
stopwords=stopwords['stopword'].values

def preprocess_text(content_lines, sentences, category):
    for line in content_lines:
        try:
            segs=jieba.lcut(line)
            segs = filter(lambda x:len(x)>1, segs)
            segs = filter(lambda x:x not in stopwords, segs)
            sentences.append((" ".join(segs), category))
        except Exception,e:
            print line
            continue 

#生成训练数据
sentences = []

preprocess_text(technology, sentences, 'technology')
preprocess_text(car, sentences, 'car')
preprocess_text(entertainment, sentences, 'entertainment')
preprocess_text(military, sentences, 'military')
preprocess_text(sports, sentences, 'sports')

#生成训练集,先打乱顺序
import random
random.shuffle(sentences)


#为了一会儿检测一下咱们的分类器效果怎么样，我们需要一份测试集。
#所以把原数据集分成训练集的测试集，咱们用sklearn自带的分割函数。
from sklearn.model_selection import train_test_split
x, y = zip(*sentences)
x_train, x_test, y_train, y_test = train_test_split(x, y, random_state=1234)
len(x_train)
'''
65696
'''

from sklearn.feature_extraction.text import CountVectorizer

vec = CountVectorizer(
    analyzer='word', # tokenise by character ngrams
    max_features=4000,  # keep the most common 1000 ngrams
)
vec.fit(x_train)

def get_features(x):
    vec.transform(x)

#分类器进行训练    
from sklearn.naive_bayes import MultinomialNB
classifier = MultinomialNB()
classifier.fit(vec.transform(x_train), y_train)

classifier.score(vec.transform(x_test), y_test)

'''
0.83866843234850907
'''
```

我们可以看到在2w多个样本上，我们能在5个类别上达到83的准确率。

有没有办法把准确率提高一些呢？

我们可以把特征做得更棒一点，比如说，我们试试加入抽取2-gram和3-gram的统计特征，比如可以把词库的量放大一点。

```python
from sklearn.feature_extraction.text import CountVectorizer

vec = CountVectorizer(
    analyzer='word', # tokenise by character ngrams
    ngram_range=(1,4),  # use ngrams of size 1、2、3
    max_features=20000,  # keep the most common 1000 ngrams
)
vec.fit(x_train)

def get_features(x):
    vec.transform(x)
    
#分类训练
from sklearn.naive_bayes import MultinomialNB
classifier = MultinomialNB()
classifier.fit(vec.transform(x_train), y_train)
classifier.score(vec.transform(x_test), y_test
'''
0.87830494543129822
'''
                 
#交叉验证
from sklearn.cross_validation import StratifiedKFold
from sklearn.metrics import accuracy_score, precision_score
import numpy as np

def stratifiedkfold_cv(x, y, clf_class, shuffle=True, n_folds=5, **kwargs):
    stratifiedk_fold = StratifiedKFold(y, n_folds=n_folds, shuffle=shuffle)
    y_pred = y[:]
    for train_index, test_index in stratifiedk_fold:
        X_train, X_test = x[train_index], x[test_index]
        y_train = y[train_index]
        clf = clf_class(**kwargs)
        clf.fit(X_train,y_train)
        y_pred[test_index] = clf.predict(X_test)
    return y_pred 

NB = MultinomialNB
print precision_score(y, stratifiedkfold_cv(vec.transform(x),np.array(y),NB), average='macro')
'''
0.88154693235
'''

```

完成一个文本分类器class

```python
import re

from sklearn.feature_extraction.text import CountVectorizer
from sklearn.model_selection import train_test_split
from sklearn.naive_bayes import MultinomialNB

class TextClassifier():

    def __init__(self, classifier=MultinomialNB()):
        self.classifier = classifier
        self.vectorizer = CountVectorizer(analyzer='word', ngram_range=(1,4), max_features=20000)

    def features(self, X):
        return self.vectorizer.transform(X)

    def fit(self, X, y):
        self.vectorizer.fit(X)
        self.classifier.fit(self.features(X), y)

    def predict(self, x):
        return self.classifier.predict(self.features([x]))

    def score(self, X, y):
        return self.classifier.score(self.features(X), y)
                
text_classifier = TextClassifier()
text_classifier.fit(x_train, y_train)
#print(text_classifier.predict('这 是 有史以来 最 大 的 一 次 军舰 演习'))
print(text_classifier.predict('苹果 公司 有 新 的 发布 计划'))
print(text_classifier.score(x_test, y_test))
'''
['technology']
0.878304945431
'''
```

SVM文本分类

```python
from sklearn.svm import SVC
svm = SVC(kernel='linear')
svm.fit(vec.transform(x_train), y_train)
svm.score(vec.transform(x_test), y_test)
```

'''
0.84528973925750039
'''

```python
#试试RBF核
from sklearn.svm import SVC
svm = SVC()
svm.fit(vec.transform(x_train), y_train)
svm.score(vec.transform(x_test), y_test)
```

```python
#TFIDF模型
import re

from sklearn.feature_extraction.text import TfidfVectorizer
from sklearn.model_selection import train_test_split
from sklearn.svm import SVC

class TextClassifier():

    def __init__(self, classifier=SVC(kernel='linear')):
        self.classifier = classifier
        self.vectorizer = TfidfVectorizer(analyzer='word', ngram_range=(1,3), max_features=12000)

    def features(self, X):
        return self.vectorizer.transform(X)

    def fit(self, X, y):
        self.vectorizer.fit(X)
        self.classifier.fit(self.features(X), y)

    def predict(self, x):
        return self.classifier.predict(self.features([x]))

    def score(self, X, y):
        return self.classifier.score(self.features(X), y)
    
text_classifier = TextClassifier()
text_classifier.fit(x_train, y_train)
print(text_classifier.predict('这 是 有史以来 最 大 的 一 次 军舰 演习'))
print(text_classifier.score(x_test, y_test))

```

['military']
0.874788803142

### 9.2机器学习高级工具与建模实战

#### 9.2.1本章概述

**高级工具库**

xgboost/LightGBM

#### 9.2.2集成模型简介

集成模型大家族

1. **随机森林>>并行的树模型集成(投票器),添加采样机制增加随机性,减缓过拟合**
2. **GBDT>>串行的模型集成,利用损失函数的负梯度方向在当前模型的值作为残差的近似值,构建下一棵树减小残差**
3. **Xgboost>>串行的模型集成,对代价函数进行泰勒展开,使用一阶和二阶导数近似,添加正则化项控制过拟合,特征粒度的并行,level-wise树生长模式**
4. **LightGBM>>串行的模型集成,类似Xgboost,基于Histogram的决策树算法,直方图做差加速,支持类别型变量,leaf-wise树生长模式**(微软)

> **随机森林**>><u>sklearn RandomForest</u>
>
> **GBDT**>><u>sklearn GradientBoostingClassifier/Regressor</u>
>
> **Xgboost**>><u>dmlc xgboost</u>
>
> **LightGBM**>><u>Microsoft LightGBM</u>

#### 9.2.3 Xgboost应用要点介绍

可伸缩且灵活的梯度提升

![137](C:\Users\Administrator\Pictures\Saved Pictures\137.jpg)

三类参数

**1.通用参数**

- booster[default=gbtree]>> gbtree和gblinear
- silent[default=0] >>0表示输出信息,1表示安静模式
- nthread >>跑xgboost的线程数,默认是最大线程数
- nun_pbuffer[无需用户手动设定]
- nun_feature[无需用户手动设定]

**2.集成(增强)参数**

- eta[default=0.3,可以视作学习率]>>缺省值为0.3,典型值0.01-0.2,取值范围[0,1]
- grammar[default=0,alias:min_split_loss]>>损失减少的最小值,该值越大,算法越保守,取值范围[0,∞]
- max_depth[default=6]>>设置树的最大深度,取值范围[1,∞]
- min_child_weight[default=1]>>子树观测权重之和的最小值,该值越大,算法越保守,取值范围[0,∞]
- subsample[default=1]>>表示观测的子样本的比率,将其设置为0.5意味着xgboost将随机抽取一半观测用于树的生长,通常取值为0.5-1,取值范围(0,1]
- colsample_bytree[default=1]>>表示用于构造每棵树时随机采样的列数的占比,通常取值0.5-1,取值范围(0,1]
- colsample_bylevel[default=1]>>用来控制树的每一级的每一次分裂,对列数的采样的占比,通常取值0.5-1,取值范围(0,1]
- scale_pos_weight[default]>>这各类别样本十分不平衡时,把这个参数设定为一个正值,可以使算法更快收敛,一个可以考虑的值>>sum(negative cases)/sum(positive cases) see Higgs Kaggle conpetitondemo for example R,py1,py2,py3

**3.任务参数**

objective[default=reg:linear]>>这个参数定义需要被最小化的损失函数,最常用的值有

- "reg:linear"--线性回归
- "reg:logistic"--逻辑回归
- "binary:logistic"--二分类的逻辑回归,返回预测的概率(不是类别)
- "binary:logitraw"--输出归一化前的得分
- "multi:softmax"--设定XGBoost做多分类,需要同时设定num_class的值
- "multi:softprob"--输出维度为ndata*nclass的概率矩阵
- "rank:pairwise"--设定XGBoost去完成排序问题(最小化pairwise loss)

base_score[default=0.5]>>the initial prediction score of all instances,global bias for suffucient number if iterations,changing this value will not have too much effect

eval_metric[默认是根据损失函数/目标函数 自动设定的]

- "rmse">>均方误差
- "mae">>绝对平均误差
- "logloss">>negative log损失
- "error">>二分类的错误率
- "error@t">>通过提供t为阈值(而不是0.5),计算错误率
- "merror">>多分类的错误率,计算公式为#(wrong cases)/#(all cases)
- "mlogloss">>多类log损失
- "auc">>ROC曲线下方的面积
- "ndcg">>Normailized Discounted Cumulative Gain
- "map">>平均准确率
- "ndcg@n","map@n">>n can be assigned as an integer to cut off the top positions in thr lists for evalution
- "ndcg-","map-","ndcg@n","map@n-">>in XGBoost,NDCG and MAP will evaluate the score of a list without any postition samples as 1 . By adding "-" in the evalution metric XGBoost will evaluate these score as 0 to be consistent under some conditionss.training repeatedly

**Xgboost应用模板**

- Libsvm格式数据读取,训练与预测
- 交叉验证
- 预处理+交叉验证
- 自定义损失函数
- Xgboost+sklearn
- 网格搜索+模型存储+early stopping

#### 9.2.4 LightGBM应用要点介绍

![138](C:\Users\Administrator\Pictures\Saved Pictures\138.jpg)

**微软**开源的boosting工具库,具有以下特点

- 更快的训练效率
- 低内存使用
- 更高的准确率
- 支持并行化学习
- 可处理大规模数据

**8类参数**

- 核心参数

- 学习控制参数

- IO参数

- 目标参数

- 度量参数

- 网格参数

- GPU参数

- 模型参数

- > 详细参数见官方网站与课程说明文档
  >
  > http://lightgbm.apachevn.org/cn/latest/Parameters.html

#### 9.2.5Kaggle比赛代码案例

xgboost用法速查表

**1.读取libsvm格式数据并指定参数模型**

```python
#!/usr/bin/python
import numpy as np
import scipy.sparse
import pickle
import xgboost as xgb
```

libsvm格式数据>>超参数设定>>设定watchlist用于查看模型状态>>使用模型预测>>判断准确率>>模型存储

**2.配合pandas DataFrame格式数据建模**

```python
#!/usr/bin/python
import numpy as np
import pandas as pd
import pickle
import xgboost as xgb
from sklearn.model_selection import train_test_split
```

用pd读入数据>>做数据切分(切分为训练集与测试集)>>**转换成Dmatrix格式**>>参数设定>>设定watchlist用于查看模型状态>>使用模型预测>>判断准确率>>模型存储

**3.使用xgboost的sklearn包**

```python
#!/usr/bin/python
import warnings
warnings.filterwarnings("ignore")
import numpy as np
import pandas as pd
import pickle
import xgboost as xgb
from sklearn.model_selection import train_test_split
from sklearn.externals import joblib

#初始化模型
xgb_classifier = xgb.XGBClassifier(n_estimators=20,\
                                   max_depth=4, \
                                   learning_rate=0.1, \
                                   subsample=0.7, \
                                   colsample_bytree=0.7)
```

用pd读入数据>>做数据切分>>取出特征x和目标y的部分>>初始化模型>>拟合模型(fit)>>使用模型预测>>判断准确率>>模型存储

**4.交叉验证**

```python
xgb.cv(param, dtrain, num_round, nfold=5,metrics={'error'}, seed = 0)
```

只用于评估这组超参数

**5.添加预处理的交叉验证**

```python
# 计算正负样本比，调整样本权重
def fpreproc(dtrain, dtest, param):
    label = dtrain.get_label()
    ratio = float(np.sum(label == 0)) / np.sum(label==1)
    param['scale_pos_weight'] = ratio
    return (dtrain, dtest, param)

# 先做预处理，计算样本权重，再做交叉验证
xgb.cv(param, dtrain, num_round, nfold=5,
       metrics={'auc'}, seed = 0, fpreproc = fpreproc)
```

![139](C:\Users\Administrator\Pictures\Saved Pictures\139.jpg)

**6.自定义损失函数与评估准则**

```python
print ('running cross validation, with cutomsized loss function')
# 自定义损失函数，需要提供损失函数的一阶导和二阶导
def logregobj(preds, dtrain):
    labels = dtrain.get_label()
    preds = 1.0 / (1.0 + np.exp(-preds))
    grad = preds - labels
    hess = preds * (1.0-preds)
    return grad, hess

# 自定义评估准则，评估预估值和标准答案之间的差距
def evalerror(preds, dtrain):
    labels = dtrain.get_label()
    return 'error', float(sum(labels != (preds > 0.0))) / len(labels)

watchlist  = [(dtest,'eval'), (dtrain,'train')]
param = {'max_depth':3, 'eta':0.1, 'silent':1}
num_round = 5
# 自定义损失函数训练
bst = xgb.train(param, dtrain, num_round, watchlist, logregobj, evalerror)
# 交叉验证
xgb.cv(param, dtrain, num_round, nfold = 5, seed = 0,
       obj = logregobj, feval=evalerror)
```

running cross validation, with cutomsized loss function
[0]	eval-rmse:0.306901	train-rmse:0.306164	eval-error:0.518312	train-error:0.517887
[1]	eval-rmse:0.179189	train-rmse:0.177278	eval-error:0.518312	train-error:0.517887
[2]	eval-rmse:0.172565	train-rmse:0.171728	eval-error:0.016139	train-error:0.014433
[3]	eval-rmse:0.269612	train-rmse:0.27111	eval-error:0.016139	train-error:0.014433
[4]	eval-rmse:0.396903	train-rmse:0.398256	eval-error:0.016139	train-error:0.014433

![140](C:\Users\Administrator\Pictures\Saved Pictures\140.jpg)

自定义的损失函数必须能够求出一阶导数和二阶导数(海森矩阵)(雅可比矩阵)

**7.只用前n棵数预测**

```python
#!/usr/bin/python
import numpy as np
import pandas as pd
import pickle
import xgboost as xgb
from sklearn.model_selection import train_test_split


# 只用第1颗树预测
ypred1 = bst.predict(xgtest, ntree_limit=1)
# 用前9颗树预测
ypred2 = bst.predict(xgtest, ntree_limit=9)
label = xgtest.get_label()
print ('用前1颗树预测的错误率为 %f' % (np.sum((ypred1>0.5)!=label) /float(len(label))))
print ('用前9颗树预测的错误率为 %f' % (np.sum((ypred2>0.5)!=label) /float(len(label))))

"""
0]	eval-error:0.255208	train-error:0.196181
[1]	eval-error:0.234375	train-error:0.175347
[2]	eval-error:0.25	train-error:0.163194
[3]	eval-error:0.229167	train-error:0.149306
[4]	eval-error:0.213542	train-error:0.154514
[5]	eval-error:0.21875	train-error:0.152778
[6]	eval-error:0.21875	train-error:0.154514
[7]	eval-error:0.213542	train-error:0.138889
[8]	eval-error:0.1875	train-error:0.147569
[9]	eval-error:0.1875	train-error:0.144097
用前1颗树预测的错误率为 0.255208
用前9颗树预测的错误率为 0.187500
"""
```

用pd读入数据>>做数据切分(切分为训练集与测试集)>>**转换成Dmatrix格式**>>参数设定>>设定watchlist用于查看模型状态>>只用第一棵树预测>>用前9棵树预测



**sklearn与Xgboost配合使用**

1.Xgboost建模,sklearn评估

```python
import pickle
import xgboost as xgb

import numpy as np
from sklearn.model_selection import KFold, train_test_split, GridSearchCV
from sklearn.metrics import confusion_matrix, mean_squared_error
from sklearn.datasets import load_iris, load_digits, load_boston

rng = np.random.RandomState(31337)

#二分类：混淆矩阵
print("数字0和1的二分类问题")
digits = load_digits(2)
y = digits['target']
X = digits['data']
kf = KFold(n_splits=2, shuffle=True, random_state=rng)
print("在2折数据上的交叉验证")
for train_index, test_index in kf.split(X):
    xgb_model = xgb.XGBClassifier().fit(X[train_index],y[train_index])
    predictions = xgb_model.predict(X[test_index])
    actuals = y[test_index]
    print("混淆矩阵:")
    print(confusion_matrix(actuals, predictions))

#多分类：混淆矩阵
print("\nIris: 多分类")
iris = load_iris()
y = iris['target']
X = iris['data']
kf = KFold(n_splits=2, shuffle=True, random_state=rng)
print("在2折数据上的交叉验证")
for train_index, test_index in kf.split(X):
    xgb_model = xgb.XGBClassifier().fit(X[train_index],y[train_index])
    predictions = xgb_model.predict(X[test_index])
    actuals = y[test_index]
    print("混淆矩阵:")
    print(confusion_matrix(actuals, predictions))

#回归问题：MSE
print("\n波士顿房价回归预测问题")
boston = load_boston()
y = boston['target']
X = boston['data']
kf = KFold(n_splits=2, shuffle=True, random_state=rng)
print("在2折数据上的交叉验证")
for train_index, test_index in kf.split(X):
    xgb_model = xgb.XGBRegressor().fit(X[train_index],y[train_index])
    predictions = xgb_model.predict(X[test_index])
    actuals = y[test_index]
    print("MSE:",mean_squared_error(actuals, predictions))
```

![141](C:\Users\Administrator\Pictures\Saved Pictures\141.jpg)

**2.网格搜索查找最优超参数**

```python
print("参数最优化：")
y = boston['target']
X = boston['data']
xgb_model = xgb.XGBRegressor()
clf = GridSearchCV(xgb_model,
                   {'max_depth': [2,4,6],
                    'n_estimators': [50,100,200]}, verbose=1)
clf.fit(X,y)
print(clf.best_score_)
print(clf.best_params_)
```

参数最优化：
Fitting 3 folds for each of 9 candidates, totalling 27 fits
0.5984879606490934
{'n_estimators': 100, 'max_depth': 4}

**3.early-stoping早停**

```python
# 在训练集上学习模型，一颗一颗树添加，在验证集上看效果，当验证集效果不再提升，停止树的添加与生长
X = digits['data']
y = digits['target']
X_train, X_val, y_train, y_val = train_test_split(X, y, random_state=0)
clf = xgb.XGBClassifier()
clf.fit(X_train, y_train, early_stopping_rounds=10, eval_metric="auc",
        eval_set=[(X_val, y_val)])
```

0]	validation_0-auc:0.999497
Will train until validation_0-auc hasn't improved in 10 rounds.
[1]	validation_0-auc:0.999497
[2]	validation_0-auc:0.999497
[3]	validation_0-auc:0.999749
[4]	validation_0-auc:0.999749
[5]	validation_0-auc:0.999749
[6]	validation_0-auc:0.999749
[7]	validation_0-auc:0.999749
[8]	validation_0-auc:0.999749
[9]	validation_0-auc:0.999749
[10]	validation_0-auc:1
[11]	validation_0-auc:1
[12]	validation_0-auc:1
[13]	validation_0-auc:1
[14]	validation_0-auc:1
[15]	validation_0-auc:1
[16]	validation_0-auc:1
[17]	validation_0-auc:1
[18]	validation_0-auc:1
[19]	validation_0-auc:1
[20]	validation_0-auc:1
Stopping. Best iteration:
[10]	validation_0-auc:1

XGBClassifier(base_score=0.5, booster='gbtree', colsample_bylevel=1,
​       colsample_bytree=1, gamma=0, learning_rate=0.1, max_delta_step=0,
​       max_depth=3, min_child_weight=1, missing=None, n_estimators=100,
​       n_jobs=1, nthread=None, objective='binary:logistic', random_state=0,
​       reg_alpha=0, reg_lambda=1, scale_pos_weight=1, seed=None,
​       silent=True, subsample=1)

**4.特征重要度**

```python
iris = load_iris()
y = iris['target']
X = iris['data']
xgb_model = xgb.XGBClassifier().fit(X,y)

print('特征排序：')
feature_names=['sepal_length', 'sepal_width', 'petal_length', 'petal_width']
feature_importances = xgb_model.feature_importances_
indices = np.argsort(feature_importances)[::-1]

for index in indices:
    print("特征 %s 重要度为 %f" %(feature_names[index], feature_importances[index]))
```

特征排序：
特征 petal_length 重要度为 0.414795
特征 petal_width 重要度为 0.295905
特征 sepal_length 重要度为 0.177015
特征 sepal_width 重要度为 0.112285

**5并行训练加速**

```python
import os

if __name__ == "__main__":
    try:
        from multiprocessing import set_start_method
    except ImportError:
        raise ImportError("Unable to import multiprocessing.set_start_method."
                          " This example only runs on Python 3.4")
    set_start_method("forkserver")

    import numpy as np
    from sklearn.model_selection import GridSearchCV
    from sklearn.datasets import load_boston
    import xgboost as xgb

    rng = np.random.RandomState(31337)

    print("Parallel Parameter optimization")
    boston = load_boston()

    os.environ["OMP_NUM_THREADS"] = "2"  # or to whatever you want
    y = boston['target']
    X = boston['data']
    xgb_model = xgb.XGBRegressor()
    clf = GridSearchCV(xgb_model, {'max_depth': [2, 4, 6],
                                   'n_estimators': [50, 100, 200]}, verbose=1,
                       				n_jobs=2)
    clf.fit(X, y)
    print(clf.best_score_)
    print(clf.best_params_)
```

**LightGBM用法速查表**

**1.读取csv数据并指定参数建模**

```python
# coding: utf-8
import json
import lightgbm as lgb
import pandas as pd
from sklearn.metrics import mean_squared_error

# 加载数据集合
print('Load data...')
df_train = pd.read_csv('./data/regression.train.txt', header=None, sep='\t')
df_test = pd.read_csv('./data/regression.test.txt', header=None, sep='\t')

# 设定训练集和测试集
y_train = df_train[0].values
y_test = df_test[0].values
X_train = df_train.drop(0, axis=1).values
X_test = df_test.drop(0, axis=1).values

# 构建lgb中的Dataset格式
lgb_train = lgb.Dataset(X_train, y_train)
lgb_eval = lgb.Dataset(X_test, y_test, reference=lgb_train)

# 敲定好一组参数
params = {
    'task': 'train',
    'boosting_type': 'gbdt',
    'objective': 'regression',
    'metric': {'l2', 'auc'},
    'num_leaves': 31,
    'learning_rate': 0.05,
    'feature_fraction': 0.9,
    'bagging_fraction': 0.8,
    'bagging_freq': 5,
    'verbose': 0
}

print('开始训练...')
# 训练
gbm = lgb.train(params,
                lgb_train,
                num_boost_round=20,
                valid_sets=lgb_eval,
                early_stopping_rounds=5)

# 保存模型
print('保存模型...')
# 保存模型到文件中
gbm.save_model('model.txt')

print('开始预测...')
# 预测
y_pred = gbm.predict(X_test, num_iteration=gbm.best_iteration)
# 评估
print('预估结果的rmse为:')
print(mean_squared_error(y_test, y_pred) ** 0.5)
```

加载数据集合>>设定训练集和测试集>>构建lgb中的Dataset格式>>敲定好一组参数>>训练

​	保存模型>>保存这个模型到文件>>预测>>评估

Load data...
开始训练...
[1]	valid_0's l2: 0.24288	valid_0's auc: 0.764496
Training until validation scores don't improve for 5 rounds.
[2]	valid_0's l2: 0.239307	valid_0's auc: 0.766173
[3]	valid_0's l2: 0.235559	valid_0's auc: 0.785547
[4]	valid_0's l2: 0.230771	valid_0's auc: 0.797786
[5]	valid_0's l2: 0.226297	valid_0's auc: 0.805155
[6]	valid_0's l2: 0.223692	valid_0's auc: 0.800979
[7]	valid_0's l2: 0.220941	valid_0's auc: 0.806566
[8]	valid_0's l2: 0.217982	valid_0's auc: 0.808566
[9]	valid_0's l2: 0.215351	valid_0's auc: 0.809041
[10]	valid_0's l2: 0.213064	valid_0's auc: 0.805953
[11]	valid_0's l2: 0.211053	valid_0's auc: 0.804631
[12]	valid_0's l2: 0.209336	valid_0's auc: 0.802922
[13]	valid_0's l2: 0.207492	valid_0's auc: 0.802011
[14]	valid_0's l2: 0.206016	valid_0's auc: 0.80193
Early stopping, best iteration is:
[9]	valid_0's l2: 0.215351	valid_0's auc: 0.809041
保存模型...
开始预测...
预估结果的rmse为:
0.4640593794679212

**2.添加样本权重训练**

```python
# coding: utf-8
import json
import lightgbm as lgb
import pandas as pd
import numpy as np
from sklearn.metrics import mean_squared_error
import warnings
warnings.filterwarnings("ignore")

# 加载数据集
print('加载数据...')
df_train = pd.read_csv('./data/binary.train', header=None, sep='\t')
df_test = pd.read_csv('./data/binary.test', header=None, sep='\t')
W_train = pd.read_csv('./data/binary.train.weight', header=None)[0]
W_test = pd.read_csv('./data/binary.test.weight', header=None)[0]

y_train = df_train[0].values
y_test = df_test[0].values
X_train = df_train.drop(0, axis=1).values
X_test = df_test.drop(0, axis=1).values

num_train, num_feature = X_train.shape

# 加载数据的同时加载权重
lgb_train = lgb.Dataset(X_train, y_train,
                        weight=W_train, free_raw_data=False)
lgb_eval = lgb.Dataset(X_test, y_test, reference=lgb_train,
                       weight=W_test, free_raw_data=False)

# 设定参数
params = {
    'boosting_type': 'gbdt',
    'objective': 'binary',
    'metric': 'binary_logloss',
    'num_leaves': 31,
    'learning_rate': 0.05,
    'feature_fraction': 0.9,
    'bagging_fraction': 0.8,
    'bagging_freq': 5,
    'verbose': 0
}

# 产出特征名称
feature_name = ['feature_' + str(col) for col in range(num_feature)]

print('开始训练...')
gbm = lgb.train(params,
                lgb_train,
                num_boost_round=10,
                valid_sets=lgb_train,  # 评估训练集
                feature_name=feature_name,
                categorical_feature=[21])
```

加载数据...
开始训练...
[1]	training's binary_logloss: 0.68205
[2]	training's binary_logloss: 0.673618
[3]	training's binary_logloss: 0.665891
[4]	training's binary_logloss: 0.656874
[5]	training's binary_logloss: 0.648523
[6]	training's binary_logloss: 0.641874
[7]	training's binary_logloss: 0.636029
[8]	training's binary_logloss: 0.629427
[9]	training's binary_logloss: 0.623354
[10]	training's binary_logloss: 0.617593

**3.模型的载入与预测**

```python
# 查看特征名称
print('完成10轮训练...')
print('第7个特征为:')
print(repr(lgb_train.feature_name[6]))

# 存储模型
gbm.save_model('./model/lgb_model.txt')

# 特征名称
print('特征名称:')
print(gbm.feature_name())

# 特征重要度
print('特征重要度:')
print(list(gbm.feature_importance()))

# 加载模型
print('加载模型用于预测')
bst = lgb.Booster(model_file='./model/lgb_model.txt')
# 预测
y_pred = bst.predict(X_test)
# 在测试集评估效果
print('在测试集上的rmse为:')
print(mean_squared_error(y_test, y_pred) ** 0.5)
```

完成10轮训练...
第7个特征为:
'feature_6'
特征名称:
[u'feature_0', u'feature_1', u'feature_2', u'feature_3', u'feature_4', u'feature_5', u'feature_6', u'feature_7', u'feature_8', u'feature_9', u'feature_10', u'feature_11', u'feature_12', u'feature_13', u'feature_14', u'feature_15', u'feature_16', u'feature_17', u'feature_18', u'feature_19', u'feature_20', u'feature_21', u'feature_22', u'feature_23', u'feature_24', u'feature_25', u'feature_26', u'feature_27']
特征重要度:
[8, 5, 1, 19, 7, 33, 2, 0, 2, 10, 5, 2, 0, 9, 3, 3, 0, 2, 2, 5, 1, 0, 36, 3, 33, 45, 29, 35]
加载模型用于预测
在测试集上的rmse为:
0.4629245607636925

**4.接着之前的模型继续训练**

```python
# 继续训练
# 从./model/model.txt中加载模型初始化
gbm = lgb.train(params,
                lgb_train,
                num_boost_round=10,
                init_model='./model/lgb_model.txt',
                valid_sets=lgb_eval)

print('以旧模型为初始化，完成第 10-20 轮训练...')

# 在训练的过程中调整超参数
# 比如这里调整的是学习率
gbm = lgb.train(params,
                lgb_train,
                num_boost_round=10,
                init_model=gbm,
                learning_rates=lambda iter: 0.05 * (0.99 ** iter),
                valid_sets=lgb_eval)

print('逐步调整学习率完成第 20-30 轮训练...')

# 调整其他超参数
gbm = lgb.train(params,
                lgb_train,
                num_boost_round=10,
                init_model=gbm,
                valid_sets=lgb_eval,
                callbacks=[lgb.reset_parameter(bagging_fraction=[0.7] * 5 + [0.6] * 5)])

print('逐步调整bagging比率完成第 30-40 轮训练...')
```

[11]	valid_0's binary_logloss: 0.616177
[12]	valid_0's binary_logloss: 0.611792
[13]	valid_0's binary_logloss: 0.607043
[14]	valid_0's binary_logloss: 0.602314
[15]	valid_0's binary_logloss: 0.598433
[16]	valid_0's binary_logloss: 0.595238
[17]	valid_0's binary_logloss: 0.592047
[18]	valid_0's binary_logloss: 0.588673
[19]	valid_0's binary_logloss: 0.586084
[20]	valid_0's binary_logloss: 0.584033
以旧模型为初始化，完成第 10-20 轮训练...
[21]	valid_0's binary_logloss: 0.616177
[22]	valid_0's binary_logloss: 0.611834
[23]	valid_0's binary_logloss: 0.607177
[24]	valid_0's binary_logloss: 0.602577
[25]	valid_0's binary_logloss: 0.59831
[26]	valid_0's binary_logloss: 0.595259
[27]	valid_0's binary_logloss: 0.592201
[28]	valid_0's binary_logloss: 0.589017
[29]	valid_0's binary_logloss: 0.586597
[30]	valid_0's binary_logloss: 0.584454
逐步调整学习率完成第 20-30 轮训练...
[31]	valid_0's binary_logloss: 0.616053
[32]	valid_0's binary_logloss: 0.612291
[33]	valid_0's binary_logloss: 0.60856
[34]	valid_0's binary_logloss: 0.605387
[35]	valid_0's binary_logloss: 0.601744
[36]	valid_0's binary_logloss: 0.598556
[37]	valid_0's binary_logloss: 0.595585
[38]	valid_0's binary_logloss: 0.593228
[39]	valid_0's binary_logloss: 0.59018
[40]	valid_0's binary_logloss: 0.588391
逐步调整bagging比率完成第 30-40 轮训练...

**5.自定义损失函数**

```python
# 类似在xgboost中的形式
# 自定义损失函数需要
def loglikelood(preds, train_data):
    labels = train_data.get_label()
    preds = 1. / (1. + np.exp(-preds))
    grad = preds - labels
    hess = preds * (1. - preds)
    return grad, hess


# 自定义评估函数
def binary_error(preds, train_data):
    labels = train_data.get_label()
    return 'error', np.mean(labels != (preds > 0.5)), False


gbm = lgb.train(params,
                lgb_train,
                num_boost_round=10,
                init_model=gbm,
                fobj=loglikelood,
                feval=binary_error,
                valid_sets=lgb_eval)

print('用自定义的损失函数与评估标准完成第40-50轮...')
```

[41]	valid_0's binary_logloss: 0.614429	valid_0's error: 0.268
[42]	valid_0's binary_logloss: 0.610689	valid_0's error: 0.26
[43]	valid_0's binary_logloss: 0.606267	valid_0's error: 0.264
[44]	valid_0's binary_logloss: 0.601949	valid_0's error: 0.258
[45]	valid_0's binary_logloss: 0.597271	valid_0's error: 0.266
[46]	valid_0's binary_logloss: 0.593971	valid_0's error: 0.276
[47]	valid_0's binary_logloss: 0.591427	valid_0's error: 0.278
[48]	valid_0's binary_logloss: 0.588301	valid_0's error: 0.284
[49]	valid_0's binary_logloss: 0.586562	valid_0's error: 0.288
[50]	valid_0's binary_logloss: 0.584056	valid_0's error: 0.288
用自定义的损失函数与评估标准完成第40-50轮...

**sklearn与LightGBM配合使用**

**1.LightGBM建模,Sklearn评估**

```python
# coding: utf-8
import lightgbm as lgb
import pandas as pd
from sklearn.metrics import mean_squared_error
from sklearn.model_selection import GridSearchCV

# 加载数据
print('加载数据...')
df_train = pd.read_csv('./data/regression.train.txt', header=None, sep='\t')
df_test = pd.read_csv('./data/regression.test.txt', header=None, sep='\t')

# 取出特征和标签
y_train = df_train[0].values
y_test = df_test[0].values
X_train = df_train.drop(0, axis=1).values
X_test = df_test.drop(0, axis=1).values

print('开始训练...')
# 直接初始化LGBMRegressor
# 这个LightGBM的Regressor和sklearn中其他Regressor基本是一致的
gbm = lgb.LGBMRegressor(objective='regression',
                        num_leaves=31,
                        learning_rate=0.05,
                        n_estimators=20)

# 使用fit函数拟合
gbm.fit(X_train, y_train,
        eval_set=[(X_test, y_test)],
        eval_metric='l1',
        early_stopping_rounds=5)

# 预测
print('开始预测...')
y_pred = gbm.predict(X_test, num_iteration=gbm.best_iteration_)
# 评估预测结果
print('预测结果的rmse是:')
print(mean_squared_error(y_test, y_pred) ** 0.5)
```

结果略

**2.网格搜索查找最优超参数**

```python
# 配合scikit-learn的网格搜索交叉验证选择最优超参数
estimator = lgb.LGBMRegressor(num_leaves=31)

param_grid = {
    'learning_rate': [0.01, 0.1, 1],
    'n_estimators': [20, 40]
}

gbm = GridSearchCV(estimator, param_grid)

gbm.fit(X_train, y_train)

print('用网格搜索找到的最优超参数为:')
print(gbm.best_params_)
```

用网格搜索找到的最优超参数为:
{'n_estimators': 40, 'learning_rate': 0.1}

**3.绘图解释**

```python
# coding: utf-8
import lightgbm as lgb
import pandas as pd

try:
    import matplotlib.pyplot as plt
except ImportError:
    raise ImportError('You need to install matplotlib for plotting.')

# 加载数据集
print('加载数据...')
df_train = pd.read_csv('./data/regression.train.txt', header=None, sep='\t')
df_test = pd.read_csv('./data/regression.test.txt', header=None, sep='\t')

# 取出特征和标签
y_train = df_train[0].values
y_test = df_test[0].values
X_train = df_train.drop(0, axis=1).values
X_test = df_test.drop(0, axis=1).values

# 构建lgb中的Dataset数据格式
lgb_train = lgb.Dataset(X_train, y_train)
lgb_test = lgb.Dataset(X_test, y_test, reference=lgb_train)

# 设定参数
params = {
    'num_leaves': 5,
    'metric': ('l1', 'l2'),
    'verbose': 0
}

evals_result = {}  # to record eval results for plotting

print('开始训练...')
# 训练
gbm = lgb.train(params,
                lgb_train,
                num_boost_round=100,
                valid_sets=[lgb_train, lgb_test],
                feature_name=['f' + str(i + 1) for i in range(28)],
                categorical_feature=[21],
                evals_result=evals_result,
                verbose_eval=10)

print('在训练过程中绘图...')
ax = lgb.plot_metric(evals_result, metric='l1')
plt.show()

print('画出特征重要度...')
ax = lgb.plot_importance(gbm, max_num_features=10)
plt.show()

print('画出第84颗树...')
ax = lgb.plot_tree(gbm, tree_index=83, figsize=(20, 8), show_info=['split_gain'])
plt.show()

#print('用graphviz画出第84颗树...')
#graph = lgb.create_tree_digraph(gbm, tree_index=83, name='Tree84')
#graph.render(view=True)
```

加载数据...
开始训练...
[10]	training's l2: 0.217995	training's l1: 0.457448	valid_1's l2: 0.21641	valid_1's l1: 0.456464
[20]	training's l2: 0.205099	training's l1: 0.436869	valid_1's l2: 0.201616	valid_1's l1: 0.434057
[30]	training's l2: 0.197421	training's l1: 0.421302	valid_1's l2: 0.192514	valid_1's l1: 0.417019
[40]	training's l2: 0.192856	training's l1: 0.411107	valid_1's l2: 0.187258	valid_1's l1: 0.406303
[50]	training's l2: 0.189593	training's l1: 0.403695	valid_1's l2: 0.183688	valid_1's l1: 0.398997
[60]	training's l2: 0.187043	training's l1: 0.398704	valid_1's l2: 0.181009	valid_1's l1: 0.393977
[70]	training's l2: 0.184982	training's l1: 0.394876	valid_1's l2: 0.178803	valid_1's l1: 0.389805
[80]	training's l2: 0.1828	training's l1: 0.391147	valid_1's l2: 0.176799	valid_1's l1: 0.386476
[90]	training's l2: 0.180817	training's l1: 0.388101	valid_1's l2: 0.175775	valid_1's l1: 0.384404
[100]	training's l2: 0.179171	training's l1: 0.385174	valid_1's l2: 0.175321	valid_1's l1: 0.382929
在训练过程中绘图...

![49](C:\Users\Administrator\Pictures\Saved Pictures\50.png)

画出特征重要度...

![51](C:\Users\Administrator\Pictures\Saved Pictures\51.png)

画出第84颗树...

![52](C:\Users\Administrator\Pictures\Saved Pictures\52.png)



**便利店销售预测**

![143](C:\Users\Administrator\Pictures\Saved Pictures\143.png)

```python
#导入所需要的库
import pandas as pd
import datetime
import csv
import numpy as np
import os
import scipy as sp
import xgboost as xgb
import itertools
import operator
import warnings
warnings.filterwarnings("ignore")

from sklearn.preprocessing import StandardScaler, LabelEncoder
from sklearn.base import TransformerMixin
from sklearn import cross_validation
from matplotlib import pylab as plt
plot = True

goal = 'Sales'
myid = 'Id'
```

```python
# 定义一些变换和评判准则
def ToWeight(y):
    w = np.zeros(y.shape, dtype=float)
    ind = y != 0
    w[ind] = 1./(y[ind]**2)
    return w

def rmspe(yhat, y):
    w = ToWeight(y)
    rmspe = np.sqrt(np.mean( w * (y - yhat)**2 ))
    return rmspe

def rmspe_xg(yhat, y):
    # y = y.values
    y = y.get_label()
    y = np.exp(y) - 1
    yhat = np.exp(yhat) - 1
    w = ToWeight(y)
    rmspe = np.sqrt(np.mean(w * (y - yhat)**2))
    return "rmspe", rmspe
```

```python
# 加载数据
store = pd.read_csv('./data/store.csv')
train_df = pd.read_csv('./data/train.csv')
test_df = pd.read_csv('./data/test.csv')

def load_data():
    """
        加载数据，设定数值型和非数值型数据
    """
    store = pd.read_csv('./data/store.csv')
    train_org = pd.read_csv('./data/train.csv',dtype={'StateHoliday':pd.np.string_})
    test_org = pd.read_csv('./data/test.csv',dtype={'StateHoliday':pd.np.string_})
    train = pd.merge(train_org,store, on='Store', how='left')
    test = pd.merge(test_org,store, on='Store', how='left')
    features = test.columns.tolist()
    numerics = ['int16', 'int32', 'int64', 'float16', 'float32', 'float64']
    features_numeric = test.select_dtypes(include=numerics).columns.tolist()
    features_non_numeric = [f for f in features if f not in features_numeric]
    return (train,test,features,features_non_numeric)
```

```python
# 数据与特征处理
def process_data(train,test,features,features_non_numeric):
    """
        特征工程与特征选择
    """
    ### 特征工程
    train = train[train['Sales'] > 0]

    for data in [train,test]:
        # year month day
        data['year'] = data.Date.apply(lambda x: x.split('-')[0])
        data['year'] = data['year'].astype(float)
        data['month'] = data.Date.apply(lambda x: x.split('-')[1])
        data['month'] = data['month'].astype(float)
        data['day'] = data.Date.apply(lambda x: x.split('-')[2])
        data['day'] = data['day'].astype(float)

        # 特定的促销月份
        data['promojan'] = data.PromoInterval.apply(lambda x: 0 if isinstance(x, float) else 1 if "Jan" in x else 0)
        data['promofeb'] = data.PromoInterval.apply(lambda x: 0 if isinstance(x, float) else 1 if "Feb" in x else 0)
        data['promomar'] = data.PromoInterval.apply(lambda x: 0 if isinstance(x, float) else 1 if "Mar" in x else 0)
        data['promoapr'] = data.PromoInterval.apply(lambda x: 0 if isinstance(x, float) else 1 if "Apr" in x else 0)
        data['promomay'] = data.PromoInterval.apply(lambda x: 0 if isinstance(x, float) else 1 if "May" in x else 0)
        data['promojun'] = data.PromoInterval.apply(lambda x: 0 if isinstance(x, float) else 1 if "Jun" in x else 0)
        data['promojul'] = data.PromoInterval.apply(lambda x: 0 if isinstance(x, float) else 1 if "Jul" in x else 0)
        data['promoaug'] = data.PromoInterval.apply(lambda x: 0 if isinstance(x, float) else 1 if "Aug" in x else 0)
        data['promosep'] = data.PromoInterval.apply(lambda x: 0 if isinstance(x, float) else 1 if "Sep" in x else 0)
        data['promooct'] = data.PromoInterval.apply(lambda x: 0 if isinstance(x, float) else 1 if "Oct" in x else 0)
        data['promonov'] = data.PromoInterval.apply(lambda x: 0 if isinstance(x, float) else 1 if "Nov" in x else 0)
        data['promodec'] = data.PromoInterval.apply(lambda x: 0 if isinstance(x, float) else 1 if "Dec" in x else 0)

    ### 特征集合
    noisy_features = [myid,'Date']
    features = [c for c in features if c not in noisy_features]
    features_non_numeric = [c for c in features_non_numeric if c not in noisy_features]
    features.extend(['year','month','day'])
    # 缺失值填充
    class DataFrameImputer(TransformerMixin):
        # http://stackoverflow.com/questions/25239958/impute-categorical-missing-values-in-scikit-learn
        def __init__(self):
            """Impute missing values.
            Columns of dtype object are imputed with the most frequent value
            in column.
            Columns of other types are imputed with mean of column.
            """
        def fit(self, X, y=None):
            self.fill = pd.Series([X[c].value_counts().index[0] # mode
                if X[c].dtype == np.dtype('O') else X[c].mean() for c in X], # mean
                index=X.columns)
            return self
        def transform(self, X, y=None):
            return X.fillna(self.fill)
    train = DataFrameImputer().fit_transform(train)
    test = DataFrameImputer().fit_transform(test)
    # 预处理非数值型的特征
    le = LabelEncoder()
    for col in features_non_numeric:
        le.fit(list(train[col])+list(test[col]))
        train[col] = le.transform(train[col])
        test[col] = le.transform(test[col])
    # LR和神经网络这种模型都对输入数据的幅度极度敏感，请先做归一化操作
    scaler = StandardScaler()
    for col in set(features) - set(features_non_numeric) - \
      set([]): # TODO: add what not to scale
        scaler.fit(list(train[col])+list(test[col]))
        train[col] = scaler.transform(train[col])
        test[col] = scaler.transform(test[col])
    return (train,test,features,features_non_numeric)
```

```Python
# 训练与分析
def XGB_native(train,test,features,features_non_numeric):
    depth = 13
    eta = 0.01
    ntrees = 8000
    mcw = 3
    params = {"objective": "reg:linear",
              "booster": "gbtree",
              "eta": eta,
              "max_depth": depth,
              "min_child_weight": mcw,
              "subsample": 0.9,
              "colsample_bytree": 0.7,
              "silent": 1
              }
    print "Running with params: " + str(params)
    print "Running with ntrees: " + str(ntrees)
    print "Running with features: " + str(features)

    # Train model with local split
    tsize = 0.05
    X_train, X_test = cross_validation.train_test_split(train, test_size=tsize)
    dtrain = xgb.DMatrix(X_train[features], np.log(X_train[goal] + 1))
    dvalid = xgb.DMatrix(X_test[features], np.log(X_test[goal] + 1))
    watchlist = [(dvalid, 'eval'), (dtrain, 'train')]
    gbm = xgb.train(params, dtrain, ntrees, evals=watchlist, early_stopping_rounds=100, feval=rmspe_xg, verbose_eval=True)
    train_probs = gbm.predict(xgb.DMatrix(X_test[features]))
    indices = train_probs < 0
    train_probs[indices] = 0
    error = rmspe(np.exp(train_probs) - 1, X_test[goal].values)
    print error

    # Predict and Export
    test_probs = gbm.predict(xgb.DMatrix(test[features]))
    indices = test_probs < 0
    test_probs[indices] = 0
    submission = pd.DataFrame({myid: test[myid], goal: np.exp(test_probs) - 1})
    if not os.path.exists('result/'):
        os.makedirs('result/')
    submission.to_csv("./result/dat-xgb_d%s_eta%s_ntree%s_mcw%s_tsize%s.csv" % (str(depth),str(eta),str(ntrees),str(mcw),str(tsize)) , index=False)
    # Feature importance
    if plot:
      outfile = open('xgb.fmap', 'w')
      i = 0
      for feat in features:
          outfile.write('{0}\t{1}\tq\n'.format(i, feat))
          i = i + 1
      outfile.close()
      importance = gbm.get_fscore(fmap='xgb.fmap')
      importance = sorted(importance.items(), key=operator.itemgetter(1))
      df = pd.DataFrame(importance, columns=['feature', 'fscore'])
      df['fscore'] = df['fscore'] / df['fscore'].sum()
      # Plotitup
      plt.figure()
      df.plot()
      df.plot(kind='barh', x='feature', y='fscore', legend=False, figsize=(25, 15))
      plt.title('XGBoost Feature Importance')
      plt.xlabel('relative importance')
      plt.gcf().savefig('Feature_Importance_xgb_d%s_eta%s_ntree%s_mcw%s_tsize%s.png' % (str(depth),str(eta),str(ntrees),str(mcw),str(tsize)))
      
print "=> 载入数据中..."
train,test,features,features_non_numeric = load_data()
print "=> 处理数据与特征工程..."
train,test,features,features_non_numeric = process_data(train,test,features,features_non_numeric)
print "=> 使用XGBoost建模..."
XGB_native(train,test,features,features_non_numeric)
```

### 9.3大学生助学金精准预测比赛案例精讲

#### 9.3.1本章概述

以**房价预测**

**经典的线性回归 模型为例**

本次竞赛中，数据集通过79个特征变量来描述爱荷华州埃姆斯的住宅房屋的各个方面，需要预测每个住宅的最终价格，并提交预测结果。问题转化成回归问题，评估指标为均方根误差(RMSE)

**导入必要的库和数据**

```python
import numpy as np 
import pandas as pd
%matplotlib inline
import matplotlib.pyplot as plt
import seaborn as sns
color = sns.color_palette()
sns.set_style('darkgrid')
import warnings
def ignore_warn(*args, **kwargs):
    pass
warnings.warn = ignore_warn


from scipy import stats
from scipy.stats import norm, skew

pd.set_option('display.float_format', lambda x: '{:.3f}'.format(x)) #Limiting floats output

train = pd.read_csv('./input/train.csv')
test = pd.read_csv('./input/test.csv')


# 检查数据维度
print("训练集丢弃ID特征前的size：",train.shape)
print("测试集丢弃ID特征前的size：",test.shape)

# 单独保存ID列
train_ID = train['Id']
test_ID = test['Id']

# 去掉ID列
train.drop("Id", axis = 1, inplace = True)
test.drop("Id", axis = 1, inplace = True)

# 检查数据维度
print("\n训练集丢弃ID特征后的size：",train.shape) 
print("测试集丢弃ID特征后的size：",test.shape)
```

**数据处理**

```python
# 绘图
fig, ax = plt.subplots()
ax.scatter(x = train['GrLivArea'], y = train['SalePrice'])
plt.ylabel('SalePrice', fontsize=13)
plt.xlabel('GrLivArea', fontsize=13)
plt.show()
```

![144](C:\Users\Administrator\Pictures\Saved Pictures\144.png)

```python
# 删除离群点
train = train.drop(train[(train['GrLivArea']>4000) & (train['SalePrice']<300000)].index)

# 绘图
fig, ax = plt.subplots()
ax.scatter(train['GrLivArea'], train['SalePrice'])
plt.ylabel('SalePrice', fontsize=13)
plt.xlabel('GrLivArea', fontsize=13)
plt.show()
```

![145](C:\Users\Administrator\Pictures\Saved Pictures\145.png)

**目标值处理**

- 线性的模型需要正态分布的目标值才能发挥最大的作用。我们需要检测房价什么时候偏离正态分布。使用probplot函数，即正态概率图

  ```python
  sns.distplot(train['SalePrice'] , fit=norm)
  # 正态分布拟合
  (mu, sigma) = norm.fit(train['SalePrice'])
  print( '\n mu = {:.2f} and sigma = {:.2f}\n'.format(mu, sigma))
  
  # 绘图
  plt.legend(['Normal dist. ($\mu=$ {:.2f} and $\sigma=$ {:.2f} )'.format(mu, sigma)],
              loc='best')
  plt.ylabel('Frequency')
  plt.title('SalePrice distribution')
  
  # 原始数据分布绘图
  fig = plt.figure()
  res = stats.probplot(train['SalePrice'], plot=plt)
  plt.show()
  ```

  ![146](C:\Users\Administrator\Pictures\Saved Pictures\146.png)

  ![147](C:\Users\Administrator\Pictures\Saved Pictures\147.png)


- 此时的正态分布属于右偏态分布，即整体峰值向左偏离，并且偏度(skewness)较大，需要对目标值做log转换，以恢复目标值的正态性

```python
# 使用log1p函数完成log(1+x)变换
train["SalePrice"] = np.log1p(train["SalePrice"])

# 查看调整后的分布
sns.distplot(train['SalePrice'] , fit=norm);

# 重新拟合
(mu, sigma) = norm.fit(train['SalePrice'])
print( '\n mu = {:.2f} and sigma = {:.2f}\n'.format(mu, sigma))

# 重新绘制正态分布
plt.legend(['Normal dist. ($\mu=$ {:.2f} and $\sigma=$ {:.2f} )'.format(mu, sigma)],
            loc='best')
plt.ylabel('Frequency')
plt.title('SalePrice distribution')

# 绘制变换后的分布
fig = plt.figure()
res = stats.probplot(train['SalePrice'], plot=plt)
plt.show()
```

![148](C:\Users\Administrator\Pictures\Saved Pictures\148.png)

![149](C:\Users\Administrator\Pictures\Saved Pictures\149.png)

**特征工程**

```python
ntrain = train.shape[0]
ntest = test.shape[0]
y_train = train.SalePrice.values
all_data = pd.concat((train, test)).reset_index(drop=True)
all_data.drop(['SalePrice'], axis=1, inplace=True)
print("合并后数据集的size：",all_data.shape)

all_data_na = (all_data.isnull().sum() / len(all_data)) * 100
all_data_na = all_data_na.drop(all_data_na[all_data_na == 0].index).sort_values(ascending=False)[:30]
missing_data = pd.DataFrame({'Missing Ratio' :all_data_na})

f, ax = plt.subplots(figsize=(15, 12))
plt.xticks(rotation='90')
sns.barplot(x=all_data_na.index, y=all_data_na)
plt.xlabel('Features', fontsize=15)
plt.ylabel('Percent of missing values', fontsize=15)
plt.title('Percent missing data by feature', fontsize=15)
```

![150](C:\Users\Administrator\Pictures\Saved Pictures\150.png)

```python
# 绘制热力图去查看特征相关性
corrmat = train.corr()
plt.subplots(figsize=(12,9))
sns.heatmap(corrmat, vmax=0.9, square=True)
```

![151](C:\Users\Administrator\Pictures\Saved Pictures\151.png)

 可以看到对角线有一条白线，这代表相同的特征相关性为最高，但值得注意的是，有两个正方形小块：TotaLBsmtSF和1stFlrSF、GarageAreas和GarageCars处。这代表全部建筑面积TotaLBsmtSF与一层建筑面积1stFlrSF成强正相关，车库区域GarageAreas和车库车辆GarageCars成强正相关，那么在填补缺失值的时候就有了依据，我们可以直接删掉一个多余的特征或者使用一个填补另一个。

```python
all_data["PoolQC"] = all_data["PoolQC"].fillna("None")
all_data["MiscFeature"] = all_data["MiscFeature"].fillna("None")
all_data["Alley"] = all_data["Alley"].fillna("None")
all_data["Fence"] = all_data["Fence"].fillna("None")
all_data["FireplaceQu"] = all_data["FireplaceQu"].fillna("None")

#Group by neighborhood and fill in missing value by the median LotFrontage of all the neighborhood
all_data["LotFrontage"] = all_data.groupby("Neighborhood")["LotFrontage"].transform(
    lambda x: x.fillna(x.median()))

for col in ('GarageType', 'GarageFinish', 'GarageQual', 'GarageCond'):
    all_data[col] = all_data[col].fillna('None')
    
for col in ('GarageYrBlt', 'GarageArea', 'GarageCars'):
    all_data[col] = all_data[col].fillna(0)
    
for col in ('BsmtFinSF1', 'BsmtFinSF2', 'BsmtUnfSF','TotalBsmtSF', 'BsmtFullBath', 'BsmtHalfBath'):
    all_data[col] = all_data[col].fillna(0)
    
for col in ('BsmtQual', 'BsmtCond', 'BsmtExposure', 'BsmtFinType1', 'BsmtFinType2'):
    all_data[col] = all_data[col].fillna('None')
    
all_data["MasVnrType"] = all_data["MasVnrType"].fillna("None")
all_data["MasVnrArea"] = all_data["MasVnrArea"].fillna(0)

all_data['MSZoning'] = all_data['MSZoning'].fillna(all_data['MSZoning'].mode()[0])

#对于'Utilities'这个特征，所有记录均为“AllPub”，除了一个“NoSeWa”和2个NA。 由于拥有'NoSewa'的房子在训练集中，
#因此此特征对预测建模无助。 然后我们可以安全地删除它。
all_data = all_data.drop(['Utilities'], axis=1)

all_data["Functional"] = all_data["Functional"].fillna("Typ")
all_data['Electrical'] = all_data['Electrical'].fillna(all_data['Electrical'].mode()[0])
all_data['KitchenQual'] = all_data['KitchenQual'].fillna(all_data['KitchenQual'].mode()[0])
all_data['Exterior1st'] = all_data['Exterior1st'].fillna(all_data['Exterior1st'].mode()[0])
all_data['Exterior2nd'] = all_data['Exterior2nd'].fillna(all_data['Exterior2nd'].mode()[0])
all_data['SaleType'] = all_data['SaleType'].fillna(all_data['SaleType'].mode()[0])
all_data['MSSubClass'] = all_data['MSSubClass'].fillna("None")
all_data_na = (all_data.isnull().sum() / len(all_data)) * 100
all_data_na = all_data_na.drop(all_data_na[all_data_na == 0].index).sort_values(ascending=False)
missing_data = pd.DataFrame({'Missing Ratio' :all_data_na})
```

更多的特征工程

```python
#1、有许多特征实际上是类别型的特征，但给出来的是数字。比如MSSubClass，是评价房子种类的一个特征，给出的是10-100的数字，但实际上是类别，所以我们需要将其转化为字符串类别。
# MSSubClass是房子种类
all_data['MSSubClass'] = all_data['MSSubClass'].apply(str)

# 同样对OverallCond做变换
all_data['OverallCond'] = all_data['OverallCond'].astype(str)

# 年与月份
all_data['YrSold'] = all_data['YrSold'].astype(str)
all_data['MoSold'] = all_data['MoSold'].astype(str)

#2、接下来 LabelEncoder，对部分类别的特征进行编号
from sklearn.preprocessing import LabelEncoder
cols = ('FireplaceQu', 'BsmtQual', 'BsmtCond', 'GarageQual', 'GarageCond', 
        'ExterQual', 'ExterCond','HeatingQC', 'PoolQC', 'KitchenQual', 'BsmtFinType1', 
        'BsmtFinType2', 'Functional', 'Fence', 'BsmtExposure', 'GarageFinish', 'LandSlope',
        'LotShape', 'PavedDrive', 'Street', 'Alley', 'CentralAir', 'MSSubClass', 'OverallCond', 
        'YrSold', 'MoSold')

# 使用LabelEncoder做变换
for c in cols:
    lbl = LabelEncoder() 
    lbl.fit(list(all_data[c].values)) 
    all_data[c] = lbl.transform(list(all_data[c].values))

# 查看维度        
print('all_data的数据维度: {}'.format(all_data.shape))

#3、接下来添加一个重要的特征，因为我们实际在购买房子的时候会考虑总面积的大小，但是此数据集中并没有包含此数据。总面积等于地下室面积+1层面积+2层面积。
# 添加总面积特征
all_data['TotalSF'] = all_data['TotalBsmtSF'] + all_data['1stFlrSF'] + all_data['2ndFlrSF']

#4、我们对房价进行分析，不符合正态分布的我们将其log转换，使其符合正态分布。那么偏离正态分布太多的特征我们也对它进行转化
numeric_feats = all_data.dtypes[all_data.dtypes != "object"].index

# 对所有数值型的特征都计算skew，计算一下偏度
skewed_feats = all_data[numeric_feats].apply(lambda x: skew(x.dropna())).sort_values(ascending=False)
print("\nSkew in numerical features: \n")
skewness = pd.DataFrame({'Skew' :skewed_feats})

skewness = skewness[abs(skewness) > 0.75]
print("总共有 {} 数值型的特征做变换".format(skewness.shape[0]))

from scipy.special import boxcox1p
skewed_features = skewness.index
lam = 0.15
for feat in skewed_features:
    #all_data[feat] += 1
    all_data[feat] = boxcox1p(all_data[feat], lam)
    
#5、将类别特征进行哑变量转化
all_data = pd.get_dummies(all_data)
print(all_data.shape)

'''
(2917, 220)
'''

#6、获得新的训练和测试集。至此，我们的特征工程已经处理完毕。
train = all_data[:ntrain]
test = all_data[ntrain:]
train.shape

'''
(1458, 220)
'''
```

**模型选择**

```python
from sklearn.linear_model import ElasticNet, Lasso,  BayesianRidge, LassoLarsIC
from sklearn.ensemble import RandomForestRegressor,  GradientBoostingRegressor
from sklearn.kernel_ridge import KernelRidge
from sklearn.pipeline import make_pipeline
from sklearn.preprocessing import RobustScaler
from sklearn.base import BaseEstimator, TransformerMixin, RegressorMixin, clone
from sklearn.model_selection import KFold, cross_val_score, train_test_split
from sklearn.metrics import mean_squared_error
import xgboost as xgb
import lightgbm as lgb
```

```python
# 交叉验证函数
n_folds = 5

def rmsle_cv(model):
    kf = KFold(n_folds, shuffle=True, random_state=42).get_n_splits(train.values)
    rmse= np.sqrt(-cross_val_score(model, train.values, y_train, scoring="neg_mean_squared_error", cv = kf))
    return(rmse)
```

```python
#1、LASSO Regression

#该模型可能对异常值非常敏感。 所以我们需要让它更加健壮。 为此，我们在pipeline上使用sklearn的Robustscaler()方法

lasso = make_pipeline(RobustScaler(), Lasso(alpha =0.0005, random_state=1))

#2、Elastic Net Regression

#同样让它对异常值具有鲁棒性

ENet = make_pipeline(RobustScaler(), ElasticNet(alpha=0.0005, l1_ratio=.9, random_state=3))

#3、Kernel Ridge Regression

KRR = KernelRidge(alpha=0.6, kernel='polynomial', degree=2, coef0=2.5)

#4、Gradient Boosting Regression

#由于Huber loss使得它对于异常值具有鲁棒性

GBoost = GradientBoostingRegressor(n_estimators=3000, learning_rate=0.05,
                                   max_depth=4, max_features='sqrt',
                                   min_samples_leaf=15, min_samples_split=10, 
                                   loss='huber', random_state =5)
#5、XGBoost 

model_xgb = xgb.XGBRegressor(colsample_bytree=0.4603, gamma=0.0468, 
                             learning_rate=0.05, max_depth=3, 
                             min_child_weight=1.7817, n_estimators=2200,
                             reg_alpha=0.4640, reg_lambda=0.8571,
                             subsample=0.5213, silent=1,
                             random_state =7, nthread = -1)
#6、LightGBM

model_lgb = lgb.LGBMRegressor(objective='regression',num_leaves=5,
                              learning_rate=0.05, n_estimators=720,
                              max_bin = 55, bagging_fraction = 0.8,
                              bagging_freq = 5, feature_fraction = 0.2319,
                              feature_fraction_seed=9, bagging_seed=9,
                              min_data_in_leaf =6, min_sum_hessian_in_leaf = 11)
 
#计算各个模型的得分
score = rmsle_cv(lasso)
print("\nLasso 得分: {:.4f} ({:.4f})\n".format(score.mean(), score.std()))
'''
Lasso 得分: 0.1115 (0.0074)
'''

score = rmsle_cv(ENet)
print("ElasticNet 得分: {:.4f} ({:.4f})\n".format(score.mean(), score.std()))
'''
ElasticNet 得分: 0.1116 (0.0074)
'''

score = rmsle_cv(KRR)
print("Kernel Ridge 得分: {:.4f} ({:.4f})\n".format(score.mean(), score.std()))
'''
Kernel Ridge 得分: 0.1153 (0.0075)
'''

score = rmsle_cv(GBoost)
print("Gradient Boosting 得分: {:.4f} ({:.4f})\n".format(score.mean(), score.std()))
'''
Gradient Boosting 得分: 0.1177 (0.0080)
'''

score = rmsle_cv(model_xgb)
print("Xgboost 得分: {:.4f} ({:.4f})\n".format(score.mean(), score.std()))
'''
Xgboost 得分: 0.1165 (0.0054)
'''

score = rmsle_cv(model_lgb)
print("LGBM 得分: {:.4f} ({:.4f})\n" .format(score.mean(), score.std()))
'''
LGBM 得分: 0.1162 (0.0071)
'''
```

**模型融合**

Stacking模型融合->>Average-Stacking
  我们从简单的平均基本模型的方法开始。 我们构建了一个新类来扩展scikit-learn和模型，并且还利用封装与代码重用（继承）

```python
class AveragingModels(BaseEstimator, RegressorMixin, TransformerMixin):
    def __init__(self, models):
        self.models = models
        
    # 遍历所有模型，你和数据
    def fit(self, X, y):
        self.models_ = [clone(x) for x in self.models]
        
        for model in self.models_:
            model.fit(X, y)

        return self
    
    # 预估，并对预估结果值做average
    def predict(self, X):
        predictions = np.column_stack([
            model.predict(X) for model in self.models_
        ])
        return np.mean(predictions, axis=1)   
```

平均四个模型ENet，GBoost，KRR和lasso。利用上面重写的方法，我们可以轻松地添加更多的模型

```python
averaged_models = AveragingModels(models = (ENet, GBoost, KRR, lasso))

score = rmsle_cv(averaged_models)
print(" 对基模型集成后的得分: {:.4f} ({:.4f})\n".format(score.mean(), score.std()))
'''
对基模型集成后的得分: 0.1091 (0.0075)
'''
```

**Meta-model Stacking**
在这种方法中，我们在平均基础模型上添加Meta-model，并使用这些基模型的out-of-folds预测来训练我们的Meta-model。
训练部分的步骤如下：
1、将整个训练集分解成两个不相交的集合（这里是train和.holdout）。
2、在第一部分（train）上训练几个基本模型。
3、在第二个部分（holdout）上测试这些基本模型。
4、使用(3)中的预测（称为 out-of-fold 预测）作为输入，并将正确的标签（目标变量）作为输出来训练更高层次的学习模型称为元模型。
前三个步骤是迭代完成的。例如，如果我们采取5倍的fold，我们首先将训练数据分成5次。然后我们会做5次迭代。在每次迭代中，我们训练每个基础模型4倍，并预测剩余的fold（holdout fold）。

```python
#构建了一个Stacking averaged Models的类
class StackingAveragedModels(BaseEstimator, RegressorMixin, TransformerMixin):
    def __init__(self, base_models, meta_model, n_folds=5):
        self.base_models = base_models
        self.meta_model = meta_model
        self.n_folds = n_folds
   
    # 遍历拟合原始模型
    def fit(self, X, y):
        self.base_models_ = [list() for x in self.base_models]
        self.meta_model_ = clone(self.meta_model)
        kfold = KFold(n_splits=self.n_folds, shuffle=True, random_state=156)
        
        # 得到基模型，并用基模型对out_of_fold做预估，为学习stacking的第2层做数据准备
        out_of_fold_predictions = np.zeros((X.shape[0], len(self.base_models)))
        for i, model in enumerate(self.base_models):
            for train_index, holdout_index in kfold.split(X, y):
                instance = clone(model)
                self.base_models_[i].append(instance)
                instance.fit(X[train_index], y[train_index])
                y_pred = instance.predict(X[holdout_index])
                out_of_fold_predictions[holdout_index, i] = y_pred
                
        # 学习stacking模型
        self.meta_model_.fit(out_of_fold_predictions, y)
        return self
   
    # 做stacking预估
    def predict(self, X):
        meta_features = np.column_stack([
            np.column_stack([model.predict(X) for model in base_models]).mean(axis=1)
            for base_models in self.base_models_ ])
        return self.meta_model_.predict(meta_features)

#测试Meta-model Stacking结果
stacked_averaged_models = StackingAveragedModels(base_models = (ENet, GBoost, KRR),
                                                 meta_model = lasso)

score = rmsle_cv(stacked_averaged_models)
print("Stacking Averaged models score: {:.4f} ({:.4f})".format(score.mean(), score.std())) 
#添加元学习器后，我们得到了一个更好的结果！
#然后为了得到最后提交的结果，我们将StackedRegressor、XGBoost和LightGBM进行融合，得到rmsle的结果。
def rmsle(y, y_pred):
    return np.sqrt(mean_squared_error(y, y_pred))

#最终的训练和预测
#StackedRegressor:
stacked_averaged_models.fit(train.values, y_train)
stacked_train_pred = stacked_averaged_models.predict(train.values)
stacked_pred = np.expm1(stacked_averaged_models.predict(test.values))
print(rmsle(y_train, stacked_train_pred))

#XGBoost:
model_xgb.fit(train, y_train)
xgb_train_pred = model_xgb.predict(train)
xgb_pred = np.expm1(model_xgb.predict(test))
print(rmsle(y_train, xgb_train_pred))

#LightGBM:
model_lgb.fit(train, y_train)
lgb_train_pred = model_lgb.predict(train)
lgb_pred = np.expm1(model_lgb.predict(test.values))
print(rmsle(y_train, lgb_train_pred))

'''RMSE on the entire Train data when averaging'''

print('训练集上的RMSLE得分:')
print(rmsle(y_train,stacked_train_pred*0.72 +
               xgb_train_pred*0.14  + lgb_train_pred*0.14 ))

#将三者进行融合，然后得到Ensemble prediction
ensemble = stacked_pred*0.70 + xgb_pred*0.15 + lgb_pred*0.15

sub = pd.DataFrame()
sub['Id'] = test_ID
sub['SalePrice'] = ensemble
sub.to_csv('submission.csv',index=False
```

#### 9.2案例代码讲解

![142](C:\Users\Administrator\Pictures\Saved Pictures\142.png)

**大学生助学金精准资助预测**

**任务**
大数据时代的来临，为创新资助工作方式提供了新的理念和技术支持，也为高校利用大数据推进快速、便捷、高效精准资助工作带来了新的机遇。基于学生每天产生的一卡通实时数据，利用大数据挖掘与分析技术、数学建模理论帮助管理者掌握学生在校期间的真实消费情况、学生经济水平、发现“隐性贫困”与疑似“虚假认定”学生，从而实现精准资助，让每一笔资助经费得到最大价值的发挥与利用，帮助每一个贫困大学生顺利完成学业。因此，基于学生在校期间产生的消费数据运用大数据挖掘与分析技术实现贫困学生的精准挖掘具有重要的应用价值。

教育算法资格赛采用某高校2014、2015两学年的助学金获取情况作为标签，2013~2014、2014~2015两学年的学生在校行为数据作为原始数据，包括消费数据、图书借阅数据、寝室门禁数据、图书馆门禁数据、学生成绩排名数据，并以助学金获取金额作为结果数据进行模型优化和评价。

本次竞赛需利用学生在2013/09~2014/09的数据，预测学生在2014年的助学金获得情况；利用学生在2014/09~2015/09的数据，预测学生在2015年的助学金获得情况。虽然所有数据在时间上混合在了一起，即训练集和测试集中的数据都有2013/09~2015/09的数据，但是学生的行为数据和助学金数据是对应的。

此竞赛赛程分为两个阶段，以测试集切换为标志，2017年2月13日切换。

**数据描述**

数据总览：

数据分为两组，分别是训练集和测试集，每一组都包含大约1万名学生的信息纪录：

- 图书借阅数据borrow_train.txt和borrow_test.txt
- 一卡通数据card_train.txt和card_test.txt
- 寝室门禁数据dorm_train.txt和dorm_test.txt
- 图书馆门禁数据library_train.txt和library_test.txt
- 学生成绩数据score_train.txt和score_test.txt
- 助学金获奖数据subsidy_train.txt和subsidy_test.txt

训练集和测试集中的学生id无交集，详细信息如下。注：数据中所有的记录均为“原始数据记录”直接经过脱敏而来，可能会存在一些重复的或者是异常的记录，请参赛者自行处理.

**数据详细描述**

**1.图书借阅数据borrow*.txt（*代表*train和*test）**

> ​    注：有些图书的编号缺失。字段描述和示例如下（第三条记录缺失图书编号）：
> ​    学生id，借阅日期，图书名称，图书编号
> ​    9708,2014/2/25,"我的英语日记/ (韩)南银英著 (韩)卢炫廷插图","H315 502"
> ​    6956,2013/10/27,"解读联想思维: 联想教父柳传志","K825.38=76 547"
> ​    9076,2014/3/28,"公司法 gong si fa = = Corporation law / 范健, 王建文著 eng"

**2.一卡通数据card*.txt**

> 字段描述和示例如下：
> ​    学生id，消费类别，消费地点，消费方式，消费时间，消费金额，剩余金额
> ​    1006,"POS消费","地点551","淋浴","2013/09/01 00:00:32","0.5","124.9"
> ​    1406,"POS消费","地点78","其他","2013/09/01 00:00:40","0.6","373.82"
> ​    13554,"POS消费","地点6","淋浴","2013/09/01 00:00:57","0.5","522.37"

**3.寝室门禁数据dorm*.txt**

> 字段描述和示例如下：
> ​    学生id，具体时间，进出方向(0进寝室，1出寝室)    
> ​    13126,"2014/01/21 03:31:11","1"
> ​    9228,"2014/01/21 10:28:23","0"

**4.图书馆门禁数据library*.txt**

> 图书馆的开放时间为早上7点到晚上22点，门禁编号数据在2014/02/23之前只有“编号”信息，之后引入了“进门、出门”信息，还有些异常信息为null，请参赛者自行处理。
>
> ​    字段描述和示例如下：
> ​    学生id，门禁编号，具体时间
> ​    3684,"5","2013/09/01 08:42:50"
> ​    7434,"5","2013/09/01 08:50:08"
> ​    8000,"进门2","2014/03/31 18:20:31"
> ​    5332,"小门","2014/04/03 20:11:06"
> ​    7397,"出门4","2014/09/04 16:50:51"

**5.学生成绩数据score*.txt**

> 注：成绩排名的计算方式是将所有成绩按学分加权求和，然后除以学分总和，再按照学生所在学院排序。
>
> ​    学生id,学院编号,成绩排名
> ​    0,9,1
> ​    1,9,2
> ​    8,6,1565
> ​    9,6,1570

**6.助学金数据（训练集中有金额，测试集中无金额）subsidy*.txt**

> 字段描述和示例如下：
> ​    学生id,助学金金额（分隔符为半角逗号）
> ​    10,0
> ​    22,1000
> ​    28,1000
> ​    64,1500
> ​    650,2000

#### 9.3.3案例第一名解决流程讲解

**流程分析**

![142](C:\Users\Administrator\Pictures\Saved Pictures\142.jpg)

![143](C:\Users\Administrator\Pictures\Saved Pictures\143.jpg)

![144](C:\Users\Administrator\Pictures\Saved Pictures\144.jpg)

![145](C:\Users\Administrator\Pictures\Saved Pictures\145.jpg)

![146](C:\Users\Administrator\Pictures\Saved Pictures\146.jpg)

![147](C:\Users\Administrator\Pictures\Saved Pictures\147.jpg)

![148](C:\Users\Administrator\Pictures\Saved Pictures\148.jpg)

![149](C:\Users\Administrator\Pictures\Saved Pictures\153.jpg)

![150](C:\Users\Administrator\Pictures\Saved Pictures\150.jpg)

![151](C:\Users\Administrator\Pictures\Saved Pictures\151.jpg)

![154](C:\Users\Administrator\Pictures\Saved Pictures\154.jpg)

![](C:\Users\Administrator\Pictures\xiniu_neteasy.png)
