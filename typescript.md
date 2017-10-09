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

在参数名称后面使用冒号来制定参数类型

```
var myname:string = "zhai liang";
//赋值检查
name = 13;
var alias = "xx";
//报错
alias = 13;

var a:any = "xx";
a = 13;


```



















