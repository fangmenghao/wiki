---
title: 设计模式总结
date: 2017-07-28 12:21
---

[TOC]

设计模式总结
=========================


设计原则
----------
#### 单一职责原则(Single Responsibility Principle, SRP)
> 介绍：对于一个类，应该只有一个引起它变化的原因

#### 开放-封闭原则(Open-Closed Principle, OCP)
> 介绍：软件实体（类、模块、函数等等）应该可以扩展，不可以修改

> 就是把弄一个抽象类或者接口，让很多新类继承或实现即可，我们只需要引用抽象类即可

#### 依赖倒转原则(Dependence  Inversion Principle, DIP)
> 介绍：抽象不应该依赖细节，细节应该依赖抽象。说白了就是`针对接口编程，不要对实现编程`

> 高层模块不应该依赖底层模块，两个都依赖抽象模块。它们都应该依赖一个抽象类或者接口

> 内存、硬盘等都是针对接口编程，因为换内存、硬盘不需要更换主板

#### 里氏代换原则(Liskov Substitution Principle, LSP)
> 介绍：子类型必须能够替换掉它们的父类型

> 要求：
- 子类的所有方法都在父类中声明，即子类必须实现所有父类的方法
- 尽量把父类设计为抽象类或接口，这样只要新增子类就可以了扩展了

> ***它是开闭原则的具体实现之一***

#### 接口隔离原则(Interface Segregation Principle, ISP)
> 介绍：使用多个专门的接口，而不使用单一的总接口

#### 合成复用原则(Composite Reuse Principle, CRP)
> 介绍：尽量使用对象组合，而不是继承来达到复用的目的

#### 迪米特法则(Law of Demeter, LoD)
> 介绍：一个软件实体应当尽可能少地与其他实体发生相互作用，又名`最少知识原则`

> 关键

- 强调类之间的松耦合。如果一个类要调用另一个类的方法，尽量通过第三方转发这个调用

#### 联系

- 开闭原则是目标，里氏代换原则是基础，依赖倒转原则是手段

设计模式
---------
## 一、创建型模式
#### 0x01 简单工厂模式`Simple Factory Pattern`
> 介绍

定义一个用于创建对象的类，包含一个静态方法，该方法能返回一个对象

> 实现

方法一：通过一个静态方法，参数是String类型，通过switch或if判断返回一个工厂

> 缺点

- 违背了`开闭原则`，每次新增子类都需要修改简单工厂模式内的逻辑。于是需要工厂方法模式

> 关键

- 简单工厂的switch或者if逻辑可以通过反射技术来去除


#### 0x02 工厂方法模式`Factory Method Pattern`
> 介绍

定义一个用于创建对象的接口，让子类决定实例化哪一个类，工厂方法使一个类的实例化延迟到子类进行。

> 优点

- 符合`开闭原则`，每次只要新增工厂子类以及具体产品即可

#### 0x03 抽象工厂模式`Abstract  Factory Pattern`
> 介绍

提供一个创建一系列相关或相互依赖对象的接口，而无需指定它们具体的类

> 关键

- 抽象工厂模式会导致维护修改的时候要改许多类，所以我们可以去除繁杂的工厂类，用简单工厂

#### 0x04 单例模式`Singleton Pattern`
> 介绍

保证一个类仅有一个实例，并提供一个访问它的全局访问点

> 关键

- `该类的实例只有1个，只有1个，只有1个。所有代码都为了让该类的实例只有一个`

- 私有化构造器方法

- 多线程问题：多线程同时访问的时候还是会创建多个实例，需要锁机制

- 双重锁定：先判断实例是否为空，再加锁

- `饿汉` 和 `懒汉`

#### 0x05 原型模式`Prototype Pattern`
> 介绍

用原型实例指定创建对象的种类，并且通过拷贝这些原型创建新的对象。

> 讲人话

原型模式就是从一个对象再创建另一个可定制的对象，而且不需要知道任何创建的细节。

> 关键

- 关键就是需要一个抽象方法`public abstract $CLASSNAME Clone()`

- 对于对象属性的克隆，要注意强弱


#### 0x06 建造者模式`Builder Pattern`
> 介绍

将一个复杂对象的构建与它的表示分离，使得同样的构建过程可以创建不同的表示

> 关键

- 因为建造一个复杂对象需要很多步骤，在这个过程中我们不希望有步骤被遗忘。所以，我们需要将这些步骤都写成`抽象方法`

> 角色

- 建造者(Builder)，抽象类，有许多子类继承
- 指挥者(Director)
- 产品(放在Builder里面)

---

## 二、结构型模式
#### 0x01 适配器模式`Adapter Pattern`
> 介绍

将一个类的接口转换成客户希望的另外一个接口，适配器模式使得原来不兼容的接口能一起工作

> 使用原因

- 已存在的类，但它的接口，也就是它的方法和你的要求不相同时
- 双方都不太容易修改各自代码的时候

> 使用场合

- 写代码的开发人员有很多，后期维护的时候，会因为代码的不同需要适配
- 开发第三方接口的时候
- 该模式是在没有办法的情况下才最后使用的。良好的设计才是重点

#### 0x02 桥接模式`Bridge  Pattern`
> 介绍

将抽象部分和它的实现部分分离，使它们可以独立变化

> 使用原因

- 当使用继承导致大量的类增加，并且不符合`开闭原则`的时候

> 个人理解

就是将上下级的树形关系变成了平等的互利互惠关系

#### 0x03 组合模式`Composite  Pattern`
> 介绍

将对象组合成树形结构以表示‘部分-整体’的层次结构，组合模式使得用户对单个对象和组合对象的使用具有一致性

