> Array类型是es中最重要的数据之一，经过es6的扩充，array类型原生方法已经非常完备了，利用不同方法间的配合完全可以脱离 `lodash` 之类的函数库进行开发。

1. 转换方法—toLocaleString()方法、toString()方法、valueOf()方法
2. 栈方法——push()方法、pop()方法
3. 队列方法——shift()方法、unshift()方法
4. 重排序方法——reverse()方法、sort()方法
5. 操作方法——concat()方法、slice()方法、splice()方法
6. 位置方法——indexOf()方法、lastIndexOf()方法
7. 迭代方法——every()方法、filter()方法、forEach()方法、map()方法、 some()方法
8. 归并方法——reduce()方法、reduceRight()方法
9. includes
10. join

---
更改原数组的方法
1. push()方法、pop()方法
2. shift()方法、unshift()方法
3. 重排序方法——reverse()方法、sort()方法
4. 操作方法——splice()方法 splice(1, 3, 'aaa', 'bbb')
5. fill，fill(value, start, end)
---

不更改原数组，返回结果的方法
* [every] 遍历查找符合条件的数组项，都满足返回ture 
* [some] 遍历查找符合条件的数组项，有一个满足返回ture
* [map] 遍历数组，返回一个调用结果组成的数组
* [forEach] 遍历数组，不返回 
* [reduce / reduceRight]
* [filter] 遍历数组，返回符合条件的数组项的新数组

* [concat] 合并数组
* [silce] 浅拷贝数组slice(1,3)，拷贝返回1~3的数组项
* [join] array => string
* [Array.isArray] 返回boolean

* [indexOf / lastIndexOf]
* [includes] 是否包含，返回boolean
* [find] 参数为表达式
* [findIndex] 参数为表达式

```
var numbers = [1,2,3,4,5];
var sum = numbers.reduce(function(pre, cur, index, array) {
    return pre + cur;
}, 0);
console.log(sum);    // 15
```



###  常见面试题

如何判断是否是数组

```
// 1.instanceOf
[] instancenof Array

// 2.isArray()
[].isArray()

// 3.underscore实现
Object.prototype.toString.call(obj) === '[object Array]'

```