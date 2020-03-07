### 3.1 函数
#### 3.1.1 函数声明：
```javascript
//语法：
function 函数名(参数1, 参数2,...,参数N) {
    函数体
}
//eg:
function sayHi(name, message) {
    alert("Hello " + name + "," + message);
}
```

#### 3.1.2 函数调用
```javascript
//语法
functionName(arg0, arg1,...,argN)；
//eg:
sayHi("Nicholas", "how are you today?");//弹出 "Hello Nicholas,how are you today?"
```

#### 3.1.3 变量作用域
* 函数内声明的变量，只在该函数内部可见。
```javascript
function sayHi() {
  let name = 'jane';
  let age = 18;
  alert(name + ":" + age);
}
console.log('age:', age);//age is not defined
```

* 函数外声明的变量，函数可以访问，也可以修改。

```javascript
let age = 20;
function sayHi() {
  let name = 'jane';
  age = 18;
  console.log(name + ":" + age);
}
sayHi() //jane:18
```

#### 3.1.4 函数返回值
任何函数、任何时候都可以通过 return 语句后跟要返回的值来是实现返回值。函数会在执行完 return 语句后停止并立即退出。因此，return 之后的任何代码都永远不会执行。
```javascript
function sum(num1, num2) {
    return num1 + num2;
}
let result = sum(5, 10);  // result 为15
```

**注：**
> * return 可以不带任何返回值。则函数将返回 undefined 值。一般用在需要提前停止函数执行，又不需要返回值的情况下。
> * 推荐：要么让函数始终都有返回值，要么就永远都不要有返回值，否则会给代码调试带来不便。

> 严格模式下的限制：  发生以下情况，会导致语法错误，代码无法执行。
> * 不能把函数/参数命名为eval 或arguments；
> * 不能出现两个命名参数同名的情况。

#### 3.1.5 参数
参数不是必需的，可以不传，个数及类型，即使个数与定义的个数不同，也不会报错。因为参数在内部使用一个数组来表示的。
函数体内部可以通过 arguments 对象来访问这个参数数组，从而获取传递过来的每一个参数。

```javascript
function sayHi(name, message) {
    alert("Hello " + name + "," + message);
}
sayHi('jane', 'nice to meet you!')//Hello jane,nice to meet you!
//重写
function sayHi() {
    alert("Hello " + arguments[0] + "," + arguments[1]);
}
sayHi('jane', 'nice to meet you!')//Hello jane,nice to meet you!
```

> * arguments 对象的长度由传入函数的参数决定;
> * 没有传递值的命名参数自动被赋予 undefined 值，类似于定义了变量但未初始化。

**严格模式下:**
> 重写arguments 的值会导致语法错误（代码将不会执行）

#### 3.1.6 ES6 函数新特性
**1. 参数默认值**

> 声明函数时直接为参数设置默认值，若调用函数时未赋值，则参数的值为默认值。
```javascript
function sayHi(name, message='nice to meet you!') {
    console.log("Hello " + name + "," + message);
}
sayHi('jane', 'yeah!')  //Hello jane,yeah!
sayHi('tom')  //Hello tom,nice to meet you!
```

> 若默认值为表达式，则执行时才计算其值
```javascript
let num = 10;
function sayHi(name, age=num+8) {
    console.log(name + ", age:" + age);
    num+=10;
}
sayHi('jane')  //jane, age:18
sayHi('tom')  //tom, age:28
sayHi('lucy', 12)   //lucy, age:12
```

**2. rest 参数**

**...变量名**，用于获取函数的剩余参数，将其放在数组中。
rest 参数必须是最后一个参数，否则会报错。
```javascript
function sum(...nums){
  let sum = 0;
  nums.forEach(item => {
    sum += item;
  })
  return sum
}
let result1 = sum()   //0
let result2 = sum(1,2,3,4)   //10
```

**3. 扩展运算符**

**...变量名**，用于取出参数对象中的所有可遍历属性，拷贝到当前对象之中。
```javascript
//对象
let obj1 = {name: 'jane', age: 18};
let obj2 = {color: 'yellow', ...obj1} //obj2: {color: "yellow", name: "jane", age: 18}
//等价于
let obj3 = Object.assign({color: 'yellow'}, obj1)   //obj3: {color: "yellow", name: "jane", age: 18}

//数组
let arr1 = [1,2,3]
let arr2 = [4,5,6]
let arr3 = [7,8,9]
let arr4 = [...arr1, ...arr2, ...arr3]  //[1, 2, 3, 4, 5, 6, 7, 8, 9]
//等价于
let arr5 = arr1.concat(arr2, arr3)  //[1, 2, 3, 4, 5, 6, 7, 8, 9]
```

**4. 箭头函数**
```javascript
//箭头函数定义
let sum = (a,b) => {
  return a+b
}
//等同于
let sum = function(a,b) {
  return a+b
}
```
> * 箭头函数的 this 指向的是定义时的 this 对象，而不是执行时的 this 对象
> * 箭头函数是匿名函数 ，不能作为构造函数
> * 箭头函数不可以使用 arguments，可使用 rest 参数

**5. name**

ES6 的 name 会返回函数名。
```javascript
function sum(...nums){
  let sum = 0;
  nums.forEach(item => {
    sum += item;
  })
  return sum
}
console.log(sum.name);    //"sum"
```