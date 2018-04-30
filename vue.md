



##核心思想

- 数据驱动

- 组件化




##计算属性是基于它们的依赖进行缓存的，不同于表达式中调用方法。计算属性只有在它的相关依赖发生改变时才会重新求值。这就意味着只要 message 还没有发生改变，多次访问 reversedMessage 计算属性会立即返回之前的计算结果，而不必再次执行函数。




##vue实例的一些是属性

- app.$mount

- app.$data    app.text和app.$data.text是同一个属性

- app.$props

- app.$options    包含了默认属性和创建vue实例时传入的

    - app.$options.data.text += 1;不是直接引用$options对象的
    
    - app.$options.render = (h) => { return h('div', {}, 'new renderfunction')}
    
- app.$root    app.$root === app

- app.$children

- app.$slots

- spp.$scopedSlots
    



