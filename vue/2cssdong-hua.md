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

```
<transition enter-active-class="animated swing" leave-active-class="animated shake">
  <p v-if="currentNav === 0">123</p>
</transition>
```