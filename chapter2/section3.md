## 2.3 引用类型 —— 其他
### 2.3.1 Array
#### 2.3.1.1 创建数组
**创建数组：**
```javascript
//使用new Array()
let arr1 = new Array(); //[]
let arr2 = new Array(5); //[empty × 5]
let arr3 = new Array('beijing','tianjin',12);//["beijing", "tianjin", 12]

//使用方括号 —— 常用
let arrs1 = [];//[]
let arrs2 = ['beijing','tianjin',12];//["beijing", "tianjin", 12]
```

**数组内的元素可以是任何类型：**
```javascript
let arr = ['beijing', {name: 'jane'}, 12, true, function(){console.log('fn')}];
//0: "beijing"
//1: {name: "jane"}
//2: 12
//3: true
//4: ƒ ()
```

**数组编号从 0 开始：**
```javascript
let arr = ['beijing','tianjin',12];
//arr[0]: 'beijing'
//arr[1]: 'tianjin'
//arr[2]: 12
```

**通过 数组名[下标] 来获取或设置值：**
```javascript
let arr = ['beijing','tianjin',12];
console.log(arr[0]);// 'beijing'
arr[3] = true;
console.log(arr); //["beijing", "tianjin", 12, true]
```

#### 2.3.1.2 常用方法
**判断是否为数组：Array.isArray**
```javascript
//Array.isArray —— 是则返回 true，否责返回 false
let a = [1,2,3];
let b = 'str';
let b = [];
console.log(Array.isArray(a), Array.isArray(b), Array.isArray(c));  //  true false true

//unshift —— 在数组最前面添加元素，可添加多个
arr.unshift('a', 'b', 'c')
console.log(arr);//arr: ["a", "b", "c", 1, 2, 3, 4, 5, 6]
```
**添加数组元素：push、unshift**
```javascript
//push —— 在数组最后添加元素，可添加多个
let arr = [1,2,3];
arr.push(4,5,6);
console.log(arr);//arr: [1,2,3,4,5,6]

//unshift —— 在数组最前面添加元素，可添加多个
arr.unshift('a', 'b', 'c')
console.log(arr);//arr: ["a", "b", "c", 1, 2, 3, 4, 5, 6]
```

**删除数组元素：pop、shift**
```javascript
//pop() —— 删除并返回数组的最后一个元素
console.log(arr.pop())//6
console.log(arr);//["a", "b", "c", 1, 2, 3, 4, 5]

//shift() —— 删除并返回数组的第一个元素
console.log(arr.shift()) //a
console.log(arr); //["b", "c", 1, 2, 3, 4, 5]
```

**替换数组中的元素：splice**
```javascript
//splice(start, num, newitem) —— 把 arr[start] 开始的 num 个，替换成后面的元素，不改变原数组
console.log(arr)    //[5, 4, 3, 2, 1, "c", "b"]
console.log(arr.splice(2,3,'jane')) //[3, 2, 1]
console.log(arr)    //[5, 4, "jane", "c", "b"]
console.log(arr.splice(1,1,'aa','bb', 'cc')) //[4]
console.log(arr)    //[5, "aa", "bb", "cc", "jane", "c", "b"]
```

**替换数组中某些元素：fill**
```javascript
//fill(value, start, end)
let arr = [1, 2, 3, 4, 5, 5, 6, "b", "c"]
let result1 = arr.fill('hello'); 
// result1: ["hello", "hello", "hello", "hello", "hello", "hello", "hello", "hello", "hello"]
let result2 = arr.fill('hello', 2, 5); 
//result2: [1, 2, "hello", "hello", "hello", 5, 6, "b", "c"]
let result3 = arr.fill('hello', 2, );
//result3: [1, 2, "hello", "hello", "hello", "hello", "hello", "hello", "hello"]
```

**取数组中的元素：slice**
```javascript
//slice(start, end) —— 取 [arr[start], ...,  arr[end-1]]，不改变原数组
console.log(arr)    //[5, 4, 3, 2, 1, "c", "b"]
console.log(arr.slice(2,5)) //[3, 2, 1]
console.log(arr)    //[5, 4, 3, 2, 1, "c", "b"]
```

