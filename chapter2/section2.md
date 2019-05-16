## 2.2 引用类型
### 2.2.1 创建对象
```javascript
//“构造函数”语法创建
let info = new Object()
//“字面量”语法创建 —— 常用
let info = {
    name: 'jane',   //键"name",值"jane"
    age: 17 //键"age",值17
}
```

### 2.2.2 对象操作
先创建一个对象
```javascript
let info = {
    name: 'jane',   //键"name",值"jane"
    age: 17 //键"age",值17
}
```
#### 2.2.2.1 添加属性
```javascript
//使用 .
info.address = 'beijing'//"beijing"，此时的 info:{name: "jane", age: 17, address: "beijing"}

//使用 []
info['friend'] = 'tom'//"tom"，此时的 info:{name: "jane", age: 17, address: "beijing", friend: "tom"}
```

#### 2.2.2.2 计算属性
**计算属性** —— 在对象字面量中使用方括号，方括号内可以是任何属性名或变量

```javascript
let s = 'sch'.concat('ool);
info[s] = 'HIT';//此时的 info：{name: "jane", age: 17, school: "HIT"}
```

#### 2.2.2.3 删除属性
```javascript
delete info.age//true，此时的 info:{name: "jane", address: "beijing", friend: "tom"}
```

#### 2.2.2.4 获取对象属性值
```javascript
//使用 .
info.address//"beijing"

//使用 []
info['friend']//"tom"
```

### 2.2.3 对象常用方法
先创建一个对象
```javascript
let info = {
    name: 'jane',   //键"name",值"jane"
    age: 17 //键"age",值17
}
```

#### 2.2.3.1 属性检查
**1. hasOwnProperty** —— object.hasOwnProperty(propertyName),propertyName 必须为字符串
```javascript
info.hasOwnProperty('name') //true
info.hasOwnProperty('language') //false
```

**2. "key" in object** —— key 为要检测的属性
```javascript
"name" in info  //true
"language" in info  //false
```




  constructor：保存着用于创建当前对象的函数。对于前面的例子而言，构造函数（constructor）
就是Object()。
  hasOwnProperty(propertyName)：用于检查给定的属性在当前对象实例中（而不是在实例的原型中）是否存在。其中，作为参数的属性名（propertyName）必须以字符串形式指定（例如：o.hasOwnProperty("name")）。
  isPrototypeOf(object)：用于检查传入的对象是否是传入对象的原型
  propertyIsEnumerable(propertyName)：用于检查给定的属性是否能够使用for-in 语句来枚举。与hasOwnProperty()方法一样，作为参数的属性名必须以字符串形式指定。
  toLocaleString()：返回对象的字符串表示，该字符串与执行环境的地区对应。
  toString()：返回对象的字符串表示。
  valueOf()：返回对象的字符串、数值或布尔值表示。通常与toString()方法的返回值相同。
由于在ECMAScript 中Object 是所有对象的基础，因此所有对象都具有这些基本的属性和方法。

