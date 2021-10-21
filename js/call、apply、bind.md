## 改变this指向call、apply、bind
- call 接受多个参数，第一个参数代替执行的this，后面的都是函数传入的参数----会立即执行函数
```js
Function.prototype.wcall = function(content = window){
	// 给原对象增加一个属性，并赋值给被执行的函数
	content.fn = this
	// 拿到除了第一个参数之外后面的参数
	let rest = [...arguments].slice(1)
	// 拿到函数的执行结果
	let result = comntent.fn(rest)
	// 删除创建的属性值，防止影响原对象
	delete content.fn
	return result
}
```
- apply 接受两个参数，第一个参数代替执行的this，第二个参数是一个数组----会立即执行函数
```js
Function.prototype.wapply = function(content = window){
	content.fn = this
    let rest = arguments[1] || []
    let result = content.fn(...rest)
    delete context.fn
    return result
}
```
- bind接受多个参数，第一个参数代替执行的this，后面的参数是返回函数的接受参数----返回一个函数(且返回函数的原型上会有原函数的属性和方法)
```js
Function.prototype.bind2 = function(content) {
	if(typeof this != "function") {
        throw Error("not a function")
    }
    // 若没问参数类型则从这开始写
    let fn = this;
    let args = [...arguments].slice(1);
    
    let resFn = function() {
        return fn.apply(this instanceof resFn ? this : content,args.concat(...arguments))
    }
    function mid() {}
    mid.prototype = this.prototype
    resFn.prototype = new mid()
    return resFn
}
```
总结: 
- 对于call、apply，拿到传参(除了第一个)，执行函数(利用this代替),返回函数
- bind 创建一个新函数,在函数内部返回函数的结果(将参数进行拼接),对于新函数，还需要保证与原函数原型相同则