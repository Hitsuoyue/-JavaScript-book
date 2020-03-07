### 3.2.1 Function
#### 3.2.1.1 函数声明：
```javascript
//1. 构造函数创建 new Function
let 函数名 = new Function(参数1, 参数2,...,参数N, 函数体)
//eg:
let sayHi = new Function("name", "message", "alert('Hello " + name + "," + message)')

sayHi3('jane','hi')//Hello jane,hi
```
**但实际的代码中不使用这种方法来创建函数，还是会用字面量的方法去创建，关于函数的详细介绍，见 [3.1 函数](../section1.md)**
