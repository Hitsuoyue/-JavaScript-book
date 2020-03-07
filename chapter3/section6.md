### 3.6 模拟面向对象的类
**面向对象的编程中的类：** 是用于创建对象的可扩展的程序代码模版，它为对象提供了状态（成员变量）的初始值和行为（成员函数和方法）的实现。

ES6 中封装了 class，在 ES6 中的 class 出现前，也可以通过其他的编程模式来创建类。

#### 3.6.1 基于构造函数的类
```javascript
function Person(name, age) {
    function getAge() {
        return age + 10;
    } 
    this.outputInfo = function() {
        console.log('name：', name, 'currentAge: ', getAge())
    }
}
let jane = new Person('jane', 14);
jane.outputInfo()     //name： jane currentAge:  24
```
* **优点：**
如上，`getAge` 方法是外部不可见的（私有的），可隐藏内部方法的实现；而 `outputInfo` 被分配到 `this` 上，则是外部可见的（即公有的），用此构造函数创建的对象可以使用共有方法。

* **缺点：**
所有的方法都在构造函数内部，每次 new 一个实例对象，都会创建内部的这些方法，且不同实例对象间不能共享这些方法，浪费内存资源。

#### 3.6.2 基于原型的类
```javascript
function Person(name, age) {
    this.name = name;
    this.age = age;
}
Person.prototype._getAge = function() {
    return this.age + 10;
}

Person.prototype.outputInfo = function() {
    console.log('name：', this.name, 'currentAge: ', this._getAge())
}
let jane = new Person('jane', 14);
jane.outputInfo()     //name： jane currentAge:  24
```

* **优点：**
如上，将公共方法放在原型中，创建新对象直接调用原型中的方法，对象中没有的属性和方法，可以在原型链中寻找。









<!-- 
#### 3.6.2 工厂类模式
```javascript
function Person(name, age) {
    function getAge() {
        return age + 10;
    } 
    return {
        info: function () {
           console.log('name：', name, 'currentAge: ', getAge())
        }
    }
}
let jane = Person('jane', 14);
jane.info()     //name： jane currentAge:  24
```
如上，这种方法创建一个函数，返回一个对象，里面包含公共方法或公共属性。
-->