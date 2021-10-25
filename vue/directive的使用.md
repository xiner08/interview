自定义指令directive钩子函数
- bind 只调用一次，指令绑定到元素时调用
- inserted 被绑定元素插入父节点使用
- update 所有组件的VNode更新时调用
- componentUpdated 指令所在的VNode及其子VNode更新后调用
- unbind 只调用一次，指令与元素解绑时调用

### 拖拽指令的实现 
```js
  // 记得给定位
  Vue.directive('drag',{
    bind(el,binding,vnode){
      let isDragStart = false
      let disX = 0
      let disY = 0
      el.addEventListener('mousedown',e=>{
        disX = e.clientX - el.offsetLeft
        disY = e.clientY - el.offsetRight
        isDragStart = true
        e.preventDefault()
      })
      el.addEventListener('mousemove',e=>{
        if(isDragStart){
          let x = e.clientX - disX
          let y = e.clientY - dixY
          el.style.left = x +'px'
          el.style.top = y +'px'
        }
        e.preventDefault()
      })
      el.addEventListener('mouseup',e=>{
        isDragStart = false
      })
    }
  })
```
### 自动获取焦点指令的实现
```js
  Vue.directive('focus',{
    inserted(el){
      el.focus()
    }
  })
```