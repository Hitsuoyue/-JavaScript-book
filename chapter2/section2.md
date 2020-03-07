## 2.2 引用类型 —— 对象
JavaScript 中，对象是及其重要的一点。其他六种是原始类型，他们的值只包含一种东西，而对象是用来存储键值对和更复杂的实体的。
### 2.2.1 创建对象
```javascript
//“构造函数”语法创建(后面会详细介绍构造函数)
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

#### 2.2.2.5 对象的可枚举与不可枚举
对象的每个属性都有一个描述对象（Descriptor），用来控制该属性。

**Object.getOwnPropertyDescriptor()** 方法返回指定对象上一个自有属性对应的属性描述符。

（自有属性指的是直接赋予该对象的属性，不需要从原型链上进行查找的属性）

**语法：**
> Object.getOwnPropertyDescriptor(obj, prop)   
//obj：需要查找的目标对象， prop：目标对象内属性名称

```javascript
let info = {
    name: 'jane',   //键"name",值"jane"
    age: 17 //键"age",值17
}
let des = Object.getOwnPropertyDescriptor(info, 'name')
//des
{
    value: "jane", //该属性的值
    writable: true,   //当且仅当属性的值可以被改变时为true
    enumerable: true,   //当且仅当指定对象的属性可以被枚举出时，为 true
    configurable: true  //当且仅当指定对象的属性描述可以被改变或者属性可被删除时，为true
}
```
**不可枚举（enumerable:false）：** 有以下操作会忽略不可枚举的属性。
* for...in：不可枚举的属性不会被遍历。
* Object.keys()：不可枚举的属性不会被遍历。
* JSON.stringify()：不可枚举的属性不会被转换为字符串。
* Object.assign()： 不可枚举的属性不会被复制。

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

#### 2.2.3.2 对象遍历

先创建一个对象

```javascript
let info = {
    name: 'jane',   //键"name",值"jane"
    age: 17 //键"age",值17
}
Object.defineProperty(info, 'name', {
  enumerable: true //可枚举
});
Object.defineProperty(info, 'age', {
  enumerable: false //可枚举
});
//在原型链上添加属性 —— 先了解，原型链部分后再看
Object.defineProperty(info, 'eg1', {
  value: 'view',
  enumerable: true //可枚举
});
Object.defineProperty(info, 'eg2222', {
  value: 'unview',
  enumerable: false //不可枚举
})
```

**1. for ... in** —— 先遍历对象自身的可枚举属性，再遍历继承的可枚举属性。
```javascript
for (var index in info) {
  console.log('key：', index, 'value：', info[index])
}
//result 只遍历了自身及原型链上的可枚举属性
key： name value： jane
key： eg1 value： view
```

**2. Object.keys()** —— 返回自身及原型链上的可枚举属性组成的数组，可通过遍历数组来遍历对象。
```javascript
Object.keys(info)
//result 返回自身及原型链上的可枚举属性组成的数组
["name", "eg1"]

Object.keys(info).forEach(item=>{
  console.log(item, info[item])
})
//result
name jane
eg1 view
```

**3. Reflect.ownKeys()** —— 返回自身及原型链上所有属性组成的数组，可通过遍历数组来遍历对象。
```javascript
Reflect.ownKeys(info)
//result 返回自身及原型链上的所有属性组成的数组，包括不可枚举属性
["name", "age", "eg1", "eg2222"]

Reflect.ownKeys(info).forEach(item=>{
  console.log(item, info[item])
})
//result
name jane
age 17
eg1 view
eg2222 unview
```

**4. Object.getOwnPropertyNames()** —— 返回自身及原型链上所有属性组成的数组（包括不可枚举属性），可通过遍历数组来遍历对象。
```javascript
Object.getOwnPropertyNames(info)
//result 返回自身及原型链上的所有属性组成的数组，包括不可枚举属性
["name", "age", "eg1", "eg2222"]

Object.getOwnPropertyNames(info).forEach(item=>{
  console.log(item, info[item])
})
//result
name jane
age 17
eg1 view
eg2222 unview
```


