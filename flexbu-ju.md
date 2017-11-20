flex:1;

flex: flex-grow flex-shrink flex-basis\|auto\|initial\|inherit;

flex-grow    一个数字，项目将相对于其他灵活的项目进行扩展的量。

flex-shrink    一个数字，规定项目将相对于其他灵活的项目进行收缩的量。

flex-basis    项目的长度。合法值："auto"、"inherit" 或一个后跟 "%"、"px"、"em" 或任何其他长度单位的数字。





## flex

* 在父节点上设置

display: flex;    伸缩盒子

flex-direction: row;    flex容器主轴方向\(row \| row-reverse \| column \| column-reverse\)

flex-wrap: wrap;    控制flex容器是单行或者多行，同时横轴的方向决定了新行堆叠的方向\(nowrap \| wrap \| wrap-reverse\)

flex-flow属性是flex-direction属性和flex-wrap属性的简写形式，默认值为row nowrap。

justify-content: center;    主轴横向对齐方式

align-content: stretch;    主轴竖向对齐方式，默认stretch

align-items: center;    定义flex子项在flex容器的当前行纵轴对齐方式\(flex-start \| flex-end \| center \| baseline \| stretch\)

![](/assets/360截图20171120204939943.jpg)

![](/assets/360截图20171117132227121.jpg)

## 

## 

## 项目的属性

* order属性定义项目的排列顺序。数值越小，排列越靠前，默认为0。

* flex-grow属性定义项目的放大比例，默认为0，即如果存在剩余空间，也不放大

如果所有项目的flex-grow属性都为1，则它们将等分剩余空间（如果有的话）。如果一个项目的flex-grow属性为2，其他项目都为1，则前者占据的剩余空间将比其他项多一倍。

* flex-shrink属性定义了项目的缩小比例，默认为1，即如果空间不足，该项目将缩小。

如果所有项目的flex-shrink属性都为1，当空间不足时，都将等比例缩小。如果一个项目的flex-shrink属性为0，其他项目都为1，则空间不足时，前者不缩小

* flex-basis属性定义了在分配多余空间之前，项目占据的主轴空间（main size）。浏览器根据这个属性，计算主轴是否有多余空间。它的默认值为auto，即项目的本来大小。

* flex属性是flex-grow, flex-shrink 和 flex-basis的简写，默认值为0 1 auto。后两个属性可选。

该属性有两个快捷值：auto \(1 1 auto\) 和 none \(0 0 auto\)。

* align-self属性允许单个项目有与其他项目不一样的对齐方式，可覆盖align-items属性。默认值为auto，表示继承父元素的align-items属性，如果没有父元素，则等同于stretch。



