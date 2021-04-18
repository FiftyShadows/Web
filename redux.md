# Redux

## Redux

* 创建createStore \(state, stateChanger\)函数，createState函数会返回getState和dispatch
* 让createStore返回subscribe方法，订阅DOM的修改
* 优化性能，renderApp之前比较新旧数据，减少不必要的重新渲染，dispatch时的数据不可变性，共享结构
* Rdeucer\(纯函数\)：负责初始化state和修改state
  * reducer 是不允许有副作用的。你不能在里面操作 DOM，也不能发 Ajax 请求，更不能直接修改 state，它要做的仅仅是 —— 初始化和计算新的 state。

## React-redux

* 将context对象设置为store = createStore\(themeReducer\)
* 子组件state设置为store.getState\(\)的值
* 给子组件加入store.subscribe订阅state修改的函数
* 重大的问题
  * 有大量重复的逻辑：它们基本的逻辑都是，取出 context，取出里面的 store，然后用里面的状态设置自己的状态，这些代码逻辑其实都是相同的。
  * 对 context 依赖性过强：这些组件都要依赖 context 来取数据，使得这个组件复用性基本为零。想一下，如果别人需要用到里面的 ThemeSwitch 组件，但是他们的组件树并没有 context 也没有 store，他们没法用这个组件了。

我们把这种组件叫做 Pure Component，因为它就像纯函数一样，可预测性非常强，对参数（props）以外的数据零依赖，也不产生副作用。这种组件也叫 Dumb Component，因为它们呆呆的，让它干啥就干啥。写组件的时候尽量写 Dumb Component 会提高我们的组件的可复用性。

* 我们把这个高阶组件起名字叫 connect，因为它把 Dumb 组件和 context 连接（connect）起来了

```javascript
export const connect = (mapStateToProps) => (WrappedComponent) => {
  class Connect extends Component {
    static contextTypes = {
      store: PropTypes.object
    }

    constructor () {
      super()
      this.state = { allProps: {} }
    }

    componentWillMount () {
      const { store } = this.context
      this._updateProps()
      store.subscribe(() => this._updateProps())
    }

    _updateProps () {
      const { store } = this.context
      let stateProps = mapStateToProps(store.getState(), this.props) // 额外传入 props，让获取数据更加灵活方便
      this.setState({
        allProps: { // 整合普通的 props 和从 state 生成的 props
          ...stateProps,
          ...this.props
        }
      })
    }

    render () {
      return <WrappedComponent {...this.state.allProps} />
    }
  }

  return Connect
}
```

* mapDispatchToProps方法返回一个对象，对象定义了方法去dispatch store的改变，但当前组件并没有dispath函数，需要传递给高阶组件，在高阶组件的\_updateProps方法里调用mapDispatchToProps\(dispatch, this.props\)获取到返回的对象，在回传给组件，组件可以在事件当中直接调用方法了
* 通过Provider组件定义context，减少代码的耦合

