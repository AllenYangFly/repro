```javascript
// 检测一个对象是否是另一个对象的原型
var d = new Date();
Date.prototype.isPrototypeOf(d);//=>true
d instanceof Date;//=>true

// 判断是否是继承属性                                           
d.hasOwnProperty('toString')

// 获取实例obj的原型
d.getPrototypeOf() === Date.prototype
```

![](https://raw.githubusercontent.com/mqyqingfeng/Blog/master/Images/prototype5.png)

![](https://raw.githubusercontent.com/mqyqingfeng/Blog/master/Images/prototype2.png)

```javascript
person.__proto__ === Person.prototype

Person === Person.prototype.constructor

person.getPrototypeOf() === Person.prototype
```