https://juejin.im/post/5ab6fb156fb9a028b6177931

Events模块是nodejs的核心模块，是node实现事件驱动的基础，node中几乎所有的模块(如http, fs等)都继承该模块；

只要继承EventEmitter类，就可拥有事件注册、触发事件等，所有能触发事件的对象都是EventEmitter类的实例, 例如：

* net.Server 对象会在每次有新连接时触发事件；
* fs.ReadStream 会在文件被打开时触发事件；
* 流对象 会在数据可读时触发事件；

实现一个EventEmitter，实现on, emit, once

```javascript
// 发布订阅类
class EventEmitter {
  _event = {}

  // on 函数用于绑定
  on(eventName, handler) {
    let listeners = this._event[eventName];
    if(!listeners || !listeners.length) {
      this._event[eventName] = [handler];
      return;
    }
    listeners.push(handler);
  }
  // off 用于移除
  off(eventName, handler) {
    let listeners = this._event[eventName];
    this._event[eventName] = listeners.filter(l => l !== handler);
  }
  // emit 用于分发消息
  emit(eventName, ...args) {
    const listeners = this._event[eventName];
    if(listeners && listeners.length) {
      for(const l of listeners) {
        l(...args);
      }
    }
  }
  // 订阅以后，emit 发布执行一次后自动解除订阅
  once (eventName, handler) {
    var that = this;
    function func () {
      var args = Array.prototype.slice.call(arguments,0);
      handler.apply(that, args);
      this.off(eventName,func);
    }
    this.on(eventName, func);
  }
}

const event = new EventEmitter;
export { event };
```
