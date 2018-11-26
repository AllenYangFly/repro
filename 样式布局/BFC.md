https://juejin.im/post/59b73d5bf265da064618731d

### 什么是BFC
> BFC全称Block Formatting Context，也就是块状格式化上下文。说白了就是一个独立的渲染区域，是一块与外部毫不相干区域。

### 怎么生成BFC?
```
    1. 根元素
    2. float不为none 
    3. position为absolute或fixed
    4. display为inline-block、table-cell、flex、inline-flex
    5. overflow不为visible
```

### BFC的应用?
```
    1. 内部的Box会在内部竖直的一个接一个放置,外部的float不会影响内部元素
    2. Box垂直距离由margin决定，属于同一个BFC的两个Box的margin会相互重叠   (触发不同BFC, 防止margin重叠)
    3. 每个元素的margin box左边与包含块的左边相接触,即使存在浮动
    4. BFC区域不会与float box相重叠     (两栏布局)
    5. BFC内的子元素不会与外部元素相互影响
    6. BFC内的浮动元素，也会参与高度计算  (清理浮动)
```

### IFC
> 看了BFC的概念，我们就会知道IFC就是 Inline Formatting context。行内格式化上下文。

IFC特性
```
    1. 在IFC中，行内元素，从左到右依次排放一个接着一个。
    2. IFC中每行的高度是由每行中高度最高的元素决定的。
    3. IFC中内联元素的 margin, padding这些属性只有水平方向值有效。
```