如果一个组件对外界的依赖过于强，那么这个组件的移植性会很差，就像这些严重依赖 context 的组件一样。

如果一个组件的渲染只依赖于外界传进去的 props 和自己的 state，而并不依赖于其他的外界的任何数据，也就是说像纯函数一样，给它什么，它就吐出（渲染）什么出来。这种组件的复用性是最强的，别人使用的时候根本不用担心任何事情，只要看看 PropTypes 它能接受什么参数，然后把参数传进去控制它就行了。

我们把这种组件叫做 Pure Component，因为它就像纯函数一样，可预测性非常强，对参数（props）以外的数据零依赖，也不产生副作用。这种组件也叫 Dumb Component，因为它们呆呆的，让它干啥就干啥。写组件的时候尽量写 Dumb Component 会提高我们的组件的可复用性。



![](/assets/360截图18720129767263.png)

![](/assets/360截图18481118110120131.png)

![](/assets/360截图1672040381132109.png)



## 复用只是组件的基本功能，组件还有很强的代码分离性

- 由于组件良好的代码分离性 -- 组件式构建小程序




##atom插件

- lint-eslint

- atom beautify

- emmet

- snippets





##兼容并包的学习态度




##NVM

![](/assets/360截图20180402203529085.jpg)

- nvm ls

- nvm install 8.9.1

- nvm use 8.9.1




##基础知识

![](/assets/360截图20180402210605360.jpg)




##技术选型

- 构建工具

- MVVM框架选择

- 模块化设计

- 自适应方案设计

- 代码维护及复用性设计的思考




##构建工具

- 任务管理：gulp、grunt；gulp是流式的，效率高

- 编译打包：webpack

- 集成方案：fis

- 代码优化方案：prepack

- rollup

- 资源压缩、静态资源替换、模块化处理、编译处理




## MVVM框架选择

- 后端转前端Angular

- 易上手vue.js

- 生态，维护热度

- 复杂场景的性能




##模块化设计




##代码维护性及复用性设计的思考

- 需求变更     项目横向扩展能力，交互耦合解耦

- 产品迭代

- Bug定位

- 新功能开发




##项目设计与原理分析

![](/assets/360截图20180403222428244.jpg)





##CSS模块化设计

- 设计原则

     - 可复用能继承要完整
     
     ![](/assets/360截图1628072875114120.png)
     
     - 周期性迭代
     
          - 优秀的代码是模仿出来的
          
          - 优秀的代码是设计出来的
          
          - 优秀的代码是重构出来的
          
     
- 设计方法

     - 先整体后部分再颗粒化
     
     - 先抽象再具体





##JS组件设计

- 设计原则

     - 高内聚低耦合
     
     - 周期性迭代


- 设计方法

     - 先整体后部分再颗粒化
     
     - 尽可能的抽象
     
![](/assets/360截图165406065910967.png)
     
![](/assets/360截图1729050791108108.png)      

![](/assets/360截图17821111354271.png)
         
     

##自适应

- 基本概念

     - CSS像素、设备像素、逻辑像素、设备像素比
     
     - viewport
     
     - rem
     
- 工作原理

     - 利用viewport和设备像素比调整基准像素
     
     - 利用px2rem自动转换css单位
     
     



##SPA设计

- 设计意义

     - 前后端分离
     
     - 减轻服务器压力     局部刷新
     
     - 增强用户体验
     
     - Prerender预渲染优化SEO
     
- 工作原理

     - History API
     
     - Hash





##viewport

- viewport分三类： layout viewport; visual viewport; ideal viewport

![](/assets/360截图20180404231712051.jpg)






##vue-lazyload





## img标签和背景图的比较

- img请求占用资源

- 背景图片：尺寸、位置很好控制

- base64编码

- 最好使用背景图片的方式





## background: #FFF url(//www.baidu.com/xxx) center center no-repeat; background-size: auto 50%;






## 是否需要抽象成组件

- 不是由数据驱动的，不会改变

- 结构太简单，没有交互性，不具备成立组件

- 复杂度太低

- 在各个页面中频繁出现





## 组件的外容器css类可以在引用时覆盖




## vertical-align




## absolute居中；top:50%;margin-top:-xx;




## 使用dl,dt,dd代替ul,li

- 减少类名/高级选择器；活用标签做选择器

```
<dl :class="$style.item" v-for="item in items" :key="item.title">
     <dt>{{ item.title }}<span>{{ item.sub }}</span></dt>
     <dd>{{ item.rate }}</dd>
     <dd>{{ item.text }}</dd>
</dl>
```




## 容器线的实现方式

- 伪元素     伪元素来代替容器内单个容器的border

- border     不要使DOM结构复杂化

```
&:after{
     content: " ";
     box-sizing: border-box;
     height: 0;
     width: 100%;
     border-bottom: 1px solid #ddd;
     margin-left: 150px;
}
&:last-child:after{
     border-color: #fff;
}
```



## CSS视觉欺骗，可以在另一个盒子里定义一个absolute的容器，并移动到当前盒子UI的位置




## CSS模块化需要把每个类名挂载到元素上才生效



## 灵活运用nth-child

- 当前元素父节点的子元素编号

- nth-child(2n)

- nth-child(n+3)

- nth-child(-n+5)

- nth-child(odd)奇数；nth-child(even)偶数

- div:empty     空标签会被选中




## 业务组件和功能组件

- 业务组件可能时常变化




## DOM结构要严谨

- 语义结构要清楚

- 不要有浪费的DOM节点









