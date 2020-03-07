### 3.2.3 Date
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

**Date.now()**

有一个特殊的方法 Date.now()，它会返回当前的时间戳，不需要整个 Date 对象。

它相当于 new Date().getTime()，但不会在中间创建一个 Date 对象。因此更快，且不会对垃圾处理造成额外的压力。

```javascript
Date.now()  //1559725827511
```
