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

![](/assets/360截图20180405180333282.jpg)




- 嵌套路由

![](/assets/360截图20180405181555567.jpg)

![](/assets/360截图20180405181833071.jpg)
    









