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

# 使用 !! 运算符来强制为布尔值(Boolean)
有时候我们会遇到一些需要判断一个变量是否存在或者是否存在值然后跟这个判断运行相应的逻辑代码(例如当一个变量没有赋值时为真否则为假).为了能实现这种验证判断,你可以使用 ` !! ` (双重否定运算符)如
 ` !!variable ` ,这样就可以把任何类型的数据转换为布尔值,当这个variable(变量)为: ` 0 ` ` null ` ` undefined ` ` NaN ` 的时候会返回 ` false ` ,其他情况则返回true.现在我们就在实践中了解它,请看下面的例子:
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
# 使用 + 运算符强制转换为数字类型
这个写法太棒了!而且非常容易实现,但是它只对字符串类型有效,如果是非字符串类型的话会返回` NaN `(Not a Number),请看下面的例子:
```javascript
function toNumber(strNumber) {
    return +strNumber
}
console.log("1234") //1234
console.log("ABC") //NaN
```
这个写法同样可以对` Date `起作用,下面的例子将返回一个时间戳数字:
```javascript
   console.log(+new Date())  //1461288164385
```

# 短路条件语句
如果你看到下面类似的代码:
```javascript
if(conected) {
    login()
}
```
你可以通过使用短路判断来简化以上的代码.例如上面的例子可以改写为一下形式:
```javascript
    connected && login()
```

# 使用 || 运算符实现带默认值的赋值
今天的es6版本已经添加了默认值参数的支持.为了在旧版本的JavaScript中模拟出带默认值参数的效果,你可以使用 ` || ` (或运算符) 通过添加默认值到或运算的第二个参数中.如果第一个参数为空值则第二个参数将作为默认值赋值给变量.下面是我们的使用例子:
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

# 遍历数组的时候预缓存数组的长度(array.length)
这个较巧非常简单,而且当在循环遍历大型数组的时候会引起很大的性能影响.基本上,很大的一部分同学们都会这样遍历一个数组:
```javascript
for (var i = 0; i < array.length; i++) {  
    console.log(array[i]);
}
```
以上写法如果你是用来遍历长度较少的数组的时候是可以接受的,但是如果你遍历的是大型数组的话,这段代码实质上是在每次遍历的时候都会重新计算获取数组的长度这样会因此效率上的降低.为了避免这种情况,你可以在循环逻辑前面添加缓存数组的逻辑(即把数组长度赋值给一个新变量)而不是每次循环遍历的时候都要调用` array.length `:
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

# 检测对象中的属性
这个技巧非常有用当你需要检测对象中是否存在某个或某些属性和不想运行对象中不存在的属性或者方法的时候.例如当你考虑需要做一些浏览器的兼容性的时候例如兼容ie8一下的浏览器?(哎 ......),你想使用 ` document.querySelector() ` 去获取某些dom元素.然而在旧版本的ie浏览器中这个方法是不存在的,所以为了检测这个方法的存在性,你可以使用` in ` 操作符,请看下面的例子:
```javascript
if ('querySelector' in document) {  
    document.querySelector("#id");
} else {
    document.getElementById("id");
}
```
上面的代码,如果遇到 `querySelector` 方法不存在于document对象的时候,我们可以使用 `getElementById` 方法来做兼容性回退方案

# 快速获取数组的最后一项值
` Array.prototype.slice(begin, end) ` 可以根据传进来的参数情况来切割数组并返回新的数组,但是当你不设置第二个参数的时候默认值则是该数组的最大长度,我相信很少人会知道这个方法的参数是可以传负数的,当你把第一个参数设置为负数的时候,你会得到这个数组的最后一个元素:
```javascript
var array = [1, 2, 3, 4, 5, 6];  
console.log(array.slice(-1)); // [6]  
console.log(array.slice(-2)); // [5,6]  
console.log(array.slice(-3)); // [4,5,6]  
```

# 数组截断
这个写法很有趣,通过设置数组的长度来截取某一部分的内容.例如你现在有一个含有10个元素的数组,但是你只想要前五个元素,那么你可以通过设置该数组的长度为5`array.length=5`来截取前五个元素.请看下面的例子:
```javascript
var array = [1,2,3,4,5,6]
console.log(array.lenght) //6
array.length = 3
console.log(array.length) // 3
console.log(array) // [1,2,3]
```

# 替换所有匹配的内容 
`String.replace`方法允许我们通过使用String和Regex(正则表达式)来替换字符串,原本这个方法只能替换第一个匹配的字符串.但是你可以模拟`replaceAll()`方法通过添加`/g`到正则表达式的后面:
```javascript
var string = "john john"
console.log(string.replace(/hn/,"ana")) // "joana john"
console.log(string.replace(/hn/g,"ana")) // "joana joana"
```

# 合并数组
如果你需要合并两个数组,你可以使用`Array.concat()`方法:
```javascript
var array1 = [1,2,3]
var array2 = [4,5,6]
console.log(array1.concat(array2)) // [1,2,3,4,5,6]
```
然而,这并不是最适合去合并两个数组的方式,因为这样合并会消耗内存来创建一个新的数组.在这种情况,你可以通过使用`Array.push.apply(arr1,arr2)`来代替.它会把第二的数组合并到一个当中从而减少内存的使用:
```javascript
var array1 = [1,2,3]
var array2 = [4,5,6]
console.log(array1.push.apply(array1,array2))//[1,2,3,4,5,6]
```

# 把dom列表转换为数组
如果你运行`document.querySelectorAll("p")`的时候,它将会返回一个包含dom元素的数组(如果有p元素的话),这就是dom列表.但是这个对象是没有数组的所有方法,如:`sort()`,`reduce()`,`map()`,`filter()`.为了让这个对象能使用数组的那些方法你需要把它转化为数组.要实现这个只需要使用`[].slice.call(elements)`:
```javascript
var element = document.querySelectorAll("p") //NodeList
var arrayElement = [].slice.call(elements) // Now the NodeList is an array
var arrayElements = Array.from(elements); // This is another way of converting NodeList to Array  
```
# 数组元素随机排序
我们可以需要使用任何三方库如(Lodash)就可以实现对数组内容的随机排序,只需要运行一下代码:
```javascript
var list = [1,2,3]
console.log(list.sort(function(){
    return Math.random() - 0.5
}))
```
上面为什么可以这样实现呢?原因如下:
> sort是根据后面的参数的正负来排序，我们取个随机数0~1，这个以0.5为分界线

# 总结
这里我就不写原作的总结了,我谈谈我看完之后的想法吧.第一这些写法有部分我都在项目中使用过,的确能很好的发挥作用而且让你的代码更简洁.
> 总之多学吧 O(∩_∩)O哈哈哈~
>> 如果发现有什么翻译的不对或则什么其他的问题可以留下评论哦

