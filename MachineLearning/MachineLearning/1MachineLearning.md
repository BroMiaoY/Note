---
typora-copy-images-to: https://github.com/BroMiaoY/Note/blob/main/MachineLearning/MachineLearning/
---

# Machine Learning

机器学习笔记，[B站吴恩达老师视频](https://www.bilibili.com/video/BV164411S78V/?spm_id_from=333.999.0.0)

https://github.com/BroMiaoY/Note/blob/main/MachineLearning/MachineLearning/

## 1 Supervised Learning AND Unsupervised Learning

### 1.3 Supervised Learning

“right answer”given 有标签

- **Pegression Problem** :Predict continuous valued Output(Price)

![image-20230601110803928](Pegression(house_price_predict).png)

- **Classificaton Problem**:Discrete valued Output(0 or 1)

  - one feature

  ![image-20230601111053713](Classification(one_feature).png)

  - two feature

![Classification(two_features)](Classification(two_features).png)

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

![image-20230601143652259](2.1Notation.png)

![image-20230601144432420](2.1linear_regression.png)

### 2.2 Cost Function

- **Cost Function/平方误差代价函数**：

计算使得**训练集中\*预测值-实际值\*的平方总和的平均值**最小的两个参数

![image-20230601145905596](Cost Function.png)

### 2.3 Cost Function(1)

- **简化**

![image-20230601150334970](2.3CostFunction简化.png)

- 回归函数和代价函数

  - $θ_1 = 1$

  ![image-20230601154047555](2.3斜率为0.png)

  - $θ_1 = 0.5$

  ![image-20230601154353554](2.3参数为0.5.png)

  

- Cost Function/$(θ_0 = 0)$时**J(θ1)图**

![image-20230601155055643](2.3CostFunction绘制.png)



### 2.4 Cost Function(2)

- **线性回归的代价函数图示**

![image-20230601155534758](image-20230601155534758-1685606140482-9.png)

- **Cost Function等高线图**

![image1](image-20230601160020658-1685606422352-11.png)

### 2.5 Gradient descent

keep changing  $θ_0,θ_1$ to reduce $J(θ_0,θ_1)$

- **Gradient descent algorithm**:
  - `:=` Assignment/赋值
  - `α` :learning rate/步长
- 同步更新：Simultaneous update

![image2](image-20230601163137576-1685608299690-13.png)

### 2.6 Summarize Gradient descent

- **步长太小**：梯度下降慢
- **步长太大**：可能越过最优解

![image3](image-20230601164139917-1685608900772-15.png)

- **达到局部最优解时**：参数不再变化，停止下降

![image4](image-20230601164422475-1685609064073-17.png)

- **越接近最优解，下降速度越慢**：无需修改步长，倒数会越来越小

![image-20230601164835777](image-20230601164835777-1685609317620-19.png)

### 2.7 Gradient descent for linear regression

- 利用梯度下降法最小化平方差代价函数：最重要的是编导项的确定

![image-20230601190523102](image-20230601190523102.png)

- 带入、求导

![image-20230601191155053](image-20230601191155053.png)

- 代入Gradient descent algorithm

![image-20230601191442227](image-20230601191442227.png)



## 3 Linear Algebra review

### 3.1 Matrices and vectors

vectors is $n \times 1$ matirx

### 3.2 Addition  and scalar multiplication

矩阵的加减法

### 3.3 Matrix-vector multiplication

矩阵向量相乘

**将实际问题转化为：矩阵向量相乘**

![image-20230601195655704](image-20230601195655704.png)

### 3.4 Matrix-matrix multiplication

$n \times m \ast m \times o \rightarrow n \times o$

**实际问题转化成：矩阵与矩阵相乘/多个假设回归函数**

![image-20230601200648653](image-20230601200648653.png)

### 3.5 Matrix mutiplication properties矩阵乘法特征

- 矩阵乘法**没有**交换律：$A×B ≠ B×A$

- 矩阵乘法**有**结合律：$A×(B×C) = (A×B)×C$

- **Identity Matrix**单位矩阵：
  - 对角线为1，其余为0
  - For any matrix：$A·I = I·A = A$

![image-20230601201854770](image-20230601201854770.png)

### 3.6 Inverse and transpose逆和转置

- **A×A的逆矩阵 = A的逆矩阵×A = I**

![image-20230601204252689](image-20230601204252689.png)

- **Matrix Transpose**矩阵的转置

![image-20230601204506614](image-20230601204506614.png)



## 4 Linear Regression with multiple variables

### 4.1 Multiple features(variables)

- **Notation**:
  - n：特征的数量
  - x^(i)^：第i行，既第i个特征向量
  - x^(i)^~j~：第i个特征向量的第j个特征值

![image-20230602084931086](image-20230602084931086.png)

- Multivariate linear regression transfer to Matrix Multiplication：多元线性回归问题转化为矩阵相乘

![image-20230602090101143](image-20230602090101143.png)

### 4.2 Gradient descent for multiple variables

![image-20230602090929826](image-20230602090929826.png)

### 4.3 Gradient descent in practice I:Feature Scaling特征缩放

- 比例缩放：**特征之间取值范围差异过大**会出现代价函数的等高线图偏移严重（太瘦或太胖）
- 比例缩放后：在进行梯度下降时下降的路径就不会左右摇摆，因此能够更快的收敛

![image-20230602092004612](image-20230602092004612.png)

- 缩放习惯

![image-20230602092508190](image-20230602092508190.png)

- **mean normalization**均值归一化
  - $\mu$：平均值
  - $s_1$：总数


$$
x_1 = \frac{x_1 - \mu}{s_1}
$$

![image-20230602094246313](image-20230602094246313.png)

### 4.4 Gradient descent in  practice Ⅱ: Learning rate $\alpha$

- **Making sure gradient descent is working correctly**

​		$J(\theta)$ should decrease after every iterations(迭代)

- 判断是否收敛，<$\varepsilon$的值

![image-20230602100332914](image-20230602100332914.png)

- **learning rate**太大可能冲过最小值，就会出现Gradient descent出错

![image-20230602100647929](image-20230602100647929.png)

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
![image-20230602105311062](image-20230602105311062.png)

-  构建矩阵$X$

![image-20230602111332432](image-20230602111332432.png)

- gradient descent 和 normal equation 优缺点对比

|      Gradient Descent       |                      Normal Equation                      |
| :-------------------------: | :-------------------------------------------------------: |
|   需要选择合适的$\alpha$    |                  无需选择合适的$\alpha$                   |
|        需要多次迭代         |                       无需多次迭代                        |
| 当$n$很大的时候依然可以工作 | 需要计算$(X^TX)^{-1}$<br/>因此当$n$较大时矩阵那个运算较慢 |

![image-20230602111958133](image-20230602111958133.png)

### 4.7 Normal equation and non-invertibility(不可逆性)

- $X^TX$不可逆问题

