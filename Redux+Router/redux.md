https://www.lingchenxuan.com/2017/07/04/Redux,-Redux-thunk-%E5%92%8C-React-Redux-%E6%BA%90%E7%A0%81%E9%98%85%E8%AF%BB/
https://juejin.im/post/5b99c7416fb9a05cf7157f2b

调用reducer然后调用subscribe的listener, 发生subscribe就调用connect传进去mapStateToProps和mapDispatchToProps

> redux的api极为简单，只暴露出5个方法
```javascript
import { createStore,  combineReducers,  compose, applyMiddleware, bindActionCreators } from 'redux';
```

### createStore(reducer, initState, enhancer) 创建store

reducer: reducer处理函数，接受一个state返回一个新的state
initState: 初始化state, 如果reducer是用combineReducer生成的，则key值需要和iniState对应
enhancer: store增强函数，可以指定middleware，时间旅行，持久化等。但是这个函数只能通过`applyMiddleware`生成。initState为空的时候，可以直接传入第二项

### applyMiddleware 组合中间件，返回一个函数

applyMiddleware会利用compose合并生成一个增强器，供createStore时使用

### compose 接受一组函数参数，从左到右多个函数，返回一个组合函数
```javascript
export default function compose(...funcs) {
  if (funcs.length === 0) {
    return arg => arg
  }
  if (funcs.length === 1) {
    return funcs[0]
  }
  /**
   * 核心语句就是这一句reduce，队列中的下一个函数b，已组合的函数a，把b作为参数扔给a，
   * 如此反复直至循环完毕。
   */
  return funcs.reduce((a, b) => (...args) => a(b(...args)))
}
```
### combineReducers 合并多个reducer，返回一个新的reducer函数给createStore用

### bindActionCreators 生成可以直接触发action的函数

### mapStateToProps，mapDispatchToProps connect