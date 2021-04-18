# 5.总结

## 表单组件

* `<switch name="switch" type="switch" color="yellow" checked="true" bindchange="switch1Change"/>`
* `<slider min="0" max="500" step="50" valie="250" color="yellow" name="slider" show-value="true"></slider>`

```text
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

* checkbox
* 小程序只能用form标签获取表单值

```text
<form class="xx" catchsubmit="" catchreset="">

  <view class="">
    <button formType="submit">Submit</button>
    <button formType="reset">Reset</button>
  </view>
</form>
```

* 地图；调内置地图
* openlayers 1.x 极致的面向对象

## MINA在Page里还提供了一个onReachBottom事件，使用这个事件来监听页面上滑到底。

## 运用es6的module，class，Promise,lambda

## 动画

* 创建一个动画实例animation。调用实例的方法来描述动画。最后通过动画实例的export方法导出动画数据传递给组件的animation属性。注意: export 方法每次调用后会清掉之前的动画操作
* 动画实例可以调用以下方法来描述动画，调用结束后会返回自身，支持链式调用的写法。
* 调用动画操作方法后要调用 step\(\) 来表示一组动画完成，可以在一组动画中调用任意多个动画方法，一组动画中的所有动画会同时开始，一组动画完成后才会进行下一组动画。step 可以传入一个跟 wx.createAnimation\(\) 一样的配置参数用于指定当前组动画的配置。
* 通过 step\(\) 分隔动画，只有第一步动画能生效

## 用户信息

* wx.getUserInfo\(OBJECT\)；获取用户信息，withCredentials 为 true 时需要先调用 wx.login 接口。需要用户授权 scope.userInfo
* 当 withCredentials 为 true 时，要求此前有调用过 wx.login 且登录态尚未过期，此时返回的数据会包含 encryptedData, iv 等敏感信息；当 withCredentials 为 false 时，不要求有登录态，返回的数据不包含 encryptedData, iv 等敏感信息。

## 通过给 button 组件设置属性 open-type="share"，可以在用户点击按钮后触发 Page.onShareAppMessage\(\) 事件，如果当前页面没有定义此事件，则点击后无效果。相关组件：button

## wx:key 的值以两种形式提供

* 字符串，代表在 for 循环的 array 中 item 的某个 property，该 property 的值需要是列表中唯一的字符串或数字，且不能动态改变。
* 保留关键字 \*this 代表在 for 循环中的 item 本身，这种表示需要 item 本身是一个唯一的字符串或者数字

## e.currentTarget指的是注册了事件监听器的对象，而e.target指的是该对象里的子对象，也是触发这个事件的对象！

