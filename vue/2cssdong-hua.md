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



## 同时使用过渡和动画

```
<transition
  :duration
>
  <div v-show="show">Hello World</div>
</transition>
```