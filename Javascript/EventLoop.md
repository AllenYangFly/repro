https://juejin.im/post/5a6309f76fb9a01cab2858b1
http://latentflip.com/loupe/?code=JC5vbignYnV0dG9uJywgJ2NsaWNrJywgZnVuY3Rpb24gb25DbGljaygpIHsKICAgIHNldFRpbWVvdXQoZnVuY3Rpb24gdGltZXIoKSB7CiAgICAgICAgY29uc29sZS5sb2coJ1lvdSBjbGlja2VkIHRoZSBidXR0b24hJyk7ICAgIAogICAgfSwgMjAwMCk7Cn0pOwoKY29uc29sZS5sb2coIkhpISIpOwoKc2V0VGltZW91dChmdW5jdGlvbiB0aW1lb3V0KCkgewogICAgY29uc29sZS5sb2coIkNsaWNrIHRoZSBidXR0b24hIik7Cn0sIDUwMDApOwoKY29uc29sZS5sb2coIldlbGNvbWUgdG8gbG91cGUuIik7!!!PGJ1dHRvbj5DbGljayBtZSE8L2J1dHRvbj4%3D


## JS中的线程

JS引擎中负责解释和执行JavaScript代码的线程只有一个，可以叫它为主线程。

除了主线程，还存在其他的线程。例如：处理AJAX请求的线程、处理DOM事件的线程、定时器线程、读写文件的线程(例如在Node.js中)等等。

### 浏览器中的eventLoop

#### 执行栈 stack

#### webapis

#### 回调队列 callback queue

#### Macrotask 宏任务队列

#### Microtask 微任务队列

Promise.then
process.nextTick
promises
Object.observe
MutationObserver

![](https://user-gold-cdn.xitu.io/2018/6/27/1643fed5a7765dd2?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)

在微任务队列清空后，事件循环会检查当前是否需要重新渲染UI，如果需要则渲染UI视图。

```
function mySetInterval(fn, millisec){
  function interval(){
    setTimeout(interval, millisec);
    fn();
  }
  setTimeout(interval, millisec)
}

```

setInterval间隔时间指的是`开始执行`的间隔时间，所以如果间隔100s，执行回调需要5m，那么两个函数的真正间隔时间是95s。

#### Node.js中的eventLoop
![](https://user-gold-cdn.xitu.io/2018/6/29/1644b17495b10980?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)

1. timers：执行满足条件的setTimeout、setInterval回调。
2. I/O callbacks：是否有已完成的I/O操作的回调函数，来自上一轮的poll残留。
3. idle，prepare：可忽略
4. poll：等待还没完成的I/O事件，会因timers和超时时间等结束等待。
5. check：执行setImmediate的回调。
6. close callbacks：关闭所有的closing handles，一些onclose事件。


真正的执行顺序
* 清空当前循环内的Timers Queue，清空NextTick Queue，清空Microtask Queue。
* 清空当前循环内的I/O Queue，清空NextTick Queue，清空Microtask Queue。
* 清空当前循环内的Check Queu，清空NextTick Queue，清空Microtask Queue。
* 清空当前循环内的Close Queu，清空NextTick Queue，清空Microtask Queue。
* 进入下轮循环。

可以看出，`nextTick` 优先级比 `promise` 等microtask高。`setTimeout` 和 `setInterval` 优先级比 `setImmediate` 高。