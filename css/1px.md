### 产生原因
逻辑像素和物理像素比(设备像素比)DPR，当设计稿是1px时，指的是css像素，而根据DPR，在页面上展示的是2px，因此应该设置0.5pxcss像素

### 解决
- 新项目
```js
// 在html中,获取当前设备的DPR,根据DPR,修改viewport的属性
// 获取 meta标签
var viewport = document.querySelector("meta[name=viewport]")
// 拿到当前设备的DPR
var dpr = window.devicePixelRatio
// 修改他的属性
viewport.setAttribute('content', `width=device-width, initial-scale=${1 / dpr}, maximum-scale=${1 / dpr}, minimum-scale=${1 / dpr}, user-scalable=no`)
```
- 老项目
```css
$borderColor: #DDDEE3;
.border-1px, .border-1px-t, .border-1px-b, .border-1px-tb, .border-1px-l, .border-1px-r {
  position: relative;
}

.border-1px {
  &:before {
    content: " ";
    position: absolute;
    border: 1px solid $borderColor;
    color: $borderColor;
    left: 0;
    top: 0;
    width: 200%;
    height: 200%;
    transform-origin: left top;
    transform: scale(0.5);
  }
}

.border-1px-t {
  &:before {
    content: " ";
    position: absolute;
    border-top: 1px solid $borderColor;
    color: $borderColor;
    left: 0;
    top: 0;
    right: 0;
    height: 1px;
    transform-origin: 0 0;
    transform: scaleY(0.5);
  }
}

.border-1px-b {
  &:after {
    content: " ";
    position: absolute;
    border-bottom: 1px solid $borderColor;
    color: $borderColor;
    left: 0;
    bottom: 0;
    right: 0;
    height: 1px;
    transform-origin: 0 100%;
    transform: scaleY(0.5);
  }
}

.border-1px-tb {
  &:before {
    content: " ";
    position: absolute;
    border-top: 1px solid $borderColor;
    color: $borderColor;
    left: 0;
    top: 0;
    right: 0;
    height: 1px;
    transform-origin: 0 0;
    transform: scaleY(0.5);
  }
  &:after {
    content: " ";
    position: absolute;
    border-bottom: 1px solid $borderColor;
    color: $borderColor;
    left: 0;
    bottom: 0;
    right: 0;
    height: 1px;
    transform-origin: 0 100%;
    transform: scaleY(0.5);
  }
}

.border-1px-l {
  &:before {
    content: " ";
    position: absolute;
    border-left: 1px solid $borderColor;
    color: $borderColor;
    left: 0;
    top: 0;
    width: 1px;
    bottom: 0;
    transform-origin: 0 0;
    transform: scaleX(0.5);
  }
}

.border-1px-r {
  &:after {
    content: " ";
    position: absolute;
    border-right: 1px solid $borderColor;
    color: $borderColor;
    right: 0;
    top: 0;
    width: 1px;
    bottom: 0;
    transform-origin: 100% 0;
    transform: scaleX(0.5);
  }
}
```