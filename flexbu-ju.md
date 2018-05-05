##flex弹性布局

- flex-direction：决定了弹性盒子的主轴是row方向还是column方向

- flex-wrap：如果主轴排不下，如何换行。默认不换行。 flex-wrap: nowrap | wrap | wrap-reverse;

- flex-flow: flex-direction属性和flex-wrap属性的简写形式。默认值为row nowrap。

- justify-content: 定义了项目在主轴上的对齐方式。


























http://www.jianshu.com/p/07e0c16a4ff5#

flex:1;

flex: flex-grow flex-shrink flex-basis\|auto\|initial\|inherit;

flex-grow    一个数字，项目将相对于其他灵活的项目进行扩展的量。

flex-shrink    一个数字，规定项目将相对于其他灵活的项目进行收缩的量。

flex-basis    项目的长度。合法值："auto"、"inherit" 或一个后跟 "%"、"px"、"em" 或任何其他长度单位的数字。

## flex

* 在父节点上设置

- display: flex;    伸缩盒子

- flex-direction: row;    flex容器主轴方向\(row \| row-reverse \| column \| column-reverse\)

- flex-wrap: wrap;    控制flex容器是单行或者多行，同时横轴的方向决定了新行堆叠的方向\(nowrap \| wrap \| wrap-reverse\)

- flex-flow属性是flex-direction属性和flex-wrap属性的简写形式，默认值为row nowrap。

- justify-content: center;    主轴横向对齐方式

- align-content: stretch;    主轴竖向对齐方式，默认stretch

- align-items 属性，用于设置弹性元素在 flex 容器的 cross 轴方向上的对齐方式(flex-start \| flex-end \| center \| baseline \| stretch\)

![](/assets/360截图20171120204939943.jpg)

![](/assets/360截图20171117132227121.jpg)

- display:flex; 设置在外层容器父级，表示该容器使用弹性盒布局方式

- flex:1; 设置在子项，数值表示占据剩余空间的份数

## 

## 

## 项目的属性

* order 属性规定了弹性容器中的可伸缩项目在布局时的顺序，元素按照 order 属性的数值的增序进行布局，数值小的排在前面，可以为负值，默认值为 0，拥有相同 order 属性值的元素按照它们在源代码中出现的顺序进行布局

* flex-grow 属性的默认值为 0，如果没有显示定义该属性，是不会拥有分配剩余空间权利的

如果所有项目的flex-grow属性都为1，则它们将等分剩余空间（如果有的话）。如果一个项目的flex-grow属性为2，其他项目都为1，则前者占据的剩余空间将比其他项多一倍。

* flex-shrink 属性的默认值为 1，如果没有显示定义该属性，将会自动按照默认值 1 在所有子项宽度相加之后计算比率来进行空间收缩

如果所有项目的flex-shrink属性都为1，当空间不足时，都将等比例缩小。如果一个项目的flex-shrink属性为0，其他项目都为1，则空间不足时，前者不缩小

* flex-basis 属性的初始值为 auto，设置或检索弹性盒伸缩基准值，如果所有子元素的基准值之和大于剩余空间，则会根据每项设置的基准值，按比率伸缩剩余空间。
浏览器根据这个属性，计算主轴是否有多余空间。它的默认值为auto，即项目的本来大小。

* flex属性是flex-grow, flex-shrink 和 flex-basis的简写，默认值为0 1 auto。后两个属性可选。

该属性有两个快捷值：auto \(1 1 auto\) 和 none \(0 0 auto\)。

* align-self属性允许单个项目有与其他项目不一样的对齐方式，可覆盖align-items属性。默认值为auto，表示继承父元素的align-items属性，如果没有父元素，则等同于stretch。



