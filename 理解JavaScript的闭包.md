## 理解JavaScript的闭包

1. 闭包

   > 调用作用域以外的变量标识符，就叫闭包。(自己理解)
   >
   > 闭包是一个函数，他在函数内部创建，并且携带了自身创建时的所处环境信息（比如说变量信息和其他函数信息）。
   >
   > 当函数可以记住并访问所在的词法作用域时，就产生了闭包，即使函数是在当前词法作用域之外执行。

2. 变量作用域

   > 1. 当js里面**声明**一个函数的时候，会给函数对象创建一个scope属性，该属性指向当前作用链对象。
   > 2. 当js里面**调用**一个函数的时候，会创建一个执行上下文，这个执行上下文定义了函数解释执行时的环境信息，每个执行上下文都有自己的作用域链，主要用于变量标识符的解析。
   > 3. 在js引擎运行一个函数的时候，它首先会把该函数的scope属性添加到执行上下文的作用域链上面，然后再创建一个**活动对象**添加到此作用域顶端共同组成了新的作用域链。活动对象包含了该函数的所有形参，arguments对象，所有的局部变量等信息。
   > 4. 当解析执行函数的每一条语句时，会依据这个执行上下文的作用域链来查找标识符，如果在一个作用域对象上面没有找到标识符，则会沿着作用域链一直向上查找，这一点类似于js的原型继承的属性查找机制。-

3. 变量提升

   > 1. 首先是函数声明提升，
   > 2. 再是变量提升

4. this绑定

   > 1. this绑定的内容与函数无关，而与函数的执行环境有关。
   > 2. 函数的this绑定的内容可以通过bind，apply和call函数来动态进行修改。
   > 3. 巧用闭包可以消除不必要的this绑定，提高代码的可读性。
   > 4. 从作用域和调用链方面看就很好理解了,  匿名函数是一个没有指针的全局变量，那么它的this指向的就是全局 就是window对象。这并不是设计缺陷，这种调用很安全，通过window并不能找到这个匿名函数，因为匿名函数没有指针。



额外的知识

1. 闭包也是一个函数，存储了额外的环境信息，所以理论上它比纯函数占用更多的内存。
2. 多使用闭包和无状态编程，让bug从此远离我们
3. 面向对象是穷人的闭包（OO is a poor man's closure.）
4. 除了闭包，你还需要被FP和无状态，lambda calculus等概念洗脑。
5. JavaScript中的函数运行在它们定义的作用域里，而不是他们被执行的作用域里。