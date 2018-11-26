https://juejin.im/post/59cb6307f265da064e1f65b9

### 生命周期


### loader与plugins

loader是对不同格式的文件的处理，比如sass，jsx。通过正则匹配不同的loader，处理我们的文件。

而plugins并不是操作单个文件，它直接对整个构建过程起作用。

```javascript
babel-loader：处理js
css-loader,style-loader: 处理sass文件
file-loader: 根据文件生成md5值，一般处理图片
```

```javascript
html-webpack-plugin: 依据一个简单的index.html模版，动态更新资源，展示我们的页面
HotModuleReplacementPlugin: 


.babelrc: react-hot-loader/babel
entry: react-hot-loader/patch
if (module.hot) {
  module.hot.accept('./containers/App', () => { render(App) })
}

MiniCssExtractPlugin: 分离js，css

SplitChunkPlugin: 分离主体代码与依赖
```