**颠倒数组中元素的顺序：reverse**
```javascript
//reverse —— 颠倒数组中元素的顺序
console.log(arr)    //["b", "c", 1, 2, 3, 4, 5]
console.log(arr.reverse())   //[5, 4, 3, 2, 1, "c", "b"]
console.log(arr)    //[5, 4, 3, 2, 1, "c", "b"]
```

**数组排序：sort**
```javascript
//sort —— 将数组中的元素进行排序
let arrN = [1,2,4,6,12,11]
arrN.sort() //[1, 11, 12, 2, 4, 6]
arrN.sort((a, b)=>{return a-b}) //[1, 2, 4, 6, 11, 12] 从小到大排序
arrN.sort((a, b)=>{return b-a}) //[12, 11, 6, 4, 2, 1] 从大到小排序
```

**数组转换为字符串：toString、join**
```javascript
//1. toString —— 将数组转换为字符串
arr.toString()  //"5,4,3,2,1,c,b

//2. join —— 通过指定的分隔符, 把数组的所有元素连接成一个字符串
arr     //[5, 4, 3, 2, 1, "c", "b"]
arr.join()  //"5,4,3,2,1,c,b"
arr.join('-')   //"5-4-3-2-1-c-b"
```

**连接数组：concat**
```javascript
//concat 连接数组，并返回结果，不改变原数组
let arr1 = ['jane', 'tom']
let arr2 = ['green', 'red']
let arr3 = [true, false]
let arr4 = [1, 2, 3]
arr1.concat(arr2)  //["jane", "tom", "green", "red"]
arr1.concat(arr2, arr3, arr4) //["jane", "tom", "green", "red", true, false, 1, 2, 3]
```

**查询数组： indexOf、lastIndexOf、find、findIndex、filter**
```javascript
let arr1 = [5, 4, 3, 2, 1, 5, 6, "c", "b"];
//indexOf(item) —— 从前面开始查询，返回查到的第一个 item 的下标值
arr1.indexOf(5)   //0

//lastIndexOf(item) —— 从后面开始查询，返回查到的第一个 item 的下标值
arr1.lastIndexOf(5)   //5

//includes(item) —— 判断数组中是否存在 item，存在则返回 true，不存在则返回 false
arr1.includes(0)     //false
arr1.includes(1)     //true

//find —— 遍历数组，返回使函数返回 true 的第一个元素
let arr2 = [
    { name: 'jane', age:12 },
    { name: 'tom', age:13 },
    { name: 'lucy', age:14 },
    { name: 'jimmy', age:12 }
]
let result1 = arr2.find((item, index, array) => {
    return item.age === 12
})
console.log('result1:', result1)    //result: {name: "jane", age: 12}

//findIndex —— 遍历数组，返回使函数返回 true 的第一个元素的下标
let result2 = arr2.findIndex((item, index, array) => {
    return item.age === 12
})
console.log('result2:', result2)    //result: 0

//filter —— 遍历数组，返回使函数返回 true 的所有元素组成的数组
let result3 = arr2.filter((item, index, array) => {
    return item.age === 12
})
console.log('result3:', result3)    
//result3: [{ name: 'jane', age:12 },{ name: 'jimmy', age:12 }]
```

**检查元素：some、every**
```javascript
//some —— 数组中至少有一个元素在执行函数时返回的结果为 true
let arr1 = [1, 2, 3, 4, 5, 5, 6, 7]
let arr2 = [1, 2, 3, 4, 5, 5, 6, 7, 8]
let flag1 = arr1.some((item)=>{
    return item > 7
})  //flag: false
let flag2 = arr2.some((item)=>{
    return item > 7
})  //flag: true

//every —— 数组中每一个元素在执行函数时返回的结果为 true
let arr1 = [1, 2, 3, 4, 5, 5, 6, 7]
let arr2 = [1, 2, 3, 4, 5, 5, 6, 7, 8]
let flag1 = arr1.every((item)=>{
    return item > 7
})  //flag: false
let flag2 = arr2.every((item)=>{
    return item > 7
})  //flag: false
let flag3 = arr2.every((item)=>{
    return item > 0
})  //flag: true
```

