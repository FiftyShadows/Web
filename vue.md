##核心思想

- 数据驱动

- 组件化




##计算属性是基于它们的依赖进行缓存的，不同于表达式中调用方法。计算属性只有在它的相关依赖发生改变时才会重新求值。这就意味着只要 message 还没有发生改变，多次访问 reversedMessage 计算属性会立即返回之前的计算结果，而不必再次执行函数。




##vue实例的一些是属性

- app.$mount    app.$mount('#root')

- app.$data    app.text和app.$data.text是同一个属性

- app.$props

- app.$options    包含了默认属性和创建vue实例时传入的

    - app.$options.data.text += 1;不是直接引用$options对象的
    
    - app.$options.render = (h) => { return h('div', {}, 'new renderfunction')}
    
- app.$root    app.$root === app

- app.$children

- app.$slots

- app.$scopedSlots

- app.$refs

- app.$isServer

- app.$watch

```
const unWatch = app.$watch( 'text', (newText, oldText) => {
    console.info(`${newTExt} : ${oldText}`);
}});
setTimeout( () => unWatch(), 2000);


//另一种写法,在组件销毁时会自动unWatch
const app = new Vue({
    template: '<div ref="div">{{text}}</div>',
    data: {
        text: 0
    },
    watch: {
        text(newText, oldText){
            console.log(`${newTExt} : ${oldText}`);
        }
    }
});
```

- app.$on    

```
app.$on('test', (a, b) => {
    console.info('test emitted ${a} ${b}');
});

app.$emit('test', 1, 2)
```

- app.$once

- app.forceUpdate

    - vue是响应式框架，如果对象的属性和值没有声明，而直接赋值属性则是非响应式的，需要强制刷新；频度过高会导致性能低
    
```js
const app = new Vue({
    template: '<div ref="div">{{text}} {{obj.a}}</div>',
    data: {
        text: 0,
        obj: {}
    },
    watch: {
        text(newText, oldText){
            console.log(`${newTExt} : ${oldText}`);
        }
    }
});

let i = 0;
setInterval( () => {
    i++;
    app.obj.a = i;
    app.$forceUpdate();
    //app.$set(app.obj, 'a', i);
}, 1000);
```

- app.$set    app.$set(app.obj, 'a', i);这种方式data的赋值仍然是响应式的

- app.$delete    防止内存溢出

- app.$nextTick





##生命周期方法

- beforeCreate    获取不到this.$el

- created

- beforeMount    app.$mount有关系；服务端渲染时不会被调用，因为没有DOM执行环境

- mounted

- beforeUpdate    数据更新

- updated

- actived

- deactived

- beforeDestroy    app.$destroy主动销毁实例，解除所有的事件监听和所有的watch

- destroyed

- render    将template转化为render function;在beforeMount后执行

- renderError    开发时才会被调用;只在本组件

- errorCaptured    用在正式环境里，可收集子组件错误，除了子组件停止掉向上冒泡

```
render(h){
    throw new TypeError('render error');
    return h('div', {}, this.text)
}
renderError(h, error){
    return h('div', {}, err.stack)
}
errorCaptured(){}{
    //会向上冒泡，并且正式环境可以使用
}
```




##数据绑定

- template模板插值表达式不能使用if else，可使用：

    - 全局对象    能访问绑定在this上的所有值和白名单（默认的js全局对象）如Date.noew()
    
    - 单一节点作为根节点
    
- 通过指令v-html解析变量中html标签

- v-bind:id="aaa"    :id="aaa"    

    - :class="{active: isActive}"
    
    - :class="[isActive ? 'active' : '']"
    
    - :class="[{active: isActive}]"
    
    - 计算属性
    
    - ：style="[]"    自动加前缀


- v-on:click="handleClick"    @click=""    自动判断dom节点使用addEventListener；组件使用$on

- v-text    等价于插值表达式

- v-html    可解析html标签

- v-model    双向绑定    .number    .trim    .lazy(类似于onBlur)

- v-show    display:none;控制样式

- v-if    不显示则节点不存在；动态的增删节点

- v-for    遍历数组/对象；

    - 数组`<li v-for="(item, index) in arr" :key="">{{item}}: {{index}}</li>`
    
    - 对象`<li v-for="(val, key, index) in arr">{{val}}: {{key}}: {{index}}</li>`
    
- v-pre    不解析插值表达式

- v-cloak    数据没渲染完成不显示，类似于AngularJS的ng-cloak;打包构建的vue项目用不到

- v-once    插值表达式的值只渲染一次，不再更新
    
    
```
//动态改变arr值
<div>
    <input type="checkbox" :value="1" v-model="arr">
    <input type="checkbox" :value="2" v-model="arr">
    <input type="checkbox" :value="3" v-model="arr">
</div>
<div>
    <input type="radio" :value="1" v-model="arr">
    <input type="radio" :value="2" v-model="arr">
    <input type="radio" :value="3" v-model="arr">
</div>



new Vue({
    el: '#root',
    data: {
        arr: [1, 2, 3]
    }
});
```

















##计算属性

- computed缓存，优化性能

- methods没有缓存

- 像变量一样访问，类似于object.defineproperty的get和set方法

- 处理数据，数据拼接




##watch

- 监听到数据变化，做一些操作；不适用于数据处理

- immediate    false时绑定时不会执行，只有数据变化时才会执行

- deep    默认只监听对象引用地址的变化；deep遍历对象属性并监听值变化；性能开销较大

- watch/computed里修改监听的data的值会导致死循环

```
watch: {
    obj: {
        handler(newName, oldName){
            console.info('ong.a changed');
        },
        immediate: true,
        deep: true
    }
}
````















