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
        }
    }
}

var {code:codeX,price:{price2}} = getStock();

```













