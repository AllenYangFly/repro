https://juejin.im/post/5bf9bb7ff265da616916e816

### 科里化
> 柯里化（curry）是一种将使用多个参数的一个函数转换成一系列使用一个参数的函数的技术。

> 作用：提高函数的适用性


```javascript
// 实现一个函数 curry 满足以下调用、
const f = (a, b, c d) => { ... }
const curried = curry(f)

curried(a, b, c, d)
curried(a, b, c)(d)
curried(a)(b, c, d)
curried(a, b)(c, d)
curried(a)(b, c)(d)
curried(a)(b)(c, d)
curried(a, b)(c)(d)

const curry = (fn) => {
    if (fn.length <= 1) return fn;

    const generator = (args, rest) => (
        !rest
        ? fn(...args)
        : arg => generator([...args, arg], rest - 1)
    );

    return generator([], fn.length);
};
```

#### 高阶函数
https://juejin.im/post/5ad6b34a6fb9a028cc61bfb3

> 高阶函数就是可以将函数作为参数的函数，因为参数可以为函数使得该函数灵活性大大增强，我们叫这种函数为高阶函数

```javascript
// es6中遍历函数的实现就大量运用高阶函数的思想
[].filter(item => item > 0);
```


### 反柯里化（uncurry）
```javascript
Function.prototype.unCurrying = function(){
    var self = this;
    return function(){
        return Function.prototype.call.apply(self, arguments);
    }
}
```