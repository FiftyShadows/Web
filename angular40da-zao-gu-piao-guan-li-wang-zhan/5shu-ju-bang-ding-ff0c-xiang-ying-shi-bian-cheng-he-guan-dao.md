#内容

- 数据绑定

- 响应式编程

- 管道




##数据绑定


####单向绑定

- 使用插值表达式将一个表达式的值显示在模板上

- 使用方括号将HTML标签的一个属性绑定到一个表达式上

- 使用小括号将组件控制器的一个方法绑定为模板上一个事件的处理器



####双向绑定变为可选项，而不再是默认行为



##事件绑定

**事件绑定右侧的表达式可以不是一个函数调用，也可以是一个属性赋值，被绑定的事件既可以是DOM事件，也可以是自定义事件。**

![](/assets/360截图20171022153622894.jpg)


##DOM属性绑定

- 插值表达式和属性绑定一样

![](/assets/360截图20171023092903496.jpg)

渲染之前会把插值表达式编译成属性绑定。


- HTML属性和DOM属性区别

![](/assets/360截图20171023113859568.jpg)

![](/assets/360截图20171023113552840.jpg)

HTML属性指定了初始值，HTML属性初始化DOM属性

DOM属性指定了当前值

DOM属性的值可以改变，HTML属性不能改变

disabled属性的HTML值无关紧要，可以设置DOM的disabled属性



####HTML属性和DOM属性的关系

- 少量HTML属性和DOM属性之间有着1:1的映射，如id。

- 有些HTML属性没有对应的DOM属性，如cosplay。

- 有些DOM属性没有对应的HTML属性，如textHTML。

- 就算名字相同，HTML属性和DOM属性也不是一样东西。

- HTML属性的值指定了初始值；DOM属性的值表示当前值。
DOM属性的值可以改变；HTML属性的值不能改变。

- 模板绑定是通过DOM属性和事件来工作的，而不是HTML属性。

![](/assets/360截图20171023130322503.jpg)





##HTML属性绑定

- 基本HTML属性绑定

`<td [attr.colspan]="tableColspan">Something</td>`

- CSS类绑定

    1. 全有或全无`<div class="aaa" [class]="someExpression">something</div>`替换原来class的值

    2. 样式名和布尔值`<div class="a b" [class.c]="bool">something</div>`

    3. 控制多个CSS类是否显示`<div ngClass="{aaa:isA,bbb:isB}"></div>`

![](/assets/360截图20171023133852147.jpg)

![](/assets/360截图20171023133957236.jpg)

- 样式绑定

`<button [style.color]="isDev?'red':'green'">Red</button>`

![](/assets/360截图20171023134313521.jpg)

`<div [ngStyle]="{'font-style':this.canSAve?'itlaic':'normal'}"></div>`

![](/assets/360截图20171023134606556.jpg)

![](/assets/360截图20171023134752280.jpg)



![](/assets/360截图20171023132451898.jpg)





##双向绑定


























































































