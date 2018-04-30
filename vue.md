



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

- beforeCreate

- created

- beforeMount

- mounted

- beforeUpdate

- updated

- actived

- deactived

- beforeDestroy

- destroyed



