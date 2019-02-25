# react navigation



## 切换页面

- `this.props.navigation.navigate('RouteName')`新路由推送到堆栈导航器，如果它尚未在堆栈中，则跳转到该页面。

- 我们可以多次调用` this.props.navigation.push('RouteName') `，并且它会继续推送路由。

- ` this.props.navigation.goBack() `

- ` this.props.navigation.popToTop() `

- ` navigation ` prop适用于所有屏幕组件（组件定义为路由配置中的屏幕，并且被 React Navigation 渲染为路由）。



## 传递参数给路由

- 传参：`this.props.navigation.navigate('RouteName', {paramName: 'value'})`

- 接受：this.props.navigation.state.params访问 params 对象。 如果没有提供参数，这可能是null，所以使用this.props.navigation.getParam通常更容易，所以你不必处理这种情况。`const otherParam = navigation.getParam('otherParam', 'some default value');`




## 配置标题栏

- 每个页面组件可以有一个名为navigationOptions({ navigation, navigationOptions, screenProps })的静态属性，它是一个对象或一个返回包含各种配置选项的对象的函数。

- 跨页面共享通用的配置标题栏： defaultNavigationOptions 

- navigationOptions 还可用于配置 navigator 自身。

- this.props.navigation.setParams

- 使用自定义组件替换标题




## 标题栏按钮的配置

