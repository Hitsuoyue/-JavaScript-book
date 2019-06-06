## 2.4 变量赋值
**基本类型数据赋值：**
从一个基本类型变量向另一个变量赋值时，会在内存中新建一个地址，存放新的变量和复制过来的值；
```javascript
let a = 1;
let b = a;
b = 3;  
console.log(a, b)// =>  a = 1; b = 3; a 和 b 的值存在于内存中的两个地址，互不影响。
```
**引用类型数据赋值：**
从一个引用类型变量向另一个变量赋值时，同上，但引用类型的值，实际上是一个指针，与初始变量指向同一个堆内存的对象。因此，这两个变量会互相影响。
```javascript
let s = {name:"jane"};let y = s; y.name="tom";console.log(s, y)
let a = {name: "jane"};
let b = a;
b.name = "tom"; 
b.city="cc";
console.log(a, b) // =>  {name: "tom", city: "cc"} {name: "tom", city: "cc"} a 和 b 的值存在于内存中的两个地址，但值是同一个指针，指向同一个内存中的对象，属性的改变会相互影响。
```
