---
title: 12个非常有用的javascript写法
date: 2018-07-06 15:38:11
tag: 
- javascript
- js
- hack
---
> **声明**: 此文章翻译于外国博客的文章

- 源链接: [12 Extremely Useful Hacks for JavaScript](https://blog.jscrambler.com/12-extremely-useful-hacks-for-javascript/)
- 原作者: [Caio Ribeiro Pereira](https://blog.jscrambler.com/author/caio-pereira)
- 翻译: [粟米somi](https://somiframe.github.io)

****
![JsHack.png](https://blog.jscrambler.com/content/images/2016/12/12-javascripts-hacks.png)

我将会在这篇文章分享12个很有用的JavaScript写法.使用这些写法将能简化和优化你代码.所以,现在我们开始学习吧!

# 1) 使用 !! 运算符来强制为布尔值(Boolean)
有时候我们会遇到一些需要判断一个变量是否存在或者是否存在值然后跟这个判断运行相应的逻辑代码(例如当一个变量没有赋值时为真否则为假).为了能实现这种验证判断,你可以使用```!! ```(双重否定运算符)如``` !!variable ```,这样就可以把任何类型的数据转换为布尔值,当这个variable(变量)为:``` 0 ``` ``` null ``` ``` undefined ``` ``` NaN ``` 的时候会返回 ``` false ```,其他情况则返回true.现在我们就在实践中了解它,请看下面的例子:
```javascript
function Account(cash) {
    this.cash = cash;
    this.hasMoney = !!cash;
}
var account = new  Account(100.50)
console.log(account.cash) //100.50
console.log(account.hasMoney) //true

var  emptyAccount = new  Account(0)
console.log(emptyAccount.cash) //0
console.log(emptyAccount.hasMoney) //false
```
# 2) 使用 + 运算符强制转换为数字类型
这个写法太棒了!而且非常容易实现,但是它只对字符串类型有效,如果是非字符串类型的话会返回```NaN```(Not a Number),请看下面的例子:
```javascript
function toNumber(strNumber) {
    return +strNumber
}
console.log("1234") //1234
console.log("ABC") //NaN
```
这个写法同样可以对```Date```起作用,下面的例子将返回一个时间戳数字:
```javascript
   console.log(+new Date())  //1461288164385
```

# 3) 短路条件语句
如果你看到下面类似的代码:
```javascript
if(conected) {
    login()
}
```
你可以通过使用短路判断来简化以上的代码.例如上面的例子可以改写为一下形式:
```javascript
    connected && login()
```

# 4) 使用 || 运算符实现带默认值的赋值
今天的es6版本已经添加了默认值参数的支持.为了在旧版本的JavaScript中模拟出带默认值参数的效果,你可以使用 ```||``` (或运算符) 通过添加默认值到或运算的第二个参数中.如果第一个参数为空值则第二个参数将作为默认值赋值给变量.下面是我们的使用例子:
```javascript
function User(name, age) {  
    this.name = name || "Oliver Queen";
    this.age = age || 27;
}
var user1 = new User();  
console.log(user1.name); // Oliver Queen  
console.log(user1.age); // 27

var user2 = new User("Barry Allen", 25);  
console.log(user2.name); // Barry Allen  
console.log(user2.age); // 25 
```

# 5) 遍历数组的时候预缓存数组的长度(array.length)
这个较巧非常简单,而且当在循环遍历大型数组的时候会引起很大的性能影响.基本上,很大的一部分同学们都会这样遍历一个数组:
```javascript
for (var i = 0; i < array.length; i++) {  
    console.log(array[i]);
}
```
以上写法如果你是用来遍历长度较少的数组的时候是可以接受的,但是如果你遍历的是大型数组的话,这段代码实质上是在每次遍历的时候都会重新计算获取数组的长度这样会因此效率上的降低.为了便面这种情况,你可以在循环逻辑前面添加缓存数组的逻辑(即把数组长度赋值给一个新变量)而不是每次循环遍历的时候都要调用```array.length```:
```javascript
var length = array.length;  
for (var i = 0; i < length; i++) {  
    console.log(array[i]);
}
```
我们还可以进一步的简化上面的代码:
```javascript
for (var i = 0, length = array.length; i < length; i++) {  
    console.log(array[i]);
}
```

# 6) 检测对象中的属性

这个技巧非常有用当你需要检测对象中是否存在某个或某些属性和不想运行对象中不存在的属性或者方法的时候.例如当你考虑需要做一些浏览器的兼容性的时候例如兼容ie8一下的浏览器?(哎 ......),你想使用 ```document.querySelector()``` 去获取某些dom元素.然而在旧版本的ie浏览器中这个方法是不存在的,所以为了检测这个方法的存在性,你可以使用```in``` 操作符,请看下面的例子:
```javascript
if ('querySelector' in document) {  
    document.querySelector("#id");
} else {
    document.getElementById("id");
}
```
上面的代码,如果遇到 querySelector 方法不存在于document对象的时候,我们可以使用 getElementById 方法来做兼容性回退方案

# 7) 快速获取数组的最后一项值
```Array.prototype.slice(begin, end)``` 可以根据传进来的参数情况来切割数组并返回新的数组,但是当你不设置第二个参数的时候默认值则是该数组的最大长度,我相信很少人会知道这个方法的参数是可以传负数的,当你把第一个参数设置为负数的时候,你会得到这个数组的最后一个元素:
```javascript
var array = [1, 2, 3, 4, 5, 6];  
console.log(array.slice(-1)); // [6]  
console.log(array.slice(-2)); // [5,6]  
console.log(array.slice(-3)); // [4,5,6]  
```
# 未完待续............