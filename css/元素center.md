- calc 实现(知道元素的宽高)
```css
body{
  padding: 0 calc(50% - 500px);
}
#app{
  width:1000px;
  height:1000px;
  background-color:cyan;
}
```
- margin + absolute 实现
```css
body{
  width: 100%;
  height: 100vh;
}
#app{
  width: 500px;
  height: 500px;
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  margin: auto;
  background-color: cyan;
}
```
- absolute + transform 实现
```css
body{
  width: 100%;
  height: 100vh;
}
#app{
  width: 500px;
  height: 500px;
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
  background-color: cyan;
}
```
- flex 实现
```css
body{
  width: 100%;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}
#app{
  width: 500px;
  height: 500px;
  background-color: cyan;
}

```