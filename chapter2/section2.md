## 2.2 各数据类型及描述
### 2.2.1 Undefined
**定义：**
```javascript
let a = undefined;
```
使用var声明变量但未初始化，或初始化其值为undefined。

```javascript
（var message）；alert（message）；//undefined 
```
### 2.2.2 Null
**定义：**
```javascript
let a = null;
```
空对象指针，用于在将来保存对象。这样只要检查变量是否等于null，就知道这个变量内是否已经保存了一个对象的引用。

**注：**
```
alert（null == undefined）； //true
alert（null === undefined）； //false
```
### 2.2.3 Boolean
**定义：**
```javascript
let a = true;
let b = false;
```
* ECMAScript 中所有类型的值都有与这两个 Boolean 值等价的值，可使用转型函数 Boolean() 进行转换。
```javascript
Boolean('111') === true
```

* 非空字符串、非零数值、任何对象都是 true；
```javascript
Boolean('111') === true
```
* 空字符串、数值零或NaN、null都是false。
```javascript
Boolean('text') === true//true
Boolean(2) === true//true
Boolean({}) === true//true
Boolean({name: 'jane'}) === true//true
```
* 流控制语句（如if）会自动执行 Boolean 转换。
```javascript
var message = 'hello';
if(message){alert('value is true');}  //message被自动转换为对应的 Boolean 值（true）。
```

### 2.2.4 Number
#### 2.2.4.1 定义
```javascript
//整数
let num = 12;
//八进制：第一位为0，后面数值若超出范围，则前导零被忽略，将后面数值按十进制解析
let num1 = 070;//八进制的56
let num2 = 079;//无效的八进制数值，解析为79
//十六进制：前两位为0x，后跟十六进制数字
let num3 = 0xa;  //十六进制的10
let num4 = 0x1f；  //十六进制的31
```
#### 2.2.4.2 NaN
NaN（非数值）——特殊的数值，本该返回数值的操作数未返回数值的情况，不抛出错误。

**1.任何涉及 NaN 的操作都会返回 NaN ，NaN 与任何值都不相等。**
```javascript
alert(NaN == NaN);   //false
```

**2.isNaN()**

isNaN() 函数收到一个值后，会尝试将这个值转换为数值，可以转换则返回 false，否则返回 true。
```javascript
isNaN(true)//false
isNaN(false)//false
isNaN(1)//false
isNaN('1')//false
isNaN('2')//false
isNaN(null)//false
isNaN(undefined)//true
isNaN({})//true
isNaN(function(){})//true
isNaN('2/0')//true
```

#### 2.2.4.3 数值转换
> **Number()：**将任何类型转换为数值；
> **parseInt()：**将字符串转换为整数；
> **parseFloat()：**将字符串转换为浮点数；

```
Number（）
var num1 = Number("Hello world!"); //NaN
var num2 = Number(""); //0
var num3 = Number("000011"); //11
var num4 = Number(true); //1
```
```
parseInt（）
var num1 = parseInt("1234blue"); // 1234
var num2 = parseInt(""); // NaN
var num4 = parseInt(22.5); // 22
var num6 = parseInt("70"); // 70
var num8 = parseInt("s2131"); // NaN
var num = parseInt("0xAF", 16); //175
var num1 = parseInt("AF", 16); //175
var num2 = parseInt("AF"); //NaN
指定基数转换：
var num1 = parseInt("10", 2); //2 （按二进制解析）
var num2 = parseInt("10", 8); //8 （按八进制解析）
var num3 = parseInt("10", 10); //10 （按十进制解析）
var num4 = parseInt("10", 16); //16 （按十六进制解析）
```
```
parseFloat（）
从第一个字符开始解析，始终忽略前导零
var num1 = parseFloat("1234blue"); //1234 （整数）
var num2 = parseFloat("0xA"); //0
var num3 = parseFloat("22.5"); //22.5
var num4 = parseFloat("22.34.5"); //22.34
var num5 = parseFloat("0908.5"); //908.5
var num6 = parseFloat("3.125e7"); //31250000
```

### 2.2.5 String
* String 类型用于表示由零或多个16 位Unicode 字符组成的字符序列，即字符串。
* 字符串可以由双引号（"）或单引号（'）表示，但前后符号应保持一致。

#### 2.2.5.1 定义
```javascript
var firstName = "Nicholas";
var lastName = 'Zakas';
```

#### 2.2.5.2 toString()
1. 数值、布尔值、对象和字符串都有一个 toString() 方法，返回一个对应字符串。
```javascript
let num = 2; num.toString();//"2"
let flag = true; flag.toString();//"true"
let text = 'hello'; text.toString();//"hello"
```
数值的 toString() 方法可以传一个参数：输出数值的基数，如下：
```
var num = 10;
alert(num.toString()); // "10"  不传，默认为10
alert(num.toString(2)); // "1010"
alert(num.toString(8)); // "12"
alert(num.toString(10)); // "10"
alert(num.toString(16)); // "a"
```
2. 对象的 toString() 方法
```javascript
let obj = {name: 'jane'};
obj.toString() //"[object Object]"`
```
3. null 和 undefined 没有 toString() 方法。

**String():**
不知道要转换的值是不是 null 或 undefined 时，可以使用转型函数 String()，这个函数可以将任何类型的值转换为字符串。String()遵循下列转换规则：
  * 如果值有toString()方法，则调用该方法（没有参数）并返回相应的结果；
  * 如果值是null，则返回"null"；
 *  如果值是undefined，则返回"undefined"。
#### 2.2.5.3 String 的其他常用方法
```javascript
let testStr = 'testStr';
testStr.substr(1,3) //"est" 截取 testStr 从第1个开始，取3个
testStr.substring(1,4)  //"est" 截取 testStr 从第1个开始，到第4个，不包含第4个
testStr.slice(1,4)  //"est" 截取 testStr 从第1个开始，到第4个，不包含第4个
testStr.substring(2,0)  //"te"
testStr.slice(2,0)  //""
```

### 2.2.6 Object
#### 2.2.6.1 创建对象
```javascript
//“构造函数”语法创建
let info = new Object()
//“字面量”语法创建 —— 常用
let info = {
    name: 'jane',   //键"name",值"jane"
    age: 17 //键"age",值17
}
```

```javascript
//添加属性 .
info.address = 'beijing'//"beijing"，此时的 info:{name: "jane", age: 17, address: "beijing"}
//添加属性 []
info['friend'] = 'tom'//"tom"，此时的 info:{name: "jane", age: 17, address: "beijing", friend: "tom"}
//删除属性
delete info.age//true，此时的 info:{name: "jane", address: "beijing", friend: "tom"}
//获取对象属性值 .
info.address//"beijing"
//获取对象属性值 []
info['friend']//"tom"
```

ECMAScript 中的对象其实就是一组数据和功能的集合。对象可以通过执行new 操作符后跟要创建
的对象类型的名称来创建。 
如：var o = new Object();若不传参数，圆括号可省，但不推荐这样做。
仅仅创建Object 的实例并没有什么用处，但关键是要理解一个重要的思想：即在ECMAScript 中，
Object 类型是所有它的实例的基础。换句话说，
Object 类型所具有的任何属性和方法也同样存在于更具体的对象中。
Object 的每个实例都具有下列属性和方法。
  constructor：保存着用于创建当前对象的函数。对于前面的例子而言，构造函数（constructor）
就是Object()。
  hasOwnProperty(propertyName)：用于检查给定的属性在当前对象实例中（而不是在实例的原型中）是否存在。其中，作为参数的属性名（propertyName）必须以字符串形式指定（例如：o.hasOwnProperty("name")）。
  isPrototypeOf(object)：用于检查传入的对象是否是传入对象的原型
  propertyIsEnumerable(propertyName)：用于检查给定的属性是否能够使用for-in 语句来枚举。与hasOwnProperty()方法一样，作为参数的属性名必须以字符串形式指定。
  toLocaleString()：返回对象的字符串表示，该字符串与执行环境的地区对应。
  toString()：返回对象的字符串表示。
  valueOf()：返回对象的字符串、数值或布尔值表示。通常与toString()方法的返回值相同。
由于在ECMAScript 中Object 是所有对象的基础，因此所有对象都具有这些基本的属性和方法。

