##CSS和模型

谈谈你对css盒模型的认识

- 基本概念：标准模型 + IE模型

- 标准模型和IE模型区别

- CSS如何设置这两种模型

- JS如何设置获取盒模型对应的宽和高

- 实例题（根据盒模型解释编剧重叠）

- BFC（边距重叠解决方案）



####标准模型和IE模型

![](/assets/360截图20171210100639194.jpg)

![](/assets/360截图20171210100623203.jpg)



####如何设置这两种模型

box-sizing: content-box;在宽度和高度之外绘制元素的内边距和边框。

box-sizing: border-box;为元素指定的任何内边距和边框都将在已设定的宽度和高度内进行绘制。



####JS如何设置获取盒模型对应的宽和高

- dom.style.witdh/height    只能取内联样式的宽和高

- dom.currentStyle.width/height    只支持IE（渲染后，即时运行的结果）

- window.getComputedStyle(dom).width/height    兼容firefox,chrome

- dom.getBoundingClientRect().width/height（left/top）    计算一个元素的绝对位置(viewport)


######css写法

- 内联样式

- html中header或任何部分加style节点

- 外联样式表


######实例题（根据盒模型解释边距重叠）

![](/assets/360截图20171210194301696.jpg)



####BFC（边距重叠解决方案）

BFC块级格式化上下文

IFC内联元素格式化上下文



######BFC原理

- BFC元素垂直方向的边距会发生重叠






















