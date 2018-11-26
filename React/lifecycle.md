> 本生命周期包含es中的生命周期，参见[掘金](https://github.com/veedrin/horseshoe/blob/master/react/%E7%94%9F%E5%91%BD%E5%91%A8%E6%9C%9F.md)

### init render（组件初始化）

* constructor()
* getDefaultProps()
* getInitialState()
* componentWillMount()
* render()
* ComponentDidMount()


### props change

* componentWillReciveProps(nextProps)
* shouldComponentUpdate(nextProps, nextState)
* componentWillUpdate(nextProps, nextState)
* render
* componentDidUpdate(prevProps, prevState)

### state change
* shouldComponentUpdate(nextProps, nextState)
* componentWillUpdate(nextProps, nextState)
* render
* componentDidUpdate(prevProps, prevState)

### unmount component (组件卸载或被销毁)

* componentWillUnmount()