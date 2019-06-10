## 方式一

1. 路由表中`<Route path='/sort/:id '   component={Sort}></Route>`

2. Link处 HTML方式`<Link to={ ' /sort/ ' + ' 2 ' }  activeClassName='active'>XXXX</Link>`

3. JS方式 this.props.history.push(  '/sort/'+'2'  )

4. sort页面  通过  this.props.match.params.id        就可以接受到传递过来的参数（id）



## 方式二 通过query前提：必须由其他页面跳过来，参数才会被传递过来

1. 路由表中`<Route path='/sort' component={Sort}></Route>`

2. Link处 HTML方式`<Link to={{ path : ' /sort ' , query : { name : 'sunny' }}}>`

3. JS方式 this.props.history.push({ pathname : '/sort' ,query : { name: ' sunny'} })

4. sort页面 this.props.location.query.name



## 方式三 同query差不多，只是属性不一样，而且state传的参数是加密的，query传的参数是公开的，在地址栏

1. 路由表中`<Route path='/sort' component={Sort}></Route>`

2. Link处 HTML方式`<Link to={{ path : ' /sort ' , state : { name : 'sunny' }}}>`

3. JS方式 this.props.history.push({ pathname : '/sort' ,state: { name: ' sunny'} })

4. sort页面 this.props.location.state.name




## 方式四

- 通过sessionStorage.setItem设置缓存数据，传递复杂数据，避免浏览器前进后退获取不到数据

