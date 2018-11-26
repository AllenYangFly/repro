https://juejin.im/post/5b10dd36e51d4506e04cf802
https://juejin.im/post/5b0638a9f265da0db53bbb6d

diff 算法、最短编辑算法

### 什么是virtual dom？

DOM 节点有太多的原生属性，节点操作是很耗费性能的一件事情。virtualDOM的主要思想就是模拟DOM的树状结构，在内存中创建保存映射DOM信息。

### diff算法

因为DOM 是多叉树的结构，如果需要完整的对比两颗树的差异，那么需要的时间复杂度会是 O(n ^ 3)，这个复杂度肯定是不能接受的。于是 React 团队优化了算法，实现了 O(n) 的复杂度来对比差异。

#### 同层级diff
react中diff算法只比较同济中的节点。

![](https://image-static.segmentfault.com/128/689/1286899590-56d41b839c27f_articlex)

#### 不同类型diff:
![](https://image-static.segmentfault.com/102/412/1024122964-56d474407bae6_articlex)
如果组件类型更改，React就不在进行计算，直接老节点，新建一个新节点。


虚拟 DOM 算是准备 React 知识时一个必定要准备的知识点，可以直接搜到很多文章，我在准备时因为时间充足，所以重点看了 React keys 的作用，以及由 keys 引发的一个数组发生了增加、删除、移动操作，如何根据前后两个数组算出具体由哪些步骤可以从之前的数组到之后的数组

#### 列表diff:
![](https://image-static.segmentfault.com/173/235/1732357161-56fe3484ebdaf_articlex)
在没有key值的列表diff中，只能通过按顺序进行每个元素的对比，更新，插入与删除，在数据量较大的情况下，diff效率低下。借助key属性，可以大大提升diff效率。

### 没有key时
这时如果每个节点都没有唯一的标识，React 无法识别每一个节点，那么更新过程会很低效
![](https://static001.infoq.cn/resource/image/c8/f9/c870788f72025a49a6781c5135df38f9.png)


### Fiber

https://tech.youzan.com/react-fiber/