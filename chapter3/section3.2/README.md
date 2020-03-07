## 3.2 构造函数
**1. 构造函数：** 一种特殊的函数。
> * 主要用来在创建对象时初始化对象， 即为对象成员变量赋初始值，总与new操作符一起使用在创建对象的语句中。
> * 我们可以使用构造函数来创建多个类似的对象，而免于代码重复。
> * JavaScript 内置了一些构造函数

**2. 构造函数特点**
> * 首字母大写（通常约定）
> * 只能用 new 操作符来执行
> * 内部使用的 this 对象，会指向即将生成的实例对象

**3. 实例化一个对象的过程**
> new 一个新对象 => this 指向这个新对象 =>  执行代码（对 this 赋值）=> 返回 this

```javascript
function Person(name, age) {
    this.name = name;
    this.age = age;
    this.displayInfo = function() {
        console.log(`name: ${name}, age: ${age}`)
    }
}
let jane = new Person('jane', 12)
jane.displayInfo()  //name: jane, age: 12
let tom = new Person('tom', 18)
tom.displayInfo()   //name: tom, age: 18
```
**JavaScript 内置了很多构造函数，如：**

**Object、Function、Array、RegExp、Date、Number、String、Boolean。**

**Object** 在 [2.2 引用类型](../chapter2/section2.md) 已经详细介绍过了。
在 JavaScript 中，Function、Array、RegExp、Date、Number、String、Boolean 是构造函数，也有自己的构造函数，他们的构造函数就是 Object，即 Object 是其他构造函数的构造函数。

后面还会介绍一个 **Math** 对象，**Math** 不是对象的类，没有构造函数，但作为 JavaScript 内置的对象，可直接调用来进行数学方法的处理。

##### [3.2.1 Function](./section1.md)
##### [3.2.2 Array](./section2.md)
##### [3.2.3 Date](./section3.md)
##### [3.2.4 RegExp](./section4.md)
##### [3.2.5 Number、String、Boolean](./section5.md)
##### [3.2.6 Math](./section6.md)