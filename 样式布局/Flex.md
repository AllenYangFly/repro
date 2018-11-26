> CSS3带来了布局的新特性，弹性盒模型。
> http://www.ruanyifeng.com/blog/2015/07/flex-grammar.html
> 兼容性移动端可以放开使用，PC IE9不支持

将容器设置为flex之后，子元素的float、clear、vertical-align

flex容器属性 [共6个属性]

```css
主轴方向：水平排列（默认） | 水平反向排列 | 垂直排列 | 垂直反向排列
flex-direction: row | row-reverse | column | column-reverse;

换行：不换行（默认） | 换行 | 反向换行(第一行在最后面)
flex-wrap: nowrap | wrap | wrap-reverse;

flex-direction属性和flex-wrap属性的简写形式，默认值为row nowrap
flex-flow: <flex-direction> || <flex-wrap>;

主轴对齐方式：起点对齐（默认） | 终点对齐 | 居中对齐 | 两端对齐 | 分散对齐
justify-content: flex-start | flex-end | center | space-between | space-around;

交叉轴对齐方式：拉伸对齐（默认） | 起点对齐 | 终点对齐 | 居中对齐 | 第一行文字的基线对齐
align-items: stretch | flex-start | flex-end | center | baseline;


多根轴线对齐方式：拉伸对齐（默认） | 起点对齐 | 终点对齐 | 居中对齐 | 两端对齐 | 分散对齐
align-content: stretch | flex-start | flex-end | center | space-between | space-around;
```

```css
// 区别
flex-direction: 排序方向
flex-wrap: 换行
flex-flow: <flex-direction> || <flex-wrap>

justify-content：调整水平轴上的对齐方式；
align-items：调整每一行里各个item垂直轴上的对齐方式；
align-content：调整垂直轴上各行间的对齐方式（仅在多于一行时有效）；
```
---

flex子元素容器 [共6个属性]

```javascript
// flex缩写
flex-grow, flex-shrink 和 flex-basis的简写，默认值为0 1 auto
两个快捷值：auto (1 1 auto) 和 none (0 0 auto)
flex:none | [ <'flex-grow'> <'flex-shrink'>? || <'flex-basis'> ]

放大比例：默认为0，如果有剩余空间也不放大，值为1则放大，2是1的双倍大小，以此类推
flex-grow: <number>; 

缩小比例：默认为1，如果空间不足则会缩小，值为0不缩小
flex-shrink: <number>;

项目自身大小：默认auto，为原来的大小，可设置固定值 50px/50%
flex-basis: <length> | auto;

顺序：数值越小越靠前，默认为0
order: <number>; 

项目自身对齐：继承父元素（默认） | 起点对齐 | 终点对齐 | 居中对齐 | 基线对齐 | 拉伸对齐
align-self: auto | flex-start | flex-end | center | baseline | stretch;
```

```css
// 区别
order: 子元素在父容器中的顺序
align-self: 可以覆盖掉父容器中align-item的样式

flex-grow: 放大比例
flex-shrink: 缩小比例
flex-basis: 自身元素伸缩比例
flex: <flex-grow> <flex-shrink> <flex-basis>
```
