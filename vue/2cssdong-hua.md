![](/assets/360截图17571114416583.png)

## 过渡

- 条件渲染 (使用 v-if)

- 条件展示 (使用 v-show)

- 动态组件

- 组件根节点

```
<transition>
    <p v-if="show">hello</p>
</transition>

<style>
.v-enter,
.v-leave-to {
  opacity: 0;
}
.v-enter-active,
.v-leave-active {
  transition: opacity 3s;
}
</style>
```



## 自定义动画名字和animate.css

```html
<transition enter-active-class="animated swing" leave-active-class="animated shake">
  <d v-if="currentNav === 0">123</p>
</transition>
```



## 同时使用过渡和动画

```
<transition
    type="transition"
    :duration="5000"
    :duration="{enter: 5000, leave: 10000}"
    name="fade"
    apear
    enter-active-class="animated swing fade-enter-active"
    leave-active-class="animated shake fade-leave-active"
    appear-active-class="animated swing"
>
    <div v-if="show">hello</div>
</transition>

<style>
.fade-enter,
.fade-leave-to {
  opacity: 0;
}
.fade-enter-active,
.fade-leave-active {
  transition: opacity 3s;
}
</style>
```



## js动画

- enter & leave

```html
<transition
    @before-enter="handleBeforeEnter"
    @eneter="handleEnter"
    @aftereneter="handleAfterEnter"
>
    <div v-if="show">hello</div>
</transition>

var vm = new Vue({
    el: '#root',
    methods: {
        handleBeforeEnter(el){
            el.style.opacity = 0;
        },
        handleEnter(el){
            Velocity(el, {opacity: 1}, {duration: 1000, complete: done});
        },
        handleAfterEnter(el){

        }
    }
});
```



## 多个元素或组件的过渡

- vue在两个元素切换时，会尽量的复用DOM。1.v-if的动画不会出现，加key值；2.mode="in-out"















