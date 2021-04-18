# react-native

## 网络图片

* 很多要在 App 中显示的图片并不能在编译的时候获得，又或者有时候需要动态载入来减少打包后的二进制文件的大小。这些时候，与静态资源不同的是，你需要手动指定图片的尺寸

为了使新的图片资源机制正常工作，require 中的图片名字必须是一个静态字符串（不能使用变量！因为 require 是在编译时期执行，而非运行时期执行！）。

React Native 会检测某个文件是否具有.ios.或是.android.的扩展名，然后根据当前运行的平台自动加载正确对应的文件。如果你还希望在 web 端复用 React Native 的代码，那么还可以使用.native.js的扩展名。此时 iOS 和 Android 会使用BigButton.native.js文件，而 web 端会使用BigButton.js。

keyExtractor 此函数用于为给定的item生成一个不重复的key。Key的作用是使React能够区分同类元素的不同个体，以便在刷新时能够确定其变化的位置，减少重新渲染的开销。若不指定此函数，则默认抽取item.key作为key值。若item.key也不存在，则使用数组下标。

为什么建议把内容放到 FlatList 里？比起直接渲染出所有的元素，或是放到一个 ScrollView 里有什么优势？这是因为尽管 React 很高效，渲染一个可能很大的元素列表还是会很慢。FlatList会安排视图的渲染，只显示当前在屏幕上的那些元素。而那些已经渲染好了但移动到了屏幕之外的元素，则会从原生视图结构中移除（以提高性能）。

## fetch请求

* 使用 Chrome 调试目前无法观测到 React Native 中的网络请求，你可以使用第三方的react-native-debugger来进行观测。

```text
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

## 长列表

* FlatList组件必须的两个属性是data和renderItem。data是列表的数据源，而renderItem则从数据源中逐个解析数据，然后返回一个设定好格式的组件来渲染。
* 如果要渲染的是一组需要分组的数据，也许还带有分组标签的，那么SectionList将是个不错的选择

## 滚动视图

* ScrollView是一个通用的可滚动的容器，你可以在其中放入多个组件和视图，而且这些组件并不需要是同类型的。通过horizontal属性来设置垂直滚动，水平滚动
* 放置在ScrollView中的所有组件都会被渲染，显示较长的滚动列表，那么应该使用功能差不多但性能更好的FlatList组件。

## Touchable 系列组件

* TouchableHighlight来制作按钮或者链接。注意此组件的背景会在用户手指按下时变暗。
* 在 Android 上还可以使用TouchableNativeFeedback，它会在用户手指按下时形成类似墨水涟漪的视觉效果。
* TouchableOpacity会在用户手指按下时降低按钮的透明度，而不会改变背景的颜色。
* 如果你想在处理点击事件的同时不显示任何视觉反馈，则需要使用TouchableWithoutFeedback。
* 某些场景中你可能需要检测用户是否进行了长按操作。可以在上面列出的任意组件中使用onLongPress属性来实现。

setState 是一个 merge 合并操作，只修改指定属性，不影响其他属性

flex:1;

```text
flex-grow: 1;
flex-shrink: 1;
flex-basis: 0%;
```

flexDirection的默认值是column而不是row，而flex也只能指定一个数字值。

