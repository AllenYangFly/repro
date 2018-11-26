var str = 'abc';

str.chartAt(1)
str.chartcodeAt(1)

str.split(''); // 转换数组
str.slice(1, 2);  // 返回截取

str.search(/reg/, 'hello') // 寻找返回位置
str.indexOf('a') // 返回位置


### 改变原string
str.replace(/reg/, 'hello') // 替换
str.concat('defg')