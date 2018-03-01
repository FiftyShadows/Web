##combineReducers()

- combineReducers() 所做的只是生成一个函数，这个函数来调用你的一系列 reducer，每个 reducer 根据它们的 key 来筛选出 state 中的一部分数据并处理，然后这个生成的函数再将所有 reducer 的结果合并成一个大的对象。没有任何魔法。正如其他 reducers，如果 combineReducers() 中包含的所有 reducers 都没有更改 state，那么也就不会创建一个新的对象。




subscribe() 返回一个函数用来注销监听器

严格的单向数据流是 Redux 架构的设计核心。

注意 reducer 是纯函数。它仅仅用于计算下一个 state。它应该是完全可预测的：多次传入相同的输入必须产生相同的输出。它不应做有副作用的操作，如 API 调用或路由跳转。这些应该在 dispatch action 前发生。

根 reducer 的结构完全由你决定。Redux 原生提供combineReducers()辅助函数，来把根 reducer 拆分成多个函数，用于分别处理 state 树的一个分支。




##处理异步

**Redux默认只处理同步，异步任务需要react-thunk中间件**

- Npm install redux-thunk -S

- 使用applyMiddleware开启thunk中间件

- Action可以返回函数，使用dispatch提交action

```js
// thunk插件的使用户主要修改action create写的方式
exprot function addGunAsync(){
    return dispatch => {
        setTimeout(() => {
            dispatch(addGun());
        });
    }
}
```


##调试工具

- 新建store的时候判断window.devToolsExtension

- 使用compose结合thunk和window.devToolsExtention

- 调试窗的redux选项卡，实时看到state

```
store = createStore(counter, compose(
    applyMiddleware(thunk),
    window.devToolsExtension? window.devToolsExtension(): undefined
));
```



##react-redux具体使用

- Provider组件在应用最外层，传入store即可，只用一次

- Connect负责从外部获取组件需要的参数

- Connect可以用装饰器的方式来写

- 复杂redux应用，多个reducer，用combineReducers合并




##使用装饰器优化connect代码

- npm run eject弹出个性化配置

- npm i babel-plugin-transform-decorators-legacy插件

- package.json里babel加上plugins配置

```
@connect(
    //你要state什么属性放到props里
    state => ({num: state}),
    //你要什么方法，放到props里，自动dispatch
    { addGun, removeGun, addGunAsync }    
)
```


##初识Router4

- npm i react-router-dom -S

- Router4使用route-router-dom作为浏览器端的路由

- BrowerRouter,包裹了整个应用

- Router路由对应渲染的组件，可嵌套

- Link跳转专用

```js
function Erying(){
    return <h2>二营</h2>
}
function Qibinglian(){
    return <h2>二营</h2>
}
ReactDom.render(
    (<Provider>
        <BrowerRouter>
            <div>
                <h1>独立团<h1>
                <ul>
                    <li><Link to='/'>一营</Link></li>
                    <li><Link to='/erying'>二营</Link></li>
                    <li><Link to='/qibingying'>骑兵连</Link></li>
                </ul>
                <Route path='/' exact component={App}></Route>
                <Route path='/erlian' component={Erying}></Route>
                <Route path='/qibingying' component={Qibingying}></Route>
            </div>
        </BrowerRouter>
    </Provider>),
    document.getElementById('root')
)
```

####其他组件

- url参数，Route组件参数可用冒号标识参数

- Redirect组件跳转

- Switch只渲染一个子Route组件