**转换数组：map**
```javascript
let arr = [1, 2, 3, 4, 5, 5, 6, "b", "c"]
let result = arr.map(function(item, index, array) {
  return `${item}--hello`;
})
//result:   ["1--hello", "2--hello", "3--hello", "4--hello", "5--hello", "5--hello", "6--hello", "b--hello", "c--hello"]
```

**遍历数组：forEach**
```javascript
let arr = [1, 2, 3, 4]
arr.forEach(function(item, index, array) {
  console.log(item, index, array)
})
// 1 0 (4) [1, 2, 3, 4]
// 2 1 (4) [1, 2, 3, 4]
// 3 2 (4) [1, 2, 3, 4]
// 4 3 (4) [1, 2, 3, 4]
```

**以上会改变数组的方法：** 
push、unshift、pop、shift、splice、reverse、sort、fill

### 2.3.2 Date
Date 为 JavaScript 内置的一个对象，用来存储日期、时间，并提供了一些管理它们的方法。
```javascript
//创建 Date 对象
let date = new Date()//date: Wed Jun 05 2019 17:10:27 GMT+0800 (中国标准时间)

//getDay：返回 0-6，对应星期日到星期六
date.getDay()   //3

//getDate：返回 1-31，对应一个月中的 1-31 号
date.getDate()  //5

//getMonth：返回 0-11，对应1-12月
date.getMonth() //5——6月 

//getFullYear：以四位数字返回年份
date.getFullYear()  //2019

//getHours：返回小时
date.getHours()   //17
//getMinutes：返回分钟
date.getMinutes()   //10
//getSeconds：返回秒
date.getSeconds()   //27
//getMilliseconds：返回毫秒
date.getMilliseconds()  //511

//getTime：返回 1970 年 1 月 1 日至今的毫秒数
date.getTime()  //1559725827511
```

### 2.3.3 Math
Math 不是对象的类，没有构造函数，但作为 JavaScript 内置的对象，可直接调用来进行数学方法的处理。

```javascript
let num = 12345.12;
//四舍五入
Math.round(num);    //12345
//下舍入
Math.floor(num);    //12345
//上舍入
Math.ceil(num);    //12346
//取两个数中的最高值
Math.max(2,3)   //3
//取两个数中的最低值
Math.max(2,3)   //2
//返回 0 ~ 1 之间的随机数
Math.random()   //0.657487039270241
```

### 2.3.4 RegExp
RegExp 是 JavaScript 内置的正则表达式对象，用来对字符串进行匹配。
#### 2.3.4.1 定义正则表达式
1）字面量语法：/pattern/attributes

2）创建 RegExp 对象的语法：new RegExp(pattern, attributes);

#### 2.3.4.2 参数
1) pattern 是一个字符串，指定了正则表达式的模式或其他正则表达式。
2) attributes 是一个可选的字符串，包含属性 "g"、"i" 和 "m"，分别用于指定全局匹配、区分大小写的匹配和多行匹配。如果 pattern 是正则表达式，而不是字符串，则必须省略该参数。

#### 2.3.4.3 修饰符
```
i  执行对大小写不敏感的匹配。
g  执行全局匹配（查找所有匹配而非在找到第一个匹配后停止）。
m  执行多行匹配。
```

#### 2.3.4.4 方括号——查找某个范围内的字符
```
[abc]  查找方括号之间的任何字符。（字母、数字、符号、中文均可）
[^abc]  查找任何不在方括号之间的字符。（字母、数字、符号、中文均可）
[0-9]  查找任何从 0 至 9 的数字。
[a-z]  查找任何从小写 a 到小写 z 的字符。
[A-Z]  查找任何从大写 A 到大写 Z 的字符。
[A-z]  查找任何从大写 A 到小写 z 的字符。
[adgk]  查找给定集合内的任何字符。
[^adgk]  查找给定集合外的任何字符。
(red|blue|green)  查找任何指定的选项。（可匹配单词）
```

