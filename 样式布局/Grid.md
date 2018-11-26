> Grid出现之前，布局都是基于一维的。Grid则是二维布局。
https://www.w3cplus.com/css3/playing-with-css-grid-layout.html

Grid容器（对应Flexbox布局中的Flex容器）
Grid项目（对应Flexbox布局中的Flex项目）


### 容器属性
```css
display: grid;

// 指定网格行数、列数、网格大小
grid-template-columns: / grid-template-rows: 1fr 2fr 1fr;

// 指定网格间距
grid-gap: 5px;

// 网格内
// 定义网格子项的内容水平方向上的排列方式
justify-items:
// 定义网格内容垂直方向上的对齐方式, 类似于flex的align-items
align-items:

// 网格间
// 定义网格内容水平方向上的排列方式, 类似于flex的justify-content 
justify-content:
// 和justify-content对齐方向垂直
align-content:
```


### 子元素属性
```css
// 设置子元素起始和结束位置
grid-columns: || grid-row:

// 
grid-area:

// 横向排列方式
justify-self:

// 纵向排列方式，覆盖容器上设置的align-item，类似于flex中的align-self
align-self:
```


### 函数
```css
repeat(num, length)

grid-template-columns: repeat(9, 1fr);
```
