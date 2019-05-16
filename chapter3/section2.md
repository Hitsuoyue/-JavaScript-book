## 3.2 原型
**所有引用类型其隐式原型都指向它的构造函数的显式原型**
> obj._ proto _ === Object.prototype
> * 当试图得到一个对象的某个属性时，如果这个对象本身没有这个属性，会去它的  _ proto _ （即其构造函数的 prototype ）中寻找。

**隐式原型：**
> 所有引用类型（数组、对象、函数），都有一个 _ proto _ 属性，属性值是一个普通对象。

**显式原型：**
> 所有的函数都有一个 prototype 属性，属性值是一个普通对象。

**hasOwnProperty：** 
> 只判断对象本身是否包含某属性，不去其原型链中寻找。