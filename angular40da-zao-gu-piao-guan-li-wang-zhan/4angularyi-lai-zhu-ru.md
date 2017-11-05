## 依赖注入Dependency Injection

控制反转Inversion Of Control

IOC容器

控制反转将依赖的控制权由代码的内部转到了代码的外部。依赖注入和控制反转其实是一体两面：只不过控制反转强调的是目的，目的就是将依赖的控制权从代码的内部转到代码的外部。而依赖注入强调的是手段，如何实现控制反转，就是依赖注入。angular2实现控制反转的机制就是依赖注入。

#### 依赖注入模式的好处

* 松耦合，可重用性

* 可测试性

#### 依赖注入原理

* 注入器

  `constructor(private productService: ProductService){}`

* 提供器

  `providers: [ProductService]`

  `providers: [provide: ProductService, useClass: ProductService]`

provide指定了提供器的token，useClass代表实例化方法是new ProductService\(\)

    `providers: [provide: ProductService, useClass: AnotherProductService]`

实例化AnotherProductService，useClass决定了实例化的类

    `providers: [provide: ProductService, useFactory: () => {...}]`

通过工厂方法返回一个实例，注入到构造函数里，并且对实例做一些初始化

#### 实战

![](/assets/360截图20171020095737298.jpg)

![](/assets/360截图20171020095822879.jpg)

外标签不能用p

product1和product.service，并在app.module设置提供器

![](/assets/360截图20171020100126983.jpg)

![](/assets/360截图20171020100200800.jpg)

![](/assets/360截图20171020100239991.jpg)

product2使用pruduct.service的Product类,但注入another.service的AnotherProductService

![](/assets/360截图20171020112039493.jpg)

#### 提供器的作用域规则

1. 当一个提供器声明在模块中时，它对所有组件可见，所有组件都可以注入

2. 当一个提供器声明在组件中时，对声明它的组件及子组件可见，其他组件不可以注入它

3. 当声明在模块中的提供器和声明在组件中的提供器有相同的token时，声明在组件中的提供器会覆盖声明在模块中的提供器

4. 一般情况下优先将服务提供器声明在模块中，只有服务必须得某个组件之外的其他组件不可见时，才将其声明在组件中（罕见）

#### @Injectable\(\)装饰器的作用

![](/assets/360截图20171020113735976.jpg)

@Injectable\(\)的作用：表示这个ProductService也可以通过构造函数**注入其他服务**。并不表示这个服务可以注入到其他地方，app.module的providers决定了能不能在其他地方注入

###### 需要注意的

1. 把所有的服务都加上@Injectable装饰器，方便以后添加依赖，服务一致性，Angular命令行工具已经这样做了

2. 组件的@Component装饰器和管道装饰器都是@Injectable的子类，所以能在构造函数里注入其他的类。

#### 使用工厂和值声明提供器

根据某些条件具体实例化那个对象；实例化对象，调用对象的构造函数时需要传递参数，需要用到工厂提供器。

工厂方法创建的对象是一个单例对象，在创建第一个需要被注入的对象时被调用一次，在整个应用中所有被注入的这个对象都是一个对象。

![](/assets/360截图20171020133111905.jpg)

###### 工厂声明提供器的两个问题

* 在useFactory里注入其他的类——解耦合

![](/assets/360截图20171020134154731.jpg)

* 用具体的值定义一个提供器

![](/assets/360截图20171020141114845.jpg)

### \

![](/assets/360截图20171020163252080.jpg)

