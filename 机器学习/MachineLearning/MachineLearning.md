---
typora-copy-images-to: ./
---

# Machine Learning

机器学习笔记，[B站吴恩达老师视频](https://www.bilibili.com/video/BV164411S78V/?spm_id_from=333.999.0.0)



## 1 Supervised Learning AND Unsupervised Learning

### 1.3 Supervised Learning

“right answer”given 有标签

- **Pegression Problem** :Predict continuous valued Output(Price)

![image-20230601110803928](.\Pegression(house_price_predict).png)

- **Classificaton Problem**:Discrete valued Output(0 or 1)

  - one feature

  ![image-20230601111053713](.\Classification(one_feature).png)

  - two feature

![Classification(two_features)](.\Classification(two_features).png)

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

![image-20230601143652259](.\2.1Notation.png)

![image-20230601144432420](.\2.1linear_regression.png)

### 2.2 Cost Function

- **Cost Function/平方误差代价函数**：

计算使得**训练集中\*预测值-实际值\*的平方总和的平均值**最小的两个参数

![image-20230601145905596](.\Cost Function.png)

### 2.3 Cost Function(1)

- **简化**

![image-20230601150334970](.\2.3CostFunction简化.png)

- 回归函数和代价函数

  - θ1=1

  ![image-20230601154047555](.\2.3斜率为0.png)

  - θ1=0.5

  ![image-20230601154353554](.\2.3参数为0.5.png)

  

- Cost Function/θ0=0时**J(θ1)图**

![image-20230601155055643](.\2.3CostFunction绘制.png)



### 2.4 Cost Function(2)

- **线性回归的代价函数图示**

![image-20230601155534758](.\image-20230601155534758-1685606140482-9.png)

- **Cost Function等高线图**

![代价函数等高线图](.\image-20230601160020658-1685606422352-11.png)

### 2.5 Gradient descent

keep changing  θ0,θ1 to reduce J(θ0,θ1)

- **Gradient descent algorithm**:
  - `:=` Assignment/赋值
  - `α` :learning rate/步长
- 同步更新：Simultaneous update

![梯度下降算法](.\image-20230601163137576-1685608299690-13.png)

### 2.6 Summarize Gradient descent

- **步长太小**：梯度下降慢
- **步长太大**：可能越过最优解

![步长的取值](.\image-20230601164139917-1685608900772-15.png)

- **达到局部最优解时**：参数不再变化，停止下降

![梯度下降达到最优解时的状态](.\image-20230601164422475-1685609064073-17.png)

- **越接近最优解，下降速度越慢**：无需修改步长，倒数会越来越小

![image-20230601164835777](D:\miao\note\机器学习\MachineLearning\image-20230601164835777-1685609317620-19.png)

### 2.7 Gradient descent for linear regression
