---
typora-copy-images-to:
---

# Machine Learning

机器学习笔记，[B站吴恩达老师视频](https://www.bilibili.com/video/BV164411S78V/?spm_id_from=333.999.0.0)

https://github.com/BroMiaoY/Note/blob/main/MachineLearning/MachineLearning/

## 1 Supervised Learning AND Unsupervised Learning

### 1.3 Supervised Learning

“right answer”given 有标签

- **Pegression Problem** :Predict continuous valued Output(Price)

![image-20230601110803928](image\Pegression(house_price_predict).png)

- **Classificaton Problem**:Discrete valued Output(0 or 1)

  - one feature

  ![image-20230601111053713](image\Classification(one_feature).png)

  - two feature

![Classification(two_features)](image\Classification(two_features).png)

### 1.4 Unsupervised Learning

clustering algorithms

### 1.5 Summarize

- **Supervised Learning**：有标签
  - Regression Problem：Predict continuous value
    - 房价预测、股票预测
  - Classification Problem：Predict discrete value
    - 垃圾邮件检测
- **Unsupervised Learning**：无标签
  - Clustering
    - ​	推荐系统



## 2 Linear regression with one variable

### 2.1 模型描述

- **Notation**
  - m:训练集大小
  - X：输入变量/特征
  - y：输出变量

![image-20230601143652259](image\2.1Notation.png)

![image-20230601144432420](image\2.1linear_regression.png)

### 2.2 Cost Function

- **Cost Function/平方误差代价函数**：

计算使得**训练集中\*预测值-实际值\*的平方总和的平均值**最小的两个参数

![image-20230601145905596](image\Cost Function.png)

### 2.3 Cost Function(1)

- **简化**

![image-20230601150334970](image\2.3CostFunction简化.png)

- 回归函数和代价函数

  - $θ_1 = 1$

  ![image-20230601154047555](image\2.3斜率为0.png)

  - $θ_1 = 0.5$

  ![image-20230601154353554](image\2.3参数为0.5.png)

  

- Cost Function/$(θ_0 = 0)$时**J(θ1)图**

![image-20230601155055643](image\2.3CostFunction绘制.png)



### 2.4 Cost Function(2)

- **线性回归的代价函数图示**

![image-20230601155534758](image\image-20230601155534758-1685606140482-9.png)

- **Cost Function等高线图**

![image1](image\image-20230601160020658-1685606422352-11.png)

### 2.5 Gradient descent

keep changing  $θ_0,θ_1$ to reduce $J(θ_0,θ_1)$

- **Gradient descent algorithm**:
  - `:=` Assignment/赋值
  - `α` :learning rate/步长
- 同步更新：Simultaneous update

![image2](image\image-20230601163137576-1685608299690-13.png)

### 2.6 Summarize Gradient descent

- **步长太小**：梯度下降慢
- **步长太大**：可能越过最优解

![image3](image\image-20230601164139917-1685608900772-15.png)

- **达到局部最优解时**：参数不再变化，停止下降

![image4](image\image-20230601164422475-1685609064073-17.png)

- **越接近最优解，下降速度越慢**：无需修改步长，倒数会越来越小

![image-20230601164835777](image\image-20230601164835777-1685609317620-19.png)

### 2.7 Gradient descent for linear regression

- 利用梯度下降法最小化平方差代价函数：最重要的是编导项的确定

![image-20230601190523102](image\image-20230601190523102.png)

- 带入、求导

![image-20230601191155053](image\image-20230601191155053.png)

- 代入Gradient descent algorithm

![image-20230601191442227](image\image-20230601191442227.png)



## 3 Linear Algebra review

### 3.1 Matrices and vectors

vectors is $n \times 1$ matirx

### 3.2 Addition  and scalar multiplication

矩阵的加减法

### 3.3 Matrix-vector multiplication

矩阵向量相乘

**将实际问题转化为：矩阵向量相乘**

![image-20230601195655704](image\image-20230601195655704.png)

### 3.4 Matrix-matrix multiplication

$n \times m \ast m \times o \rightarrow n \times o$

**实际问题转化成：矩阵与矩阵相乘/多个假设回归函数**

![image-20230601200648653](image\image-20230601200648653.png)

### 3.5 Matrix mutiplication properties矩阵乘法特征

- 矩阵乘法**没有**交换律：$A×B ≠ B×A$

- 矩阵乘法**有**结合律：$A×(B×C) = (A×B)×C$

- **Identity Matrix**单位矩阵：
  - 对角线为1，其余为0
  - For any matrix：$A·I = I·A = A$

![image-20230601201854770](image\image-20230601201854770.png)

### 3.6 Inverse and transpose逆和转置

- **A×A的逆矩阵 = A的逆矩阵×A = I**

![image-20230601204252689](image\image-20230601204252689.png)

- **Matrix Transpose**矩阵的转置

![image-20230601204506614](image\image-20230601204506614.png)



## 4 Linear Regression with multiple variables

### 4.1 Multiple features(variables)

- **Notation**:
  - n：特征的数量
  - x^(i)^：第i行，既第i个特征向量
  - x^(i)^~j~：第i个特征向量的第j个特征值

![image-20230602084931086](image\image-20230602084931086.png)

- Multivariate linear regression transfer to Matrix Multiplication：多元线性回归问题转化为矩阵相乘

![image-20230602090101143](image\image-20230602090101143.png)

### 4.2 Gradient descent for multiple variables

![image-20230602090929826](image\image-20230602090929826.png)

### 4.3 Gradient descent in practice I:Feature Scaling特征缩放

- 比例缩放：**特征之间取值范围差异过大**会出现代价函数的等高线图偏移严重（太瘦或太胖）
- 比例缩放后：在进行梯度下降时下降的路径就不会左右摇摆，因此能够更快的收敛

![image-20230602092004612](image\image-20230602092004612.png)

- 缩放习惯

![image-20230602092508190](image\image-20230602092508190.png)

- **mean normalization**均值归一化
  - $\mu$：平均值
  - $s_1$：总数


$$
x_1 = \frac{x_1 - \mu}{s_1}
$$

![image-20230602094246313](image\image-20230602094246313.png)

### 4.4 Gradient descent in  practice Ⅱ: Learning rate $\alpha$

- **Making sure gradient descent is working correctly**

​		$J(\theta)$ should decrease after every iterations(迭代)

- 判断是否收敛，<$\varepsilon$的值

![image-20230602100332914](image\image-20230602100332914.png)

- **learning rate**太大可能冲过最小值，就会出现Gradient descent出错

![image-20230602100647929](image\image-20230602100647929.png)

- **Summary**
  - $\alpha$ 太小可能出现收敛较慢
  - $\alpha$ 太大可能$J(\theta)$在每次迭代时没有收敛

### 4.5 Features and polynomial regression多项式回归

根据不同情况做合适的特征选择

### 4.6 Normal equation（正态方程）

直接找到最优解的$\theta$使得的Cost function：$J(\theta)$最小

求偏导置0，解出参数的取值
$$
\theta = (X^TX)^{-1}X^Ty
$$
![image-20230602105311062](image\image-20230602105311062.png)

-  构建矩阵$X$

![image-20230602111332432](image\image-20230602111332432.png)

- gradient descent 和 normal equation 优缺点对比

|      Gradient Descent       |                      Normal Equation                      |
| :-------------------------: | :-------------------------------------------------------: |
|   需要选择合适的$\alpha$    |                  无需选择合适的$\alpha$                   |
|        需要多次迭代         |                       无需多次迭代                        |
| 当$n$很大的时候依然可以工作 | 需要计算$(X^TX)^{-1}$<br/>因此当$n$较大时矩阵那个运算较慢 |

![image-20230602111958133](image\image-20230602111958133.png)

### 4.7 Normal equation and non-invertibility(不可逆性)

- **$X^TX$不可逆**
  - 存在**Redandunt features**冗余特征时：行（列）向量线性相关时**Linearly dependent**（线性依赖）
    - 删除冗余的特征
  - Too many features ($m \le n$)特征数量大于训练集
    - 删除一些特征，或正则化

![image-20230602150413748](image\image-20230602150413748.png)

**相当于方程的数量小于未知数的数量，因此无解**



##  6 Logistic Regression

### 6.1 Classification

- 线性回归不适用于分类的问题的原因：噪声影响回归模型

![image-20230602155231126](image\image-20230602155231126.png)

- 使用**Logistic Regression**代替**Linear Regression**处理**Classification**

![image-20230602160724522](image\image-20230602160724522.png)

###  6.2 Hypothesis Representation假设表示

- **Logistic Regression Modle**：Sigmoid function/Logistic function

$$
g(z) = \frac{1}{1 + e^{-z}}
$$

![image-20230602161227394](image\image-20230602161227394.png)

### 6.3 Decision boundary决策界限

- **e.g: Logistic regression**
  - $g(z)\geq 0.5$    $when$   $z \geq 0$
  - $h_\theta (x) = g(\theta^T x) \geq 0.5$  $when$  $\theta^T x \geq 0$

![image-20230602162748703](image\image-20230602162748703.png)

- **Decision Boundary**:决策边界

![image-20230602163710723](image\image-20230602163710723.png)

- **non-linear decision boundaries:**非线性决策边界

![image-20230602164427315](image\image-20230602164427315.png)

### 6.4 Cost function

-  **线性回归存在的问题**：可能代价函数不是一个凸
  - 可能存在多个局部最优解
  - 因此在梯度下降时存在未收敛到全局最小值的情况

![image-20230602165604077](image\image-20230602165604077.png)

- 使用**Logistic regression**实现代价函数呈现凸图
  - 关注$z \in [0, 1]$因此图像为下图

- 公式含义：也就是公式$-\log{z} \in (0,1]$,  if  $ y=1$的函数意义
  - 当预测值和实际值都1时cost function=0
  - 当预测值和实际值一个为0，另一个为1时，cost function=$\infty$
  - 也就是当错误越大，那么惩罚也越大
- **Logistic regression cost function when** **y=1**

![image-20230602170024736](image\image-20230602170024736.png)

![image-20230603090805174](image\image-20230603090805174.png)

- **Logistic regression cost function when** **y=0**

![image-20230603091359638](image\image-20230603091359638.png)

### 6.5 Simplified cost function and gradient descent

- **单个训练样本的Cost function**

$$
Cost(h_\theta (x), y) = -y\log{(h_\theta (x))} - (1-y)\log{(1-h_\theta (x))}
$$

- **解释：**
  - IF $y=1:$  $Cost(h_\theta (x), y) = -\log{h_\theta (x)}$
  - IF $y=0:$  $Cost(H_\theta (x), y) = -\log{(1-h_\theta (x))}$  

 ![image-20230603092606339](image\image-20230603092606339.png)

- **Logistic regression cost function**
  - 概率论：**极大似然法**得来

$$
\begin{aligned}
J(\theta) &= \frac{1}{m}\sum^m_{i-1}{Cost(h_\theta(x^{(i)}), y^{(i)})}\\
		  &=  -\frac{1}{m}[\sum^m_{i-1}{y^{(i)}\log{h_\theta(x^{(i)}) + (1-y^{(i)})\log{(1-h_\theta(x^{(i)}))}}}]
\end{aligned}
$$

- 为了使得cost function最小，拟合出合适的$\theta$

![image-20230603100923179](image\image-20230603100923179.png)

- **Gradient Descent**

$$
J(\theta) = -\frac{1}{m}[\sum^m_{i-1}{y^{(i)}\log{h_\theta(x^{(i)}) + (1-y^{(i)})\log{(1-h_\theta(x^{(i)}))}}}]
$$

使得$J(\theta)$最小：

Repeat {

​				$\begin{aligned}\theta_j &:= \theta_j - \alpha\frac{\partial}{\partial \theta_j}{J(\theta)}\\ &:=\theta_j - \alpha\sum^m_{i-1}(h_\theta(x^{(i)} - y^{(i)})x_j^{(i)}) \end{aligned}$ 

}

- 刚好和线性回归的求导结果一样，但实际的意义不同，逻辑回归使用了sigomid映射函数





### 6.6 Advanced optimization



### 6.7 Mutli-class classification:One-vs-all

- eg:

  **Multiclass classification**

  email foldering/tagging:Work, Friends, Famliy, Hobby

  Medicine diagrams: Not ill, Cold, Flu

  Weather: Sunny, Cloudy, Rain, Snow

  - **y** can take on a small number of **discrete values**

- **one-versus-all** problem

  - take this into three separate binary classification problems
    $$
    h_\theta^{(i)}(x) = P(y = i |x;\theta)   (i = 1, 2, 3)
    $$
    

    ![image-20230621094105899](image\image-20230621094105899.png)



## 7 Regularization

### 7.1 The problem of overfitting

- **Example: Linear regression(housing prices)**

  - Underfit and Overfit

  -  	have **lot of features** and very **little trainning data** could cost Overfitting![image-20230621100347530](image\image-20230621100347530.png)

- **Addressing Overfitting**

  :one:reduce the number of features

  - Manually select which features to keep
  - Modle selection algorithm

  :two:Regularization

  - Keep all features, but reduce magnitude/values of parameters $\theta_j$

  - Works well when we have a lot of features, each of which contributes a bit to predicting $y$.



### 7.2 Cost function

**penalize**

![image-20230621102246784](image\image-20230621102246784.png)

- Small values for parameters $\theta_0, \theta_1, ..., \theta_n$
  - "Simpler"  hypothesis
  - Less prone to overfitting

- Housing:
  - Features:$x_1, x_2, ..., x_{100}$
  - Parameters:$\theta_0, \theta_1, \theta_2 ..., \theta_{100}$

$$
J(\theta) = \frac{1}{2m}[\sum_{i=1}^m({h_\theta(x^{(i)}) - y^{(i)})^2} + \lambda\sum_{i=1}^n{\theta_j^2}]
$$



# Deep Learning



### 1 Artificial Neural Network

BP神经网络：信号正向传播，**误差反向**传播

#### 神经元与激活函数：

**神经元：**

1.感知机：多个输入，加权计算后输出

2.Sigmoid函数：输入为0-1的任意值（正则化），输出也不再是$wx+b$而是$\sigma(wx+b)$
$$
\sigma(z) = \frac{1}{1+e^{-z}}
$$


损失函数：
$$
Loss = \frac{1}{n}\sum^{n}_{i=1}{|f_i-y_i|}
$$
当$\sigma(z)\approx0$或$\sigma(z)\approx1$时，Sigmoid神经元的输出跟感知器是很接近的。只有当w?x+b在一个适度的值，sigmoid神经元和感知器偏差才较大。

**激活函数：**

神经元的输入和输出之间具有函数关系，这个函数就称为激励函数。

**多层感知机：**

![image-20230709090150676](D:\miao\note\MachineLearning\MachineLearning\1MachineLearning\image-20230709090150676.png)



### 2 Convolution  Neural Network

#### 数据输入层/ Input layer

去均值：输入数据各个维度都中心化为0，把样本拉到坐标系原点上

归一化:

PCA/白化：PCA降维，数据各个特征轴上的幅度归一化



#### 卷积计算层/ CONV layer

深度：

步幅：

填充值：

卷积层的输出大小：$O = \frac{(W-K+2P)}{S}+1$

 O 是输出尺寸，K 是过滤器尺寸，P 是填充，S 是步幅

![img](D:\miao\note\MachineLearning\MachineLearning\1MachineLearning\v2-ae8a4d6f0ded77d731f179f361254db1_720w.gif)

#### ReLU激励层 / ReLU layer

激活函数用于解决**线性不可分**问题，提高对模型的表达能力

**ReLU:**
$$
f(x) = max(0,x), f(x)\in(0,+\infty)
$$
**Sigmoid:**
$$
g(x) = \frac{1}{1+e^{-x}},g(x)\in(0,1)
$$
使用ReLU激活后矩阵产生很多0，Sigmoid激活后矩阵中元素值都处于0-1之间

因此ReLU输出要比Sigmoid稀疏度高，特征少更易拟合，找规律更容易

**总结：ReLU具有稀疏化的功能**



#### 池化层 / Pooling layer

信息冗余

池化层夹在连续的卷积层中间，用于压缩数据和参数的体量，减少过拟合

**特征不变性**

**特征降维**

**防止过拟合**



#### 全连接层 / FC layer

将学到的**特征**表示**映射**到**样本的标记空间**

**分类器作用**
