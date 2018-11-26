> React经过数个版本迭代，除了具备基本view描述及渲染能力外，也新出很多新特性

### React context

主要为了解决多层嵌套传参问题，部分不是很复杂的业务就没必要接入redux了

```javascript
// 通过createContext创建，返回两个React组件
var { Provider, consumer } = React.createContext(defaultColor);


<Provider value={color} >
    <consumer>
        {color => <p>{color}<p>}
    <consumer>

    <consumer>
        {color => <div>{color}<div>}
    <consumer>
</Provider>
```

### React.Fragments

用于返回array组件，不需要用额外标签包裹

```javascript
<>
    <li></li>
</>

<React.Fragments>
    <li></li>
</React.Fragments>
```


### Portals

用于插入组件节点至任意位置，适用于pop，alert等场景

```
class Pop extends Component {
    render () {
        return React.CreatePortal(
            this.props.children,
            domNode
        )
    }
}

<Pop>
    <div> pop content </div>
</Pop>
```

### Error Boundaries

React中的try catch机制，可以直接在应用根目录挂载，防止由于JS报错引起的页面崩溃

```javascript
componentDidCatch(err, info) {
    // 处理页面崩溃展示样式
    this.setState({ hasError: true });
    console.log(info);
}
```

### Strict Mode

作用类似于JS中的strict mode，只在开发模式中生效，对开发中存在的风险进行提示

```
    <div>
        <React.StrictMode>
            <App />
        </<React.StrictMode>
    </div>
```

### hooks v16.7

```
    // 暂时放在timeLine里面，快学不动了~
```