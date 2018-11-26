https://github.com/AllenYangFly/codeAnywhere/blob/master/%E9%9D%A2%E8%AF%95/%E5%89%8D%E7%AB%AF%E9%9D%A2%E8%AF%95%E4%B8%89%E5%8D%83%E9%97%AE/test.html

### 字面量
```javascript
var person = { name: 'allen', age: 31 };
```

### 工厂模式
```javascript
function createPerson(name) {
    var o = new Object();
    o.name = name;
    o.getName = function () {
        console.log(this.name);
    };

    return o;
}

var person1 = createPerson('kevin');
```
缺点：不能识别对象类型，所有的实例都指向一个原型


### 构造函数
```javascript
function Person(name) {
    this.name = name;
    this.getName = function () {
        console.log(this.name);
    };
}

var person1 = new Person('kevin');
```
优点：实例可以识别为一个特定的类型
缺点：不同实例，都会新建方法。无法共享


### 原型模式
```javascript
function Person(name) {}

Person.prototype.name = 'keivn';
Person.prototype.getName = function () {
    console.log(this.name);
};
```

### 组合模式（最佳）
``` javascript
function Person(name) {
    this.name = name;
}

Person.prototype.getName = {
    console.log(this.name);
};

var person1 = new Person();
```