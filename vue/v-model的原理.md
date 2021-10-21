```js
<input v-model="message" />
// 等同于
<input :value="message" @input="message=$event.target.value" />
```
相当于 输入的值赋值给绑定的值，当这个值是响应式的时候，则就成了双向数据绑定