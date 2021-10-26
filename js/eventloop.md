### 事件循环
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