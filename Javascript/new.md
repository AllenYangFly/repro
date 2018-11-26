```javascript
function Fun() {
  //new做的事情
  var obj = {};
  obj.__proto__ = Fun.prototype;//Base为构造函数
  obj.name = 'Damonare';
  ...//一系列赋值以及更多的事
  return obj
}
```

* 创建一个临时对象
* 给临时对象绑定_proto_。指向原型
* 给临时对象对应的属性赋值
* 将临时对象return

也就是说new其实就是个语法糖，this之所以指向临时对象还是没逃脱上面说的几种情况。


箭头函数中的 this 只和定义它时候的作用域的 this 有关，而与在哪里以及如何调用它无关，同时它的 this 指向是不可改变的