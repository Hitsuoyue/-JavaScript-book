### 3.2.2 Array
#### 3.2.2.1 创建数组
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

#### 3.2.2.2 常用方法
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