> 使用场合

- 需求中是体现部分与整体层次的结构时
- 希望用户忽略组合对象与单个对象的不同，统一使用组合结构中的所有对象

> 关键

- 叶子节点没有下一级，所以继承组合类的它不需要完成`添加`和`移除`等方法

> 角色

- 组合类
- 叶子节点
- 枝节点

#### 0x04 装饰模式`Decorator  Pattern`
> 介绍

动态地给一个对象添加一些额外的职责，就增加功能来说，装饰模式比生成子类更为灵活

#### 0x05 外观模式`Facade  Pattern`
> 介绍

为子系统中的一组接口提供一个一致的界面，此模式定义了一个高层接口，这个接口使得这一子系统更加容易使用

> 优点

- 体现了`依赖倒转原则`和`迪米特原则`

> 使用场合

- `设计初期`，有意识的将不同的两个层分离。比如在数据访问层和业务逻辑层之间建立外观。
- `开发阶段`，子系统往往因为不断的重构而复杂，会产生很多小类，给调用带来麻烦，增加外观可以提供一个接口，降低它们之间的依赖。
- `维护阶段`，可能遗留系统难以维护和扩展，可以提供一个简单外观接口让新系统来使用。

#### 0x06 享元模式`Flyweight  Pattern`
> 介绍

运用共享技术有效地支持大量细粒度的对象

> 使用场合

- 如果一个应用程序使用了大量对象，造成了大量存储开销的时候

> 说人话

> 具体应用

- 五子棋、围棋等，服务器要实例化大量棋子，使用享元只需要几个就够了。

就是共享代码，然后怎么共享，外部内部等

#### 0x07 代理模式`Proxy  Pattern`
> 介绍

为其他对象提供一种代理以控制对这个对象的访问

> 使用场合

- 远程代理
- 虚拟代理
- 安全代理
- 智能指引

---

## 三、行为型模式
#### 0x01 职责链模式`Chain  of Responsibility Pattern`
> 介绍

使多个对象都有机会处理请求，从而避免请求的发送者和接受者之间的耦合关系。将这个对象连成一条链，并沿着这条链传递该请求。直到有一个对象处理它为止。

> 关键

- 如果一个处理者无法处理请求，则该请求会沿着链一直传递到能处理的地方
- 最终处理者无需下一个处理者引用

#### 0x02 命令模式`Command  Pattern`
> 介绍

将一个请求封装为一个对象，从而使你可用不同的请求对客户进行参数化，对请求或记录请求日志，以及支持可撤销行为。

> 优点

- 容易设计一个命令队列
- 可将命令记录日志
- 允许接受请求的请求者否决请求
- 撤销和重做请求简单
- 容易扩展，添加新的命令类
- 分离了操作请求和知道怎么操作

#### 0x03 解释器模式`Interpreter  Pattern`
> 介绍

给定一个语言，定义它的文法的一种表示，并定义一个解释器，这个解释器使用该表示来解释语言中的句子。

#### 0x04 迭代器模式`Iterator  Pattern`
> 介绍

提供一种方法顺序访问一个聚合对象中的各个元素，而又不暴露该对象的内部表示

#### 0x05 中介者模式`Mediator  Pattern`
> 介绍

用一个中介对象来封装一系列的对象交互，中介者使各对象不需要显示地相互引用，从而使其耦合松散，而且可以独立地改变它们之间的交互。

> 使用场合

- 应用与一组对象以定义良好但是复杂的方式进行通信的场合

- 想定制一个分布在多个类中的行为，又不想生成太多的子类的场合

#### 0x06 备忘录模式`Memento  Pattern`
> 介绍

在不破坏封装性的前提下，捕获一个对象的内部状态，并在该对象之外保存这个状态，这样以后就可将该对象恢复到原先保存的状态

> 角色

- 发起人(Originator)
- 备忘录(Memento)
- 管理者(Caretaker)

> 使用场合

- 适用于功能复杂，但需要维护或记录属性历史的类
- 保存的属性只是众多属性中的一部分时
- 要实现撤销命令的时候，可以用备忘录模式来存储可撤销操作的状态

> 优点

- 可以把复杂的对象内部信息对其他的对象屏蔽起来。


#### 0x07 观察者模式`Observer  Pattern`
> 介绍

定义了一种一对多的依赖关系，让多个观察者对象同时监听某一个主题对象，这个主题对象在状态发生变化时，会通知所有观察者对象，使它们能更新自己。

> 优点

- 依赖与抽象，体现了`依赖倒转原则`

> 使用原因

- 当一个对象的改变同时需要改变其他多个对象的时候

> 使用场合

#### 0x08 状态模式`State  Pattern`
> 介绍

当一个对象的内在状态改变时允许改变其行为，这个对象看起来像是改变了其类

> 使用场合

- 当一个对象的行为取决于它的状态，并且它必须在运行时刻根据状态改变它的行为时

#### 0x09 策略模式`Strategy  Pattern`
#### 0x0A 模板方法模式`Template  Method Pattern`
> 介绍

定义一个操作中的算法骨架，而将一些步骤延迟到子类中。模板方法使得子类可以不更改一个算法的结构即可重新定义该算法的某些特定步骤

> 特点

- 模板方式通过把不变的行为放在超类中，去除子类中的重复代码。

> 使用原因

- 当多个子类中出现了重复的代码的的时候，把这些重复的代码放在超类中

#### 0x0B 访问者模式`Visitor  Pattern`
> 介绍

表示一个作用于某对象结构中的各元素的操作，它使你可以在不改变各元素的类的前提下定义作用于这些元素的新操作

> 使用场合

- 适用于数据结构相对稳定的系统