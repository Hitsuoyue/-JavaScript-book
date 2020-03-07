### 3.2.5 Number、String、Boolean 构造函数
前面 [2.1 基本类型](./chapter2/section1.md) 章节已经介绍了 Number、String、Boolean 类型，下面介绍下 Number、String、Boolean 三种构造函数。

#### 3.2.5.1 Number 构造函数
* 通过 Number 构造函数创建的是对象

```javascript
let numObj = new Number(2);
let num = 2;

typeof numObj  //"object"
typeof num //"number"
numObj === num; //false

//通过 Number 构造函数创建的是对象可以调用数字的方法
let sum = numObj + numObj;  //4
let str = numObj + 'hello';  //"2hello"

//通过 Number 构造函数创建的是对象可以添加属性
numObj.name='jane'//
console.log(numObj.name)   //"jane"
num.name='tom'
console.log(num.name)  //undefined
```

* Number() 也可以把各种值转换为数字，不能转换的就是 NaN。

```javascript
Number('1')   //1
Number(true)  //1
Number(false)   //0
Number('text')  //NaN
```

#### 3.2.5.2 String 构造函数
* 通过 String 构造函数创建的是对象

```javascript
let stringObj = new String('abc');
let string = 'abc';

typeof stringObj  //"object"
typeof string //"string"

stringObj === string; //false

//通过 String 构造函数创建的是对象可以添加属性
stringObj.name='jane'//
console.log(stringObj.name)   //"jane"
string.name='tom'
console.log(string.name)  //undefined

//通过 String 构造函数创建的是对象可以调用字符串的方法
let testStr = new String('testStr');
testStr.substr(1,3) //"est" 截取 testStr 从第1个开始，取3个
testStr.substring(1,4)  //"est" 截取 testStr 从第1个开始，到第4个，不包含第4个
testStr.slice(1,4)  //"est" 截取 testStr 从第1个开始，到第4个，不包含第4个
testStr.substring(2,0)  //"te"
testStr.slice(2,0)  //""
```

* String() 也可以把各种值转换为字符串。

```javascript
String(1)   //"1"
String(true)  //"true"
String(false)   //"false"
String('text')  //"text"
String([1,2,3])   //"1,2,3"
String({name: 'jane'})  //"[object Object]"
```

#### 3.2.5.3 Boolean 构造函数* 
通过 Boolean 构造函数创建的是对象

```javascript
let booleanObj = new String(true);
let boolean = true;

typeof booleanObj  //"object"
typeof boolean //"boolean"

booleanObj === boolean; //false

//通过 Boolean 构造函数创建的是对象可以添加属性
booleanObj.name='jane'//
console.log(booleanObj.name)   //"jane"
boolean.name='tom'
console.log(boolean.name)  //undefined

```

* Boolean() 也可以把各种值转换为布尔值，同 [2.1 基本类型](./chapter2/section1.md) 里面介绍的一样 。

```javascript
Boolean('111') === true
Boolean('text') === true//true
Boolean(2) === true//true
Boolean({}) === true//true
Boolean({name: 'jane'}) === true//true
```