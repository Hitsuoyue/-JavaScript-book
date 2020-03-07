### 3.2.4 RegExp
RegExp 是 JavaScript 内置的正则表达式对象，用来对字符串进行匹配。
#### 3.2.4.1 定义正则表达式
1）字面量语法：/pattern/attributes

2）创建 RegExp 对象的语法：new RegExp(pattern, attributes);

#### 3.2.4.2 参数
1) pattern 是一个字符串，指定了正则表达式的模式或其他正则表达式。
2) attributes 是一个可选的字符串，包含属性 "g"、"i" 和 "m"，分别用于指定全局匹配、区分大小写的匹配和多行匹配。如果 pattern 是正则表达式，而不是字符串，则必须省略该参数。

#### 3.2.4.3 修饰符
```
i  执行对大小写不敏感的匹配。
g  执行全局匹配（查找所有匹配而非在找到第一个匹配后停止）。
m  执行多行匹配。
```

#### 3.2.4.4 方括号——查找某个范围内的字符
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

#### 3.2.4.5 元字符（Metacharacter）——拥有特殊含义的字符
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

#### 3.2.4.6 量词
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

#### 3.2.4.7 RegExp 对象方法
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

#### 3.2.4.8 支持正则表达式的 String 对象的方法

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