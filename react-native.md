# fetch请求

- 使用 Chrome 调试目前无法观测到 React Native 中的网络请求，你可以使用第三方的react-native-debugger来进行观测。

```
fetch('https://mywebsite.com/endpoint/', {
  method: 'POST',
  headers: {
    Accept: 'application/json',
    'Content-Type': 'application/json',
  },
  body: JSON.stringify({
    firstParam: 'yourValue',
    secondParam: 'yourOtherValue',
  }),
});
```



# 长列表

- FlatList组件必须的两个属性是data和renderItem。data是列表的数据源，而renderItem则从数据源中逐个解析数据，然后返回一个设定好格式的组件来渲染。

- 如果要渲染的是一组需要分组的数据，也许还带有分组标签的，那么SectionList将是个不错的选择



# 滚动视图

- ScrollView是一个通用的可滚动的容器，你可以在其中放入多个组件和视图，而且这些组件并不需要是同类型的。通过horizontal属性来设置垂直滚动，水平滚动

- 放置在ScrollView中的所有组件都会被渲染，显示较长的滚动列表，那么应该使用功能差不多但性能更好的FlatList组件。



# Touchable 系列组件

- TouchableHighlight来制作按钮或者链接。注意此组件的背景会在用户手指按下时变暗。

- 在 Android 上还可以使用TouchableNativeFeedback，它会在用户手指按下时形成类似墨水涟漪的视觉效果。

- TouchableOpacity会在用户手指按下时降低按钮的透明度，而不会改变背景的颜色。

- 如果你想在处理点击事件的同时不显示任何视觉反馈，则需要使用TouchableWithoutFeedback。

- 某些场景中你可能需要检测用户是否进行了长按操作。可以在上面列出的任意组件中使用onLongPress属性来实现。



setState 是一个 merge 合并操作，只修改指定属性，不影响其他属性

flex:1;

```
flex-grow: 1;
flex-shrink: 1;
flex-basis: 0%;
```

flexDirection的默认值是column而不是row，而flex也只能指定一个数字值。





