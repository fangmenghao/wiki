---
title: UML基础知识
date: 2016-07-28 09:54
---

[TOC]

# 0x00 类 #

> ***类分三层***

- 第一层：类名，若类名是斜体-->说明该类是抽象类
- 第二层：类的特性，通常是字段和属性
- 第三层：类的操作，通常是方法或行为，+代表public | -代表private | #代表protected


> ***其他规则***

- 若一个类实现了一个接口，则该类上会有一个类似棒棒糖的图案

# 0x01 接口

# 0x02 关系线 #
> 类A：指向类B

> 类B：被箭头指着的类

#### 继承(Generalization)：空心三角形 + 实线

#### 实现接口(Realization)：空心三角形 + 虚线

#### 关联(association)：普通箭头 + 实线
> 在类A中引用类B，就是在类A中实例化了类B

> 在java中体现为类A有一个类B的成员属性 --> 大话设计模式p14

#### 聚合(aggregation)：空心菱形 + 实线 + 普通箭头
> 空心菱形在类A这一边

>聚合表示一种弱的‘拥有’关系，对象A可以包含对象B，但是对象B可以不是对象A的部分。

>就是对于对象A来说有一个数组，这个数组可以有很多个对象B，但是有几个对象B不一定会加入这个数组

#### 合成(Composition，组合)：实心菱形 + 实线 + 普通箭头
> 实心菱形在类A这一边

> 组合表示一种强的‘拥有’关系，类A必须包含类B，是整体和部分的关系，他们的生命周期相同

> 比如鸟有一对翅膀，假设类A为鸟，类B为翅膀，这里有基数问题，所以在类B这里有个数字是2，因为在类A中需要2个实例化的类B

#### 依赖(Dependency)：虚线 + 普通箭头
> 类A需要类B，依赖类B

> 通常类B表现为作为参数传入到类A的方法中

#### 其他
> - 基数：就是在连接类之间有数字进行标识，主类引用了几个其他类，体现在：`关联`、`聚合`、`合成`


# 0x03 图

#### 序列图
#### 状态图
#### 用例图(Use Case)
#### 活动图
