https://github.com/mqyqingfeng/Blog/issues/7

```javascript
var obj = {
    a: 1,
    b: function(){
        console.log(this);
    }
}
1、在全局环境或是普通函数中直接调用  // 指向window

4、作为构造函数   //指向实例化的对象

2、作为对象的方法   // 指向该对象

3、使用apply和call   // 指向绑定的作用域
```


http://zachrey.win/%E4%B8%BA%E4%BB%80%E4%B9%88React%E7%BB%84%E4%BB%B6%E7%82%B9%E5%87%BB%E4%BA%8B%E4%BB%B6%E5%9B%9E%E8%B0%83%E5%87%BD%E6%95%B0%E4%BC%9A%E9%9C%80%E8%A6%81%E7%BB%91%E5%AE%9Athis.html


箭头函数中的 this 只和定义它时候的作用域的 this 有关，而与在哪里以及如何调用它无关，同时它的 this 指向是不可改变的