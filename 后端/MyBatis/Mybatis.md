# Mybatis

#### 1 keyProperty和useGeneratedKeys

##### 控制台报错：

```
No setter found for the keyProperty
```

##### 原因：

`useGeneratedKeys`：MyBatis使用JDBC的`useGeneratedKeys`方法来取出数据库内部生成的主键（自增后的值）

`keyProperty`：是唯一能够识别对象的属性，对应的是实体类的属性。MyBatis会使用`useGeneratedKeys`的返回值设置它的值。

由于这里的使用的insert方法，传入的数据中并没有自增的属性id，所以在取出`useGeneratedKeys`的返回值给`keyProperty`赋值时就会报错。

##### 解决方法：

去除insert标签中的keyProperty属性

[参考]([(140条消息) 关于Mybatis中keyProperty属性_学习路上的朱某人的博客-CSDN博客](https://blog.csdn.net/qq_39210750/article/details/108248320))