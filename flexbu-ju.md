flex:1;

flex: flex-grow flex-shrink flex-basis|auto|initial|inherit;

flex-grow	一个数字，项目将相对于其他灵活的项目进行扩展的量。

flex-shrink	一个数字，规定项目将相对于其他灵活的项目进行收缩的量。

flex-basis	项目的长度。合法值："auto"、"inherit" 或一个后跟 "%"、"px"、"em" 或任何其他长度单位的数字。

## flex

* 在父节点上设置

display: flex;    伸缩盒子

flex-direction: row;    flex容器主轴方向

flex-wrap: wrap;    控制flex容器是单行或者多行，同时横轴的方向决定了新行堆叠的方向
        nowrap	默认值。规定灵活的项目不拆行或不拆列。
        wrap-reverse	规定灵活的项目在必要的时候拆行或拆列，但是以相反的顺序。
        inherit	从父元素继承该属性。
        

justify-content: center;    主轴横向对齐方式

align-content: stretch;    主轴竖向对齐方式，默认stretch

align-items: center;    定义flex子项在flex容器的当前行纵轴对齐方式

![](/assets/360截图20171117132227121.jpg)




















