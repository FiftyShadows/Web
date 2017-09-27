##作用域和闭包

###说一下对变量提升的理解

####执行上下文

- 范围：一段`<script>`或者一个函数

- 全局：变量定义、函数声明

- 函数：变量定义、函数声明、this、arguments

**PS：注意“函数声明”和“函数表达式”的区别**

![](/assets/360截图20170926174333254.jpg)




###说明this几种不同的使用场景

- this要在执行时才能确认值，定义时无法确认

![](/assets/360截图20170926174124005.jpg)

四个应用场景

    - 作为构造函数执行
    ```
        function Foo(name){
            this.name = name;
        }
        var f = new Foo();
    ```
    
    - 作为对象属性执行
    ```
    var obj = {
        name:'A',
        printName:function(){
            console.log(this.name);
        }
    }
    obj.printName();
    ```
    
    - 作为普通函数执行
    ```
    function fn(){
        console.log(this);    //this===window
    }
    fn();
    ```
    
    - call apply bind
    ```
    function fn1(name,age){
        alert(name);
        console.log(this);
    }
    fn1.call({x:100},'zhangsan',20);
    
    fn1.apply({x:100},['zhangsan',20]);
    
    var fn2 = function (name,age){
        alert(name);
        console.log(this);
    }.bind({y:200});    //只能用函数表达式，不能用函数声明方式    
    fn2();
    ```

    
    


###创建10个`<a>`标签，点击的时候弹出来对应的序号

###如何理解作用域

- JS没有块级作用域（只有全局和函数作用域）

```
// 无块级作用域
if (true) {
    var name = 'zhangsan';
}
console.log(name);

//函数和全局作用域
var a = 100;
function fn(){
    var a = 200;
    console.log('fn',a);
}
console.log('global',a);
fn();
```

####作用域链

```
var a = 100;
function fn(){
    var b = 200;
    //当前作用域没有定义的变量，即“自由变量”
    console.log(a);
    console.log(b);
}
fn();
```



###实际开发中闭包的作用
























































































