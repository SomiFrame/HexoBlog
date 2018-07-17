---
title: javascript-面向对象
date: 2018-07-17 13:24:08
tag:
- javascript
- object-oriented
- IIFE
---

# 面向对象概念
以下解释引用于MDN

> 面向对象编程是用抽象方式创建基于现实世界模型的一种编程模式。它使用先前建立的范例，包括模块化，多态和封装几种技术

> 相对于 “一个程序只是一些函数的集合，或简单的计算机指令列表。”的传统软件设计观念而言，面向对象编程可以看作是使用一系列对象相互协作的软件设计。 在 OOP 中，每个对象能够接收消息，处理数据和发送消息给其他对象。每个对象都可以被看作是一个拥有清晰角色或责任的独立小机器。

# 使用面向对象设计的目的

> 面向对象程序设计的目的是在编程中促进更好的灵活性和可维护性，在大型软件工程中广为流行。凭借其对模块化的重视，面向对象的代码开发更简单，更容易理解，相比非模块化编程方法, 它能更直接地分析, 编码和理解复杂的情况和过程。

# 对象创建方式
javascript的对象创建可一通过Object构造函数或者对象字面量的方式来创建单个对象.

> 字面量创建
```javascript
    var Person = {
        name: 'somi',
        age: '18',
        sex: 'male',
        sayHello: function(){
            console.log('hello everybody,my name is:'+this.name)
        }
    }
    Person.sayHello() // 'hello everybody,my name is:somi'
```
j
> 构造函数创建
```javascript
    function Person(){
        this.name = 'somi'
        this.age = '18'
        this.sex = 'male'
    }
    Person.prototype.sayHello = function() {
        console.log('hello everybody,my name is:'+this.name)
    }
    var person = new Person()
    person.sayHello()
```
> PS: 其实创建对象的方法不止这两种,例如还有 1. 工厂模式 2. 构造函数模式 3. 原型模式 4. 组合使用构造函数模式和原型模式 5. 动态原型模式 6. 寄生构造函数模式 7. 稳妥构造函数模式. 详细请见:


# JavaScript的继承
创建一个或多个类的专门版本类方式称为继承（Javascript只支持单继承）。
## 原型继承
## 类式继承
## 组合继承
## extend方法
