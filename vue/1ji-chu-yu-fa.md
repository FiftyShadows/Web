通过数组下表的方式修改数据并不会触发DOM重新渲染，触发数组重新渲染的方法有push,pop,shift,unshift,splice,sort,reverse

想要修改数组中的某一项，通过vue.list.splice(1, 1, {id: '333', text: 'Dell1'})；或者改变数组引用的地址;vue.set

可用template作为占位符，在列表渲染的时候

遍历对象，v-for="(item, key, index) of userinfo"，通过改变对象引用地址的方式给对象添加数据；或者vue.set(vue.userinfo, 'address', 'beijing')


computed方法的get,set方法；get依赖的值变化，会重新计算


计算属性computed(缓存值) > 侦听器watch(缓存值) > 方法methods


v-html能够解析DOM节点


v-if/else 重新渲染页面的时候vue会尽量的复用页面上的DOM，key值做区分

v-show在DOM上一直存在，对于需要频繁显示和隐藏的元素性能会更高

v-if不会存在



## vue的样式绑定

- `:class="{actived: isActivated}"`

- `:class="[activited, error]"`

- `:style="styleObj"    styleObj:{color: "red"}`

- `:style="[styleObj, {fontSize: '20px'}]"`




##模板语法

- mustache语法： {{msg}}

- html赋值：v-html=""

- 绑定属性：v-bind:id=""

- 使用表达式：{{ok? 'YES': 'NO'}}

- 文本赋值：v-text=""

- 指令：v-if=""

- 过滤器：{{ message | capitalize}}和v-bind:id="rawld | formatid"




##class和style绑定

- 对象语法：v-bind:class="{active: isActive, 'text-danger': hasError}"

- 数组语法`<div v-bind:class="[activeClass, errorClass]"></div>`

- style绑定





##条件渲染

- v-if

- v-else

- v-else-if

- v-show

- v-cloak





##事件处理器

- v-on:click="greet"或者 @click="greet"

- 修饰符：v-on:click.stop阻止冒泡;prevent阻止默认事件、self自身触发、once绑定一次

- v-on:keyup.enter

    - tab
    
    - delete捕获删除和退格
    
    - esc
    
    - space
    
    - up
    
    - down
    
    - left
    
    - right
    
    
    
    
    
##组件

- 全局组件和局部组件

- 父子组件通讯-数据传递

- slot






##路由特点

- 优点：用户体验好，不需要每次都从服务器全部获取，快速展现给用户

- 缺点：

    - 不利于SEO
    
    - 使用浏览器的前进，后退键的时候会重新发送请求，没有合理地利用缓存
    
    - 单页面无法记住之前滚动的位置，无法在前进，后退额时候记住滚动的位置
    

    
        
            
##路由基础

- vue-router用来构建SPA

- `<router-link></router-link>`或者this.$router.push({path:''})

- `<router-view></router-view>`





##动态路由匹配

- 路由模式history/hash

![](/assets/360截图20180405181228155.jpg)

![](/assets/360截图20180405180939734.jpg)




- 什么是动态路由？

    - 参数获取$route.params.goodsId

![](/assets/360截图20180405180333282.jpg)




- 嵌套路由

![](/assets/360截图20180405181555567.jpg)

![](/assets/360截图20180405181833071.jpg)
    
    

- 编程式路由
    
    - 获取参数$route.query.goodsId

![](/assets/360截图20180405182517733.jpg)






##命名路由和命名视图

- 给路由定义不同的名字，根据名字进行匹配

- 给不同的router-view定义名字，通过名字进行对应组件的渲染

![](/assets/360截图20180405184648908.jpg)

- 命名视图

![](/assets/360截图20180405185027691.jpg)

![](/assets/360截图20180405185159053.jpg)









