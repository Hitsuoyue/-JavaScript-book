### 3.2.6 Math
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