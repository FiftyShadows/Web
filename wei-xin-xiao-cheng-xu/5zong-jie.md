##表单组件

- `<switch name="switch" type="switch" color="yellow" checked="true" bindchange="switch1Change"/>`

- `<slider min="0" max="500" step="50" valie="250" color="yellow" name="slider" show-value="true"></slider>`


```
<radio-group class="radio-group" bindchange="radioChange">
  <label class="radio">
    <radio value="战士" checked="true"/>战士</radio>
  </label>
  <label class="radio">
    <radio value="法师"/>法师</radio>
  </label>
  <label class="radio">
  <  radio value="牧师"/>牧师</radio>
  </label>
</radio-group>
```

- checkbox

- 小程序只能用form标签获取表单值

```
<form class="xx" catchsubmit="" catchreset="">

  <view class="">
    <button formType="submit">Submit</button>
    <button formType="reset">Reset</button>
  </view>
</form>
```


- 地图；调内置地图


- openlayers 1.x 极致的面向对象




##MINA在Page里还提供了一个onReachBottom事件，使用这个事件来监听页面上滑到底。



##运用es6的module，class，Promise,lambda 




##动画

- 创建一个动画实例animation。调用实例的方法来描述动画。最后通过动画实例的export方法导出动画数据传递给组件的animation属性。注意: export 方法每次调用后会清掉之前的动画操作

- 动画实例可以调用以下方法来描述动画，调用结束后会返回自身，支持链式调用的写法。