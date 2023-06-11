---
typora-copy-images-to: ./
---

# ML实验中遇到的问题



### 1 matplotlib画图中文无法显示的问题

添加以下代码

```python
# 设置matplotlib正常显示中文和负号
matplotlib.rcParams['font.sans-serif']=['SimHei']   # 用黑体显示中文
matplotlib.rcParams['axes.unicode_minus']=False     # 正常显示负号
```



### 2 matplotlib图与图之间重合的问题

```python
fig.tight_layout(pad=0, w_pad=0.4, h_pad=0.4)
```

pad：与画布边缘的距离

w_pad：图与图之间的水平距离

h_pad：图与图之间的垂直距离

**注意：代码要放在绘制完子图之后，否则无法生效！！！**

如下所示：

```python
import matplotlib.pyplot as plt
import matplotlib

# 设置matplotlib正常显示中文和负号
matplotlib.rcParams['font.sans-serif']=['SimHei']   # 用黑体显示中文
matplotlib.rcParams['axes.unicode_minus']=False     # 正常显示负号

fig = plt.figure()
fig.set(alpha = 0.2)

plt.subplot2grid((2,3),(0,0))             # 在一张大图里分列几个小图
data_train.Survived.value_counts().plot(kind='bar')# 柱状图
plt.title(u"获救情况 (1为获救)") # 标题
plt.ylabel(u"人数")

plt.subplot2grid((2,3),(0,1))
data_train.Pclass.value_counts().plot(kind="bar")
plt.ylabel(u"人数")
plt.title(u"乘客等级分布")

plt.subplot2grid((2,3),(0,2))
plt.scatter(data_train.Survived, data_train.Age)
plt.ylabel(u"年龄")                         # 设定纵坐标名称
plt.grid(which='major', axis='y')
plt.title(u"按年龄看获救分布 (1为获救)")


plt.subplot2grid((2,3),(1,0), colspan=2)
data_train.Age[data_train.Pclass == 1].plot(kind='kde')
data_train.Age[data_train.Pclass == 2].plot(kind='kde')
data_train.Age[data_train.Pclass == 3].plot(kind='kde')
plt.xlabel(u"年龄")# plots an axis lable
plt.ylabel(u"密度")
plt.title(u"各等级的乘客年龄分布")
plt.legend((u'头等舱', u'2等舱',u'3等舱'),loc='best') # sets our legend for our graph.


plt.subplot2grid((2,3),(1,2))
data_train.Embarked.value_counts().plot(kind='bar')
plt.title(u"各登船口岸上船人数")
plt.ylabel(u"人数")

# 解决图与图之间重合的问题
fig.tight_layout(pad=0, w_pad=0.4, h_pad=0.4)
plt.show()
```



### 3 matplotlib删除原有x、y轴和刻度

matplotlib删除原有x、y轴和刻度

```python
plt.xticks([])  # 去x坐标刻度
plt.yticks([])  # 去y坐标刻度
plt.axis('off')  # 去坐标轴
```



### 4 遇到缺失值的几种处理方法

遇到缺失值的几种处理方法

- 如果缺值的样本占总数比例极高，我们可能就直接舍弃了，作为特征加入的话，可能反倒带入noise，影响最后的结果了
- 如果缺值的样本适中，而该属性非连续值特征属性(比如说类目属性)，那就把NaN作为一个新类别，加到类别特征中
- 如果缺值的样本适中，而该属性为连续值特征属性，有时候我们会考虑给定一个step(比如这里的age，我们可以考虑每隔2/3岁为一个步长)，然后把它离散化，之后把NaN作为一个type加到属性类目中。
- 有些情况下，缺失的值个数并不是特别多，那我们也可以试着根据已有的值，拟合一下数据，补充上。
- [原文链接](https://blog.csdn.net/han_xiaoyang/article/details/49797143)