- 微软开发

- javascript超集

- 遵循ES6



##优势

- 支持ES6规范

- 强大的IDE支持（语法提示，重构）

- Angular的开发语言




##搭建typescipt开发环境

- 使用在线complier开发

- 本地complier

    - npm install -g typescipt
    
    - tsc --version

    - tsc hello.ts




##字符串新特性

###多行字符串

```
var content = `aaa
bbb
ccc`;
```

###字符串模板

```
var name = `zhai liang`;
var getName = function (){
    return "zhai liang";
}
console.log(`hello ${name}`);
console.log(`hello ${getName()}`);
console.log(`<div>
<span>${name}</span>
<span>${getName()}</span>
<div>xxx</div>
</div>`);
```

###自动拆分字符串

```
function (template,name,age){
    console.log(template);
    console.log(name);
    console.log(age);

}
var myname= "zhai liang";
var getAge = function (){
    return 18;
}
test`my name is ${name},i'm ${getAge()}`;
```





##参数新特性


###参数类型

在参数名称后面使用冒号来制定参数类型。

```
var myname:string = "zhai liang";
name = 13;    //报错
var alias = "xx";
alias = 13;    //报错

var a:any = "xx";
a = 13;

var age:number = 13;

var man:boolean = true;

//返回值void
function test(name:string):void{
    return   //报错,string则不会
}
test(13);    //报错


class Person{
    name:string;
    age:number;
}
var zhangsan:Person = new Person();
zhangsan.name = "zhang liang";.
zhangsan.age = 18;
```


###参数默认值

带默认值的参数一定要放在最后面。

```
function test(a:string, b:string, c:string = "jojo"){
    console.log(a);
    console.log(b);
    console.log(c);
}
test("xx", "yy", "zz");
test("xx", "yy");
```


###可选参数

可选参数要放在必选参数的后面。

```
function test(a:string, b?:string, c:string = "jojo"){
    console.log(a);
    console.log(b);
    console.log(c);
}
test("xx");    //xx undefined jojo
```



##函数新特性


###Rest and Spread 操作符：

    用来声明任意数量的方法参数

```
function fun1(...args){
    args.forEach(function (arg){
        console.log(arg);
    });
}

func1(1,2,3);
func1(6,7,8,9,11);
```

```
function func1(a,b,c){
    console.log(a);
    console.log(b);
    console.log(c);
}

var args = [1,2];
func1(...args);    //1 2 undefined

var args2 = [7,8,9,10,11];
func1(...args2);    // 7 8 9
```


###generator函数：

    控制函数的执行过程，手动暂停和恢复代码执行


```js
function* doSomething(){
    console.log("start");
    yield;
    console.log("finish");
}
var func1 = doSomething();
func1.next();
func1.next();
```


```js
function* getPrice(stock){
  while(true){
    yield Math.random()*100;
  }
}
var num = getPrice("IBM");
var price = 100;
var limitPrice = 15;

while(price > limitPrice){
  console.log(price);
  price = num.next().value;
  }
console.log(`buying at ${price}`);
```



###析构表达式

```
function getStock(){
    return{
        code:"IBM",
        price:100
    }
}
//ES5
var stock = getStock();
var code = stock.code;
var price = stock.price;

//ES6,参数必须对应
var {code,price} = getStock();

var {code:codeX,price} = getStock();
console.log(codeX);
console.log(price);
```


```
function getStock(){
    return{
        code:"IBM",
        price:{
            price1:200,
            price2:400
        },
        aaa:"xx",
        bbb:"yy"
    }
}
var {code:codeX,price:{price2}} = getStock();
console.log(price);
```


```
var arr = [1,2,3,4];

var [,,num1, num2] = arr;
```


```
var arr = [1,2,3,4];
var [num1, num2, ...others] = arr;
console.log(others);
```

```
var arr = [1,2,3,4];
function do(num1,num2,...others){
    console.log(num1);
    console.log(num2);
    console.log(others);
}
```




##表达式和循环


###箭头表达式

    用来声明匿名函数，消除传统匿名函数的this指针问题

```
//单行
var sum = (arg1,arg2) => arg1 + arg2;
```


```
//无参数
var sum = () => {

}
```

```
//一个参数
var sum = arg1 => {

}
```

```
var arr = [1,2,3,4,5,6,7,8,9];
console.log(arr.filter(val => val%2 == 0));
```



```
//消除传统匿名函数的this指针问题
function getStock(name:string){
    this.name = name;
    setInterval(function (){
        console.log("name is" + this.name);
    },1000);
}
var stock = new getStock("IBM");

function getStock2(name:string){
    this.name = name;
    setInterval(() => {
        console.log("name is" + this.name);
    },1000);
}
var stock2 = new getStock2("IBM");
```

functino(){}的写法，由于是匿名函数，上下文是调用时的上下文，即window，因为window.name未定义，所以访问不到。箭头函数的上下文是由创建时所在的上下文决定的，在getStock()函数中创建，所以this之中指向getStock()，故可以访问到name属性。



###forEach(),for in 和 for of


```
var arr = [1,2,3,4];
arr.desc = "four number";
arr.forEach(val => console.log(val));
//会忽略属性值,不能break
```


```
var arr = [1,2,3,4];
arr.desc = "four number";
for(var n in arr){
    console.log(arr[n]);
}
```


```
var arr = [1,2,3,4];
arr.desc = "four number";
for(var n of arr){
    console.log(n);
    if(n > 2)break;
}
//会忽略属性值,能break,还可用于字符串
```





##面向对象特性

###类，类是typescrip的核心，使用typescript开发时，大部分代码都是写在类里面的。


```
class Person{
    name;
    eat(){
        console.log("i'm eating");
    }
}
var p1 = new Person();
p1.name = "batman";
p1.eat();

var p2 = new Person();
p2.name = "superman";
p2.eat();
```

访问控制符public,private（内部）,protected(内部和子类)



####类的构造方法

```
class Person{
    //声明了name属性
    constructor(public name:string){
        console.log("imooc");
    }
    eat(){
        console.log(this.name);
    }
}
var p1 = new Person("batman");
p1.eat();


```



####类的继承extends, super

```
class Person{
    //声明了name属性
    constructor(public name:string){
        console.log("imooc");
    }
    eat(){
        console.log(this.name);
    }
}
class Employee extends Person{
    code:string;
    work(){
    
    }
}
var e1 = new Employee("name");
```




```
class Person{
 constructor(public name:string){
        console.log("imooc");
    }
    eat(){
        console.log("i'm eating.");
    }
}
class Employee extends Person{
    constructor(name: string, code: string){
        super(name);
        console.log("xx");
        this.code = code;
    }
    code:string;
    work(){
        super.eat();
        this.doWork();
    }
    private doWork(){
        console.log("i'm working.");
    }
}
var e1 = new Employee("name","1");
e1.work();
```



###泛型（generic）
    
    参数化的类型，一般用来限制集合的内容

```
class Person{
 constructor(public name:string){
        console.log("imooc");
    }
    eat(){
        console.log("i'm eating.");
    }
}
class Employee extends Person{
    constructor(name: string, code: string){
        super(name);
        console.log("xx");
        this.code = code;
    }
    code:string;
    work(){
        super.eat();
        this.doWork();
    }
    private doWork(){
        console.log("i'm working.");
    }
}
var workers: Array<Person> = [];
workers[0] = new Person("zhangsan");
workers[1] = new Employee("lisi","2");
```



###接口(Interface)

    用来建立某种代码约定，使得其他开发者在调用某个方法或创建新的类时必须遵循接口所定义的代码约定。
    
    
    
    
    
    
    
    
    
