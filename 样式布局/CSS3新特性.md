https://juejin.im/entry/595f1e3c5188250d914dd53c

### 选择器
```
E>F 子选择器
E+F 选择紧贴在E元素之后的F元素
E~F 选择E元素所有兄弟元素F

E[attr="val"] 
E[attr~="val"] 选择具有attr属性且属性值其中一个等于val的E元素
E[attr^="val"] attr属性中以val开头的字符串的E元素
E[attr$="val"] attr属性中以val结尾的字符串的E元素
E[attr*="val"] attr属性中包含val的字符串的E元素

E:not(s) 匹配不含有s选择符的元素E
E:first-child
E:last-child
E:first-of-type
E:last-if-type

E:nth-child(n)
E:nth-of-type(n)
E:nth-last-child(n)
E:nth-last-of-type(n)
```

### 边框

### 背景

### 文字

### 渐变 Transition

渐变效果可以用贝塞尔曲线
```
// 简写
transition: transition-property transition-duration transiton-timing-function transition-dela;

transition-property: 过渡属性(默认值为all)
transition-duration: 过渡持续时间(默认值为0s)
transiton-timing-function: 过渡函数(默认值为ease函数)
transition-delay: 过渡延迟时间(默认值为0s)
```

#### Transform
translate 位移
rotate 旋转
scale 缩放
skew 斜切
Matrix 二维变换

transform-origin

#### Animation
```css
.start-run {
    animation: start-run 5000ms; 
    animation-fill-mode: forwards;
    animation-timing-function: linear;
}

@keyframes start-run {
    0% {
        transform: translate3d(0, 0, 0);
    }
    35% {
        transform: translate3d(0, 155px, 0) rotate3d(0, 0, 1, 0deg);
    }
    50% {
        transform: translate3d(20px, 224px, 0) rotate3d(0, 0, 1, -45deg);
    }
    70% {
        transform: translate3d(80px, 242px, 0) rotate3d(0, 0, 1, -90deg);
    }
    100% {
        transform: translate3d(200px, 243px, 0) rotate3d(0, 0, 1, -90deg);
    }
}
```