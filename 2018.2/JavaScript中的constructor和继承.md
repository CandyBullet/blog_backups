[^_^]: # ( -*- coding: utf-8 -*-)
[^_^]: # ( @Author: yang zhou)
[^_^]: # ( @Date:   2018-02-10 12:29:50)
[^_^]: # ( @Last modified by:   yang zhou)
[^_^]: # ( @Last Modified time: 2018-02-10 12:30:03)

# JavaScript中的constructor和继承 #

## 概述 ##
这是我在看[JavaScript面向对象编程指南][1]的时候，对`constructor`和继承的总结。

关于它们的详细知识，可以上网查到，所以我只写那些网上没有的。

## 内容 ##

 - `constructor`的理解
 - `constructor`的实际用途
 - `constructor`的陷阱
 - 从应用角度理解继承
 - 函数构造器的继承
 - 纯对象的继承

### constructor的理解 ###
`constructor` 属性是一个指针，指向创建此对象的函数。（可以更改）

### constructor的实际用途 ###
看下面这段代码：
```
var a,b;
(function(){
  function A (arg1,arg2) {
    this.a = 1;
    this.b=2; 
  }

  A.prototype.log = function () {
    console.log(this.a);
  }
  c = new A();
})()
c.log();
// 1
```
实例c是用闭包建立的，但是因为A是在闭包里面，所以我们不能直接访问A。但是如果需要给A添加方法怎么办呢？方法是用`constructor`。

```
c.constructor.prototype.log2 = function () {
  console.log(2)
}

c.log2();
// 2
```
### constructor的陷阱 ###

```
//继承
Child.prototype = new F();
Child.prototype.constructor = Child;
```

我们一般在继承中，要给constructor属性进行重置，比如上面那段代码，这是为什么呢？

先来看看一个例子：

```
function Dog(){this.tail = true;}
var benji = new Dog();
Dog.prototype.say = function(){return 'woof';};

Dog.prototype = {paws:4}
var lucy = new Dog();

benji.constructor.prototype.paws
//4
lucy.constructor.prototype.paws
//undefined

```

其中，`benji`和`lucy`都是`Dog()`的子对象，但是结果却不相同。造成这种结果的原因是`Dog.prototype = {paws:4}`重置了`Dog()`的原型。（原理不明，貌似和`__proto__`有关。）

如果在`Dog.prototype = {paws:4}`后面再加一条语句`Dog.prototype.constructor = Dog;`结果就一样了。这也是为什么在继承中要重置`constructor`的原因。

### 从应用角度理解继承 ###
继承，就是对父元素的代码复用。

```
//父元素是函数构造器
function Parent() {
    this.id = 3;   //带this的自身属性
    var od = 5;  //不带this的自身属性
}
Parent.prototype.ud = 7;  //原型属性

//父元素是纯对象
Parent= {id:9};
Parent.prototype.ud = 7;
```
综合考虑一下，父元素分为2种：函数构造器和纯对象。父元素里面的代码又分为自身属性和原型属性。（方法和属性差不多，所以只考虑属性。）

所以我们分别来讨论函数构造器和纯对象的代码复用，即属性继承。

### 函数构造器的继承 ###

 - 只继承原型属性

很简单，只需要把父对象的原型赋值给子对象即可。（**原型继承法**）
```
Child.prototype = Parent.prototype;
```
但是这样的话，修改子对象的原型会影响父对象的原型，所以我们考虑用闭包。（**临时构造器法**）
```
var F = function() {};
F.prototype = Parent.prototype;
Child.prototype = new F();
Child.prototype.constructor = Child;
```
但是如果子对象的prototype本来就有值，所以不能直接进行prototype的赋值。这个时候我们可以直接把属性拷贝过去。（**原型属性拷贝法**）

```
var p = Parent.prototype;
var c = Child.prototype;
for (i in p) {
    c[i] = p[i];
}
```
当然，还有**深拷贝法**，这里就不贴代码了。

 - 只继承自身属性。

首先想到的就是**拷贝法**，上面贴过代码这里就补贴了。但是拷贝法只能继承父对象中不带this的自身属性。

如果想只继承带this的自身属性，可以用**构造器借用法**。

```
function Child() {
    Parent.apply(this, argument);
}
```

如果想全部继承的话，那就只能两者结合了。

 - 同时继承自身属性和原型属性

这个时候，我们第一个想到的就是用`new`。（**原型链法**）

```
Child.prototype = new Parent();
```
需要注意的是，这时子对象仅继承父对象中带有`this`的自身元素，**不继承**不带`this`的自身元素。

其它方法就只能结合上面多个方法了。

### 纯对象的继承 ###

 - 只继承原型属性。

和函数构造器的继承一样。

 - 只继承自身属性。

当父元素是纯对象的时候，它里面**没有**带`this`的自身元素。所以只需用拷贝法即可。

另外，还可以把父元素的自身元素放到子元素的`prototype`里面去。（原型继承法）

```
function object() {
    function F(){};
    F.prototype = Parent;
    return new F();
}
```

 - 同时继承自身属性和原型属性

这个就是结合上述方法了。

  [1]: https://book.douban.com/subject/21372235/
