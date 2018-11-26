https://github.com/MuYunyun/reactSPA/issues/53

### 依赖分离

借助commonchunk，webpack4借助splitchunk进行主体代码与vender分离

### 根据路由分片
实现原理，router借用动态 import（dynamic import）, 进行动态组件加载。Webpack会自动据此完成代码分片，不需要任何额外的手动配置。

```javascript
const Loading = () => <div>Loading...</div>

const Home = Loadable({
  loader: () => import('../pages/home'),
  loading: Loading,
})

// 类似这样使用路由
<Router>
  <Route path="/home" component={Home} />
  <Route path="/follow" component={Follow} />
  <Route path="/tools" component={Tools} />
  <Route path="/music" component={Music} />
  <Route path="/todo" component={Todo} />
  <Route path="/album" component={Album} />
  <Route path="/editor" component={Editor} />
  <Route path="/todoList" component={TodoList} />
  <Route path="/searchEngine" component={Search} />
  <Route path="/waterfall" component={Waterfall} />
</Router>
```


1. loadble
2. output: chunkFilename: '[name].bundle.js',