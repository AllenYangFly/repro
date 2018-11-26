https://segmentfault.com/a/1190000012233339

> 通过链式调用，解决回调地狱

### 创建promise对象
```javascript
var p = new Promise((resolve, reject) => {
    resolve(data);
});
```

### Promise调用
Promise#then(resolvetion, rejection);
Pormise#catch();

```javascript
p.then(data => {
    return data
}, err => {
    return err
}).then(data => {
    console.log(data);
}).catch(err => {

})
```
catch()会收到整个promise链中的异常，而then中的第二个参数rejection，只会作用于本promise

### 直接返回
`Promise.resolve`，`Promise.reject` 方法主要是将一个值转变为一个Promise对象，然后使它具有Promise的一些方法和特性

Promise.resolve();
Promise.reject();

### 原生方法
```javascript
// 当列表中所有都执行完，会返回一个data列表
Promise.all([p1,p2,p3])

// 返回先执行完的Promise中的数据
Promise.race([p1,p2,p3])
```

### 链式调用
```javascript
let p1 = new Promise((resolve, reject) => {
    let flag = Math.random() > 0.5 ? true : false;
    resolve();
});
// @2 使用then方法进行链式的调用
p1.then(() => {
    return 1;
}).then((result) => {
    console.log(result);
    return 'hello'
}).then((result) => {
    console.log(result);
});

// @3 在then方法内部可以再次使用异步的操作
p1.then(() => {
    console.log('******');
    let p1 = new Promise((resolve, reject) => {
        setTimeout(() => {
            resolve(123);
        }, 1000);
    });
    return p1;
}).then((result) => {
    console.log(result);
});
```

### generator / async * await

```javascript
function * readFile() {
    let file = yield readFile('/etc/fstab'); 
}

async function() {
    let file = awiat readFile('/etc/fstab'); 
}
```

区别:

* 内置执行器。
  Generator 函数的执行必须靠执行器，所以才有了co模块，而async函数自带执行器。
* 更广的适用性。
  co模块约定，yield命令后面只能是 Thunk 函数或 Promise 对象，而async函数的await命令后面，可以是 Promise 对象和原始类型的值（数值、字符串和布尔值，但这时等同于同步操作）。
* 返回值是 Promise。
  async函数的返回值是 Promise 对象，这比 Generator 函数的返回值是 Iterator 对象方便多了。你可以用then方法指定下一步的操作。

  进一步说，async函数完全可以看作多个异步操作，包装成的一个 Promise 对象，而await命令就是内部then命令的语法糖。

#### co源码
```javascript
function co(gen) {
    var it = gen();
    var ret = it.next();
    ret.value.then(function(res) {
        it.next(res);
    });
}

function sayhello() {
    return Promise.resolve('hello').then(function(hello) {
        console.log(hello);
    });
}

co(function *helloworld() {
    yield sayhello();
    console.log('world');
});
```