#### 2.3.4.5 元字符（Metacharacter）——拥有特殊含义的字符
```
.  查找单个字符，除了换行和行结束符。
\w  查找单词字符。（数字、字母、下划线）
\W  查找非单词字符。（除数字、字母、下划线的字符，包括中文、特殊符号、空格等）
\d  查找数字。
\D  查找非数字字符。
\s  查找空白字符。
\S  查找非空白字符。
\b  匹配单词边界。
\B  匹配非单词边界。
\0  查找 NUL 字符。
\n  查找换行符。
\f  查找换页符。
\r  查找回车符。
\t  查找制表符。
\v  查找垂直制表符。
\xxx  查找以八进制数 xxx 规定的字符。
\xdd  查找以十六进制数 dd 规定的字符。
\uxxxx  查找以十六进制数 xxxx 规定的 Unicode 字符。
```

#### 2.3.4.6 量词
```
n+  =>  匹配任何包含至少一个 n 的字符串。
n*  =>  匹配任何包含零个或多个 n 的字符串。
n?  =>  匹配任何包含零个或一个 n 的字符串。
n{X}  =>  匹配包含 X 个 n 的序列的字符串。 a{2}  aa
n{X,Y}  =>  匹配包含 X 至 Y 个 n 的序列的字符串。a{2,4} aa aaa aaaa  
n{X,}  =>  匹配包含至少 X 个 n 的序列的字符串。a{2}  aa aaa aaaa aaaaa...
n$  =>  匹配任何结尾为 n 的字符串。
^n   => 匹配任何开头为 n 的字符串。
?=n   => 匹配任何其后紧接指定字符串 n 的字符串。
?!n   => 匹配任何其后没有紧接指定字符串 n 的字符串。
```

#### 2.3.4.7 RegExp 对象方法
**1. test  => 检索字符串中指定的值。返回 true 或 false。**
```javascript
let reg = /[a-z]/i;
reg.test('A')   //true
reg.test('z')   //true
reg.test(1)    //false
```

**2. exec  => 检索字符串中指定的值。返回找到的值，并确定其位置。**
```javascript
let str = 'hello everybody!';
let reg = /e/i;
reg.exec(str)   //["e", index: 6, input: "hello everybody!", groups: undefined]
reg.exec('abc')    //null
```

**3. compile =>  编译正则表达式。用于改变 RegExp 对象**
`RegExpObject.compile(regexp,modifier)`
```javascript
let str = 'hello everybody!';
let reg = /e/i;
reg.compile('[0-9]', g)//reg: /[0-9]/g
```

#### 2.3.4.8 支持正则表达式的 String 对象的方法

**1. search  => 检索与正则表达式相匹配的值(返回第一个匹配到的位置）**
```javascript
let str = 'hello everybody!';
let reg = /l/i;
str.search(reg) //2
reg = /f/g;
str.search(reg)  //-1
```

**2. match  => 找到一个或多个正则表达式的匹配。（返回匹配到的值）**
```javascript
let str = 'hello everybody!';
let reg = /l/g;
str.match(reg) //["l", "l"]
reg = /f/g;
str.match(reg)  //null
```

**3. replace  => 替换与正则表达式匹配的子串（返回替换后的整个字符串,改变原字符串）**
```javascript
let str = 'hello everybody!';
let reg1 = /l/;
str.replace(reg1, 'p')  //"heplo everybody!"
str = 'hello everybody!';
let reg2 = /l/g;
str.replace(reg2, 'p')  //"heppo everybody!"
```
**4. split  => 在符合 separator 的位置把字符串分割为字符串数组。**
```javascript
let str = 'hello everybody!';
let reg = /e/g;
str.split(reg)  //["h", "llo ", "v", "rybody!"]
```