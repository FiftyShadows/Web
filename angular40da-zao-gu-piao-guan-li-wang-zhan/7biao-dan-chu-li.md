## 内容

* 模板式表单

* 响应式表单

* 表单验证

## Angular表单API

![](/assets/360截图20171024234630050.jpg)

![](/assets/360截图20171024234702839.jpg)

![](/assets/360截图20171024234903667.jpg)

![](/assets/360截图20171024235049273.jpg)






## 模板式表单

![](/assets/360截图20171025002101919.jpg)

指令NgForm、NgModel、NgModelGroup

Angular会自动为form表单添加ngForm指令，阻止表单自动提交导致的刷新，可以给其他标签手动添加ngForm指令，ngNoForm阻止Angular接管。

####ngForm被模板本地变量引用，以便在模板中访问ngForm的实例。

![](/assets/360截图20171025001434065.jpg)

![](/assets/360截图20171025002253141.jpg)

####ngModel指令创建的对象也可以通过本地模板变量来引用

![](/assets/360截图20171125155542956.jpg)

####ngModelGroup嵌套ngModel指令

![](/assets/360截图20171125160028710.jpg)






## 响应式表单

![](/assets/360截图20171025085528204.jpg)

![](/assets/360截图20171025003216388.jpg)

指令全都来自于ReactiveFormsModule

#### 不可引用

不能通过模板本地变量引用这个指令的实例，为了明确区分两种表单的处理方式。

注意:

* 所有的指令都是以form开头的

* 如果指令以name结尾不需要属性绑定语法的方括号，不以name结尾需要方括号

* 以name结尾的指令只能用在formGroup指令覆盖的范围之内。

![](/assets/360截图20171025125449895.jpg)

![](/assets/360截图20171025125528991.jpg)

#### FormBuilder

![](/assets/360截图20171025130038237.jpg)







## 表单校验

#### 校验器

* 预定义的校验器Validators\(required,minLength,maxLength,pattern\)

![](/assets/360截图20171025131200552.jpg)

* 自定义的校验器







## 状态字段

![](/assets/360截图20171025142529067.jpg)

- touch和untouch字段是否获取过焦点。

- pristine和dirty字段的值是否变过。

- 对于整个表单，任何一个字段touched（dirty），整个表单touched(dirty);所有字段untouched(pristine)，整个表单untouched(pristine)。

- pending当一个字段正处于异步校验时，字段的pending属性为true，显示一段文字或图片让用户知道在校验。

![](/assets/360截图20171025143402423.jpg)


####针对所有字段Angular会自动根据其状态，给input标签添加一些样式，可以通过自定义这些样式个性化input在不同状态下的外观

![](/assets/360截图20171031160921809.jpg)

给input标签添加hasError样式

`<div>用户名：<input [class.hasError]="formModel.get('username').invalid && formModel.get('username').touched" type="text" formControlName="username"></div>`









## 模板式表单校验

directive（没有模板的组件）和component类似，区别就是directive没有模板。


 


