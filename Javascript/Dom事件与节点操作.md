https://juejin.im/post/5af43bd5f265da0b8336c6f7

### DOM0 与 DOM2

```javascript
dom.onClick= function() {};
dom.addEventListner('click', callback, false); || attachEvent(IE8以下)
```

历史：
IE远古时期坚持使用事件冒泡。netscape坚持使用事件捕获。

后经IE0进行统一，后衍生出DOM2

onClick与addEventListner区别:
    1. onClick只能进行事件冒泡捕获
    2. onClick只同种类型事件，只能绑定一个
    3. 无法解除相应绑定


### 捕获冒泡阶段

 1. 当节点事件被触发，首先执行捕获流程，遇到注册的捕获事件立即触发执行
 2. 找到target节点，无论是捕获还是冒泡，谁先注册先执行
 3. 执行事件冒泡，遇到冒泡事件就触发执行

![](https://lc-gold-cdn.xitu.io/a8d6c4231abb6134a7d1.png?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)

### 事件委托

> 当事件绑定到父级稳定节点，监听处理子节点的事件。

关键点 - `event.target`

1. 减少内存消耗。

2. 动态更改子节点，不需要重新进行绑定


```javascript
// 给父层元素绑定事件
    document.getElementById('list').addEventListener('click', function (e) {
        // 兼容性处理
        var event = e || window.event;
        // 拿到目标元素dom对象
        var target = event.target || event.srcElement;
        // 判断是否匹配目标元素 
        if (target.nodeName.toLocaleLowerCase === 'li') {
            console.log('the content is: ', target.innerHTML);
        }
    }
);
```

匹配的时候还可以使用`target.matches(#list.li)`来进行精准匹配


### 事件委托局限性

1. focus、blur 之类的事件本身没有事件冒泡机制，所以无法委托；

2. mousemove、mouseout 这样的事件，虽然有事件冒泡，但是只能不断通过位置去计算定位，对性能消耗高，因此也是不适合于事件委托的；


### 如何判断是否是子节点

```javascript
// 方法一
function isChildOf(child, parent) {
    var parentNode;
    if(child && parent) {
        parentNode = child.parentNode;
        while(parentNode) {
            if(parent === parentNode) {
                return true;
            }
            parentNode = parentNode.parentNode;
        }
    }
    return false;
}

// 方法二
parentNode.contains(childNode) 
```

### 节点操作

查询节点：

* document.getElementById(id)   // 根据ID
* document.getElementsByTagName()   // 根据Tag
* document.getElementsByClassName()  // 根据class
* 
* document.querySelector()
* document.querySelectorAll() // 区别，内容更改，会自动更新

获取父元素:

> element.parentNode // 父元素


获取子元素: 

> element.childNodes // 子元素

获取兄弟节点:

> element.previousSibling // 前兄弟节点
> element.nextSibling // 后兄弟节点

创建DOM:

> document.createElement()

插入节点:

* paranetElement.appendChild(child)  // 插入到最后
* paranetElement.insertBefore(newElement, A) // 插入到A节点前
* parentDiv.insertBefore(sp1, A.nextSibling); // 插入A节点后

删除节点:

* paranetElement.removeChild()

修改节点:

* element.innerHTML
* element.cssAttribute
* element.setAttribute() 
* element.removeAttribute() 
* element.className