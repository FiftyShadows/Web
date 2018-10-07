## 介绍

- 为对象添加新功能

- 不改变其原有的结构和功能


![](/assets/微信截图_20181007153546.png)


```js
class Circle{
    draw(){
        console.info('画一个圆形')
    }
}

class Decorator{
    constructor(circle){
        this.circle = circle
    }
    draw(){
        this.circle.draw()
        this.setRedBorder(circle)
    }
    setRedBorder(circle){
        console.info('设置红色边框')
    }
}

//测试代码
let circle = new Circle()
circle.draw()

let dec = new Decorator(circle)
dec.draw()
```



## 场景

- ES7装饰器

- core-decorators


```js
class Math{
    @log
    add(a, b){
        return a + b
    }
}

function log(target, name, descriptor){
    let oldValue = descriptor.value
    descriptor.value = function () {
        console.log(`calling ${name} with`, arguments)
        oldValue.apply(this, arguments)
    }
    return descriptor
}

let math = new Math()
const result = math.add(2, 4)
console.log('result', result)
```



## 设计原则验证

- 将现有对象和装饰器进行分离，两者独立存在

- 符合开放封闭原则















