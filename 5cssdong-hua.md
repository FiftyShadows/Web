## 面试题

1. CSS动画的实现方式有几种

    - transition
    
    - keyframes(animation)
    
2. 过渡动画和关键帧动画的区别

    - 过渡动画需要有状态变化，主要是DOM元素hover等状态
    
    - 关键帧动画不需要状态变化
    
    - 关键帧动画能控制更精细
    
3. 如何实现逐帧动画

    - 使用关键帧动画
    
    - 去掉补间(用steps)
    
4. CSS动画的性能

    - 性能不坏(也就支持那么几个属性，底层的实现方式是已经浏览器已经写好的，当你写出一个性能不好的动画，基本上用JS做不会得到一个更好的结果)
    
    - 部分情况下优于JS(看具体怎么实现，有很多实现方式，市面上的动画库性能差距很大，取决于编写方式不同，性能也不一样)
    
    - 但JS可以做到性能更好(在一些可以做优化的场景下，CSS优化的空间不多，JS可以做更精细的控制，设定动画帧数少一些,在一些看不到的地方减少运算量)
    
    - 部分高危属性 box-shadow等(变换颜色，大小的时候，性能都是非常差的，cpu负载很高)
    
    - 没有场景的情况下很难说哪个更好
    


# JS动画

- setTimeout、setInterval、requestAnimationFrame(告诉浏览器——你希望执行一个动画，并且要求浏览器在下次重绘之前调用指定的回调函数更新动画。cancelAnimationFrame取消)

    - 异步的实际执行时间一般要比其设定的时间晚一些。
    
    - setTimeout的执行只是在内存中对图像属性进行改变，这个变化必须要等到屏幕下次刷新时才会被更新到屏幕上。如果两者的步调不一致，就可能会导致中间某一帧的操作被跨越过去，而直接更新下一帧的图像。

- requestAnimationFrame 接收一个函数，这个函数将在下一帧渲染之前执行，也就是说，不需要太多次的计算，只要在下一帧渲染之前，我们将需要修改的数值修改掉即可。requestAnimationFrame 的帧率和硬件以及浏览器有关，一般是60FPS(16.66666666ms/帧)。

    - requestAnimationFrame最大的优势是由系统来决定回调函数的执行时机，它能保证回调函数在屏幕每一次的刷新间隔中只被执行一次
    
    - CPU节能：使用setTimeout实现的动画，当页面被隐藏或最小化时，setTimeout 仍然在后台执行动画任务，由于此时页面处于不可见或不可用状态，刷新动画是没有意义的，完全是浪费CPU资源。而requestAnimationFrame则完全不同，当页面处理未激活的状态下，该页面的屏幕刷新任务也会被系统暂停，因此跟着系统步伐走的requestAnimationFrame也会停止渲染，当页面被激活时，动画就从上次停留的地方继续执行，有效节省了CPU开销。
    
    - 函数节流：在高频率事件(resize,scroll等)中，为了防止在一个刷新间隔内发生多次函数执行，使用requestAnimationFrame可保证每个刷新间隔内，函数只被执行一次，这样既能保证流畅性，也能更好的节省函数执行的开销。一个刷新间隔内函数执行多次时没有意义的，因为显示器每16.7ms刷新一次，多次绘制并不会在屏幕上体现出来。

```
const box = document.querySelector('.box') // 获取方块元素
let value = 0 // 设置初始值
// 创建每一帧渲染之前要执行的方法
const add = () => {
    requestAnimationFrame(add) //循环执行，下一帧渲染之前继续执行 add 方法
    value += 5 // 每帧加数值增加5
    box.style.transform = `translateX(${value}px)` // 将数值设置给 方块 的 css 属性 transform 属性可以控制元素在水平方向上的位移
}
requestAnimationFrame(add) // 下一帧渲染之前执行 add 方法


/*
    假设屏幕每隔16.7ms刷新一次，而setTimeout每隔10ms设置图像向左移动1px， 就会出现如下绘制过程：
    
    第0ms: 屏幕未刷新，等待中，setTimeout也未执行，等待中；
    
    第10ms: 屏幕未刷新，等待中，setTimeout开始执行并设置图像属性left=1px；
    
    第16.7ms: 屏幕开始刷新，屏幕上的图像向左移动了1px， setTimeout 未执行，继续等待中；
    
    第20ms: 屏幕未刷新，等待中，setTimeout开始执行并设置left=2px;
    
    第30ms: 屏幕未刷新，等待中，setTimeout开始执行并设置left=3px;
    
    第33.4ms:屏幕开始刷新，屏幕上的图像向左移动了3px， setTimeout未执行，继续等待中；
*/



1、requestAnimationFrame 会把每一帧中的所有DOM操作集中起来，在一次重绘或回流中就完成，并且重绘或回流的时间间隔紧紧跟随浏览器的刷新频率，一般来说，这个频率为每秒60帧。
2、在隐藏或不可见的元素中，requestAnimationFrame将不会进行重绘或回流，这当然就意味着更少的的cpu，gpu和内存使用量。


//兼容写法，IE9-无该方法
var requestAnimationFrame = window.requestAnimationFrame ||
			    window.webkitRequestAnimationFrame ||
			    window.mozRequestAnimationFrame ||
			    window.oRequestAnimationFrame ||
			    window.msRequestAnimationFrame ||
			    function(cb){window.setTimeout(cb,1000/60);};

```


## 动画的原理

- 视觉暂留作用

- 画面逐渐变化



## 动画的作用

- 愉悦感

- 引起注意

- 反馈

- 掩饰



## 动画类型

- transition补间动画

- keyframe关键帧动画

- 逐帧动画



## 补间动画

- 位置-平移    left/right/margin/transform

- 方位-旋转    transform

- 大小-缩放    transform

- 透明度        opacity

- 其他-线性变换    transform

    - translate
    
    - rotate
    
    - scale
    
    - skew

- 颜色    background兼容问题



## transition

- transition-delat

- transition-duration

- transition-property

- `transition-timing-function: cubic-bezier(0.205, -0.390, 0.860, 1.480);`



## 关键帧动画

- 相当于多个补间动画

- 与元素状态的变化无关(hover)

- 定义更加灵活



## animation

- animation-name

- animation-duration

- animation-timing-function

- animation-delay

- animation-iteration-count

- animation-direction

- animation-play-state: paused;  可用于JS控制动画暂停

- animation-fill-mode: backwards;  forwards保持最后的状态，backwards保持开始的状态



## 逐帧动画

- 适用于无法补间计算的动画

- 资源较大

- 使用steps()  steps指定关键帧之间有几个画面

- 原理：仍然是使用关键帧动画去实现的，核心是去掉关键帧之间补间，具体方式就是使用steps(animation-timing-functaion)属性值。适用于动画面积比较小，时常不大。动画太长，画面太大不适合，会导致资源增大，性能也不会很好。