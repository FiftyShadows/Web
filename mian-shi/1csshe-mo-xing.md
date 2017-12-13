##CSS盒模型

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

box-sizing: content-box;    (浏览器默认)在宽度和高度之外绘制元素的内边距和边框。

box-sizing: border-box;    为元素指定的任何内边距和边框都将在已设定的宽度和高度内进行绘制。



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

- BFC的区域不会与浮动元素的box重叠（可用来清除浮动和布局）

- BFC在页面上是一个独立的容器，外面的元素不会影响里面的元素，里面的元素也不会影响外面的元素

- 计算BFC高度时浮动元素也会参与计算


######如何创建BFC

- overflow（不为visible）

- float（值不为none）

- position(值不是static或relative)

- display(值为inline-block,table,table-cell,table-caption)


######BFC的使用场景

```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>CSS盒模型</title>
	<style media="screen">
		html *{
			margin: 0;
			padding: 0;
		}
	</style>
</head>
<body>
	<section id="sec">
		<style media="screen">
			#sec{
				background: #f00;
			}
			.child{
				height: 100px;
				margin-top: 10px;
				background: yellow;
			}
		</style>
		<article class="child"></article>
	</section>

	<!-- BFC垂直方向边距重叠 -->
	<!-- 给子元素增加父元素，父元素创建BFC -->
	<section class="margin">
		<style media="screen">
			.margin{
				background: pink;
				overflow: hidden;
			}
			.margin p{
				margin: 5px auto 25px;
				background: red;
			}
		</style>
		<p>1</p>
		<div style="overflow: hidden;">
			<p>2</p>
		</div>
		<p>3</p>
	</section>

	<!-- BFC的元素不会与浮动元素的box重叠 -->
	<section id="layout">
		<style media="screen">
			#layout{
				background: blue;
				border: 1px dashed blue;
			}
			#layout .left{
				float: left;
				width: 100px;
				height: 100px;
				background: pink;
			}
			#layout .right{
				height: 110px;
				background: #ccc;
				overflow: auto;
			}
		</style>
		<div class="left"></div>
		<div class="right"></div>
	</section>

	<!-- BFC子元素即时是float也会参与高度计算 -->
	<section id="float">
		<style media="screen">
			#float{
				background: red;
				overflow: auto;
				/*float: left;*/
			}
			#float .float{
				float: left;
				font-size: 30px;
			}
		</style>
		<div class="float">我是浮动元素</div>
	</section>
</body>
</html>
```















