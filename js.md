# let const 和 var

#### 1. 作用域
    let const 具有块级作用域；而var不存在块级作用域,
    *块级作用域* 就是代码块，语言组成为执行语句组成代码块；
    最显著的特点就是大括号
    let，const的生命周期只存在于代码块内，var变量则存活于当前的整个作用域里,
    在es6之前想要实现代码块，可以通过立即执行语句来实现

```javascript
   var a = 1;// 这是语句
   {
       var a = 2;
   }
   // 这是代码块
```

#### 2. 变量提升
    变量提升是js的一大特点，即es6之前，所有的var， function等，不管声明位置在哪里，都会被提取到头部，这样的目的是方便js在浏览器端的快速完成编译.而let、const包括后续的class都不存在变量提升，这样就形成了暂时性死区，
#### 3. 变量可赋值
    let,var声明之后可以重新赋值，但const不行
#### 4. 全局作用域
    块级作用域变量不会绑定在顶级作用域上，而var声明在全局下的变量会绑定在顶部全局变量this上，浏览器环境下就是window
```javascript
// 在浏览器中
let RegExp = "Hello!";
console.log(RegExp); // "Hello!"
console.log(window.RegExp === RegExp); // false
const ncz = "Hi!";
console.log(ncz); // "Hi!"
console.log("ncz" in window);
var _varc = 123;
window._varc;// 123
```
*块级绑定当前的最佳实践就是：在默认情况下使用 const ，而只在你知道变量值需要被更改
的情况下才使用 let 。这在代码中能确保基本层次的不可变性，有助于防止某些类型的错
误。*
# 字符串和正则
1. 只有调用正则表达式对象上的方法（例如 exec() 与 test() 方法）， lastIndex 属性
第二章 字符串与正则表达式
才会生效。而将正则表达式作为参数传递给字符串上的方法（例如 match() ），并不会
体现粘连特性。
2. 当使用 ^ 字符来匹配字符串的起始处时，粘连的正则表达式只会匹配字符串的起始处
（或者在多行模式下匹配行首）。当 lastIndex 为 0 时， ^ 不会让粘连的正则表达式
与非粘连的有任何区别；而当 lastIndex 在单行模式下不对应整个字符串起始处，或者
当它在多行模式下不对应行首时，粘连的正则表达式永远不会匹配成功。
# 函数
默认值
>arguments  和 参数变量的区别
- 函数参数拥有各自的作用域和暂时性死区，与函数体的作用域相分离，这意味着参数的
默认值不允许访问在函数体内部声明的任意变量。
- 函数的 length 属性用于指示具名参数的数量，而剩余参数对其毫无影响。此例中
pick(a, ...b) 函数的 length 属性值是 1 ，因为只有 a 参数被用于计算该值。
>箭头函数
- 没有 this 、 super 、 arguments ，也没有 new.target 绑定： this 、 super 、
arguments 、以及函数内部的 new.target 的值由所在的、最靠近的非箭头函数来决定
（ super 详见第四章）。
- 不能被使用 new 调用： 箭头函数没有 [[Construct]] 方法，因此不能被用为构造函
数，使用 new 调用箭头函数会抛出错误。
没有原型： 既然不能对箭头函数使用 new ，那么它也不需要原型，也就是没有
prototype 属性。
- 不能更改 this ： this 的值在函数内部不能被修改，在函数的整个生命周期内其值会
保持不变。
- 没有 arguments 对象： 既然箭头函数没有 arguments 绑定，你必须依赖于具名参数或
剩余参数来访问函数的参数。
- 不允许重复的具名参数： 箭头函数不允许拥有重复的具名参数，无论是否在严格模式
下；而相对来说，传统函数只有在严格模式下才禁止这种重复。
> 注意：箭头函数也拥有 name 属性，并且遵循与其他函数相同的规则。
