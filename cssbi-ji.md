## position

- static 默认值，没有定位

- relative 生成相对定位的元素，相对于其正常位置进行定位,其值的定位起点都是是父元素左上角(这点和absoute、fixed不一样)

- absoute 生成绝对定位的元素，相对于 static 定位以外的第一个父元素进行定位。top、left的定位起点是包含块左上角，right、bottom的定位起点是包含块右下角

- fixed 生成绝对定位的元素，相对于浏览器窗口进行定位，和absoute的区别是fixed不会跟随屏幕滚动。top、left的定位起点是包含块左上角，right、bottom的定位起点是包含块右下角


## 不要把fixed元素放在有transform属性的元素内

- fixed相对的不是visual viewport，而是transformELe, 产生这样的原因主要是因为transform和position: fixed使用了不同的坐标系统



## 对元素的margin，padding设置百分数，百分数是相对于父元素的width计算



## animation 属性 timing-function 中的 steps()函数。

- Animation 在执行动画时默认以 ease函数进行过渡，ease 会在每个关键帧之间插入补间动画，所以动画效果是连贯的。

- steps()是 Animation 中的一个 timing-function函数， 能够实现动画的阶跃式变化，而非两个状态间的线性过渡。




## 文本省略

- 单行文本，overflow: hidden;white-space: nowrap;text-overflow: ellipsis;需要设置盒子宽度；所以flex下需设置min-width/max-width

- 多行文本，1.使用伪元素content:'...'；2.display:-webkit-box;-webkit-line-clamp:2;-webkit-box-orient: vertical;




## outline

- outline（轮廓）是绘制于元素周围的一条线，位于边框边缘的外围，可起到突出元素的作用。

- 可以设置的属性分别是（按顺序）：outline-color, outline-style, outline-width

- 如果不设置其中的某个值，也不会出问题

- 可以通过outline-offset属性来控制与边缘的间距，可以接受负值。        缝边效果




## HSLA(Hue, saturation, Lightness, Alhpa)

- 此色彩模式与HSL相同，只是在HSL模式上新增了Alpha透明度

- H：Hue(色调)。0(或360)表示红色，120表示绿色，240表示蓝色，也可取其他数值来指定颜色。取值为：0 - 360

- S：Saturation(饱和度)。取值为：0% - 100%

- L：Lightness(亮度)。取值为：0% - 100%

- A：Alpha透明度。取值0~1之间




##脱离文档流的元素其margin属性是参照哪个元素的？

1. 相对于和当前元素在同个父级元素下的其他脱离文档流的元素

2. 设置float后，margin只会相对于同级元素下其他有浮动熟悉的元素

3. top是绝对定位时候使用的属性，用来设置当前绝对定位元素距离父级容器顶部的距离;left同样是绝对定位时使用的属性,用来设置当前绝对定位元素距离父级容器左边的距离。




##box-shadow

- box-shadow: x轴偏移 y轴偏移 阴影模糊区域 阴影扩展区域 颜色 <inset>;

- box-shadow: 0 0 0 5px green;    作为边框

- 增大xy轴偏移，复制一个元素出来

- 用投影做非常多的效果，一个div实现……效果

- 一个元素画叮当猫系列，大量使用点画线

####作用

- 营造层次感（立体感）

- 充当没有宽度的边框

- 特殊效果

![](/assets/360截图1738040774124101.png)





##text-shadow

- 立体感

- 印刷品质感        text-shadow: 0 0 1px rgba(128,128,128,.2);

- 黑色背景下，给四周加阴影        第三个属性只能是模糊效果




##border-radius

- 圆角矩形

- 圆形        超过50%不会有影响，仍然是圆形；使用百分比和使用像素相比，百分比不用考虑边框对盒子的影响。

- 半圆/扇形

- 一些奇怪的角角 
        
        - 可单独设置水平方向和垂直方向的圆角 border-radius:10px 10px 10px 10px /20px 20px 20px 20px;
        
        - border-top-left-radius: 10px 20px;
        
- 大值特性

- 等比特性

- 垂直在前
        
        
        

##background

- 纹理、图案

- 渐变

- 雪碧图动画

- 背景图尺寸适应



####background属性

- background-size 大小

        - background-size: 100% 100%;        全覆盖，会拉伸
        
        - cover覆盖整个画面，保持长宽比不变，不会有空白
        
        - contain长宽比不变，让图片完整显示，会有空白
        
- background-position 位置

        - background-position: center center; top left
        
- background-repeat
        
        - repeat-x
        
        - no-repeat

        
        


##clip-path 按路径裁剪

- 对容器进行裁剪

- 常见几何图形

- 自定义路径


####clip-path写法

- clip-path: inset(100px 50px);

- clip-path: circle(50px at 100px 100px);

        - 区别于border-radius；仍然占据相应位置。
        
        - 支持动画，适合做容器内的动画
        
- clip-path: polygon(50% 0%, 100% 50%, 50% 100%, 0% 50%);

- 用svg裁剪各种图形效果





##3D变换

      




##移除input在type="number"时的上下箭头

1. chrome浏览器移除
```
input::-webkit-outer-spin-button,input::-webkit-inner-spin-button{
        -webkit-appearance:textfield;
}
```

2. firefox浏览器下移除
```
input[type="number"]{
        -moz-appearance:textfield;
}
```

3. 用type="tel"代替

input[type="tel"]的value值亦是number，且其没有type="number"时的上下箭头，故我们可以用[type="tel"]代替[type="number"]，达到一样的效果，并通过设置maxlength = "m"限定value值得长度。如果有其他的要求，可以通过正则来判断



##关于浮动元素宽度的问题

- 不设置宽度会使浮动元素进行shrink-to-fit趋于最小收缩宽度计算；按照规范它会计算最宽子元素来确定容器本身宽度。还是写上宽度为好，否则会带来额外布局计算消耗




##white-space:nowrap不换行



##letter-spacing文字间距



##text-indent:2em;规定文本块中首行文本的缩进



##word-break:break-all换行时拆分单词；break-word不拆分单词，并在下一行显示



##文字省略

![](/assets/360截图20180404225732078.jpg)









