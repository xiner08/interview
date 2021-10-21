#### new操作符的作用:
   1. 创建一个新的对象，意思是在内存地址中会开辟一个新的空间
   2. 生成的新的对象的__proto__ 会指向构造函数的 prototype
   3. 执行构造函数，并将其this指向新对象
   4. 返回一个新的对象
   
#### 实现

```js
function New(func){
    // 1. 首先创建一个对象
    var res = {}
    // 2. 判断构造函数的prototype是否存在，存在则将新对象的__proto__ 指向构造函数的prototype
    if( func.prototype !== null ){
      res.__proto__ = func.prototype
    }
    // 3. 执行构造函数，得到一个新对象(call、apply 都会执行，bind不会)
    // Array.prototype.slice.call(arguments,1) 拿到除了构造函数后面的传进来的参数
    var result = func.apply( res, Array.prototype.slice.call(arguments,1)) 
    if((typeof result === "object" || typeof result === "function") &&typeof result !== null){
      return result
    }
    return res
  }
```
