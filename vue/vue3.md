### 新特性
- composition API setup中
  - ref 单值响应式,改变值用 value取值
  - toRefs 将对象中的每一个属性转化成单值响应式
  - reactive 对象响应式
  - onMounted 组件挂载执行，是一个回调函数
  - onUnmounted 组件卸载执行，是一个回调函数
  - computed  用法改变，计算属性
    - 一个参数:监听的参数
  - watch 比computed多了一个回调函数，用法改变
    - 第一个参数： 监听的参数
    - 第二个参数： 回到函数 oldval-newval
```js
import { computed, onMounted, onUnmounted, reactive, ref, watch } from 'vue'
export default {
  name: 'HelloWorld',
  setup () {
    const msg = ref('1')
    const msg2 = computed(() => msg.value * 2)
    const data = doubleData()
    let timer
    onMounted(() => {
      console.log(msg)
      timer = setInterval(() => msg.value++, 1000)
    })
    // 第一个参数，想要简写必须是单值或者是多值响应式，否则需要写箭头函数
    watch(data, () => {
      console.log(msg.value + '---' + data.a)
    })
    onUnmounted(() => {
      clearInterval(timer)
    })
    const desc = ref(null)
    onMounted(() => {
      let p = desc.value
      p.innerHTML = '9999999'
    })
    return { msg, msg2, data, desc }
  }
}
function doubleData () {
  const data = reactive({
    a: 1,
    b: computed(() => data.a++),
    d: {
      name: 'xiner'
    }
  })
  onMounted(() => {
    setInterval(() => {
      data.a++
      data.c = data.a * 4
      data.d.name = `lili-----${data.a}`
    }, 1000)
  })
  return data
}
```
- Teleport 模态弹框,可以追加到body上
- v-model 中的sync去掉了
- 渲染函数h、nextTick需要引用，才可以使用，更好的tree shaking



### 移除的api