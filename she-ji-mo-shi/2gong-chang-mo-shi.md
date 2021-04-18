# 2.工厂模式

## 介绍

* 将new操作单独封装
* 遇到new时，就要考虑是否该使用工厂模式

## UML类图

![](../.gitbook/assets/微信截图_20181006223048.png)

## 代码演示

```text
class Product{
    constructor(name){
        this.name = name
    }
    init(){
        alert('init')
    }
    fun1(){
        alert('fun1')
    }
    fun2(){
        alert('fun2')
    }
}

class Creator{
    create(name){
        return new Produce(name)
    }
}

let creator = new Creator()
let p = creator.create('p1')
p.init()
p.fun1()
```

![](../.gitbook/assets/微信截图_20181006223738.png)

![](../.gitbook/assets/微信截图_20181006223640.png)

![](../.gitbook/assets/微信截图_20181006223923.png)

## 设计原则

* 构造函数和创建者分离
* 符合开放封闭原则

