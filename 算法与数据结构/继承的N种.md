继承的作用是既能通过原型上定义的方法实现复用，又能保证每个实例都有自己属性
```javascript
1）原型链继承  问题，1.原型中的引用类型会被所有实例所引用 2.创建子类型不能向超类型传递参数
function SuperType() {
    this.property = true;
    this.color = ['blue', 'red']
}
SuperType.prototype.getSuperValue = function() {
    return this.property;
}
function SubType(name) {
    this.subproperty = false;
    this.name = name;
}
SubType.prototype = new SuperType();
SubType.prototype.getSubvalue = function() {
    return this.subproperty;
}


2）构造函数继承   解决了上面的1，2两个问题,缺点不能使用父级的原型方法
function SuperType(name) {
    this.color = ['red', 'blue'];
    this.name = name;
}
function SubType(name) {
    // 继承了 SuperType
    SuperType.call(this, name);
}


3）组合继承(最常用) 综合上面两个,利用原型链实现方法和原型属性的继承，利用构造函数实现实例属性的继承.缺点，两次调用父类构造函数
function SuperType(name) {
    this.name = name;
}
SuperType.prototype.sayName = function() {
    alert(this.name);
}
function SubType(name, age) {
    SuperType.call(this, name);      // 第二次调用
    this.age = age;
}
SubType.prototype = new SuperType();     // 第一次调用
SubType.prototype.constructor = SubType;
SubType.prototype.sayAge = function() {
    alert(this.age);
}
var instance = new SubType('allen', 11);
instance.sayAge();
instance.sayName();
```