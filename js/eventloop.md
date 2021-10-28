### 事件循环
浏览器自上而下执行，遇到同步的，等待执行，遇到异步的，需要看它是宏任务(setTimeout)还是微任务(promise.then catch), 宏任务先进入工作线程，执行完毕后，回调函数进入到任务队列中，微任务会进入到微任务队列;当主线程代码执行完之后，会去先看微任务队列有没有任务，有的话，执行所有的微任务，微任务执行完毕，主线程会去看任务队列有需要执行的回调函数么，有的话将其放入到主线程中，同样的遇到宏任务放入到工作线程，有回调进入任务队列，微任务进入到微任务队列，直到所有的任务都执行完毕，结束
### 面试题--美团
```js
setTimeout(() => {
    console.log(1)
}, 0)
setTimeout(() => {
    console.log(2)
}, 1000)
;(new Promise((resolve, reject) => {
    console.log(3)
    resolve()
    ;(new Promise((resolve, reject) => {
        console.log(6)
        resolve()
    })).then(() => {
        console.log(7)
    })
})).then(() => {
    console.log(8)
})
setInterval(() => {
    console.log(4)
},1000)

console.log(5)

// 输出结果
3 6 5 7 8 1 2 4 4 4 4 4 ...
```
