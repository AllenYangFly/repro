https://github.com/fastCreator/MVVM
https://www.cnblogs.com/yexiaochai/p/9755844.html



### 实现一个双向事件绑定
https://juejin.im/post/5abdd6f6f265da23793c4458

```javascript
<input id="input"/>

const data = {};
const input = document.getElementById('input');
Object.defineProperty(data, 'text', {
  set(value) {
    input.value = value;
    this.value = value;
  }
});
input.onChange = function(e) {
  data.text = e.target.value;
}
```