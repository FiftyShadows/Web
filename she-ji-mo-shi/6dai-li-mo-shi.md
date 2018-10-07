## 介绍

- 使用者无权访问目标对象

- 中间加代理，通过代理做授权和控制


![](/assets/微信截图_20181007184934.png)


```js
class RealImg{
    constructor(fileName){
        this.fileName = fileName
        this.laodFromDisk()
    }
    display(){
        console.log('display...' + this.fileName)
    }
    loadFromDisk(){
        console.log('loading...' + this.fileName)
    }
}

class ProxyImg{
    constructor(fileName){
        this.realImg = new ReadImg(fileName)
    }
    display(){
        this.realImg = new ReadImg(fileName)
    }
}

//test
let prixyImg = new ProxyImg('1.png')
proxyImg.display()
```



## $.proxy

```js
$('#div1').click(function (){
    setTimeout($.proxy(function (){
        $(this).css('background-color', 'yellow')
    }, this), 1000)
})
```



```
//明星
let star = {
    name: 'xxx',
    age: 25,
    phone: 'star: 13100001111'
}

//经纪人
let agent = new Proxy(star, {
    get: function(target, key){
        if(key === 'phone'){
            return 'agent: 18888888888'
        }
        if(key === 'price'){
            return 120000
        }
        return target[key]
    },
    set: function(target, key, val){
        if(val < 100000){
            throw new Error('价格太低')
        }
        else{
            target[key] = val 
            return true
        }
    }
})

//test
console.log(agent.name)
console.log(agent.age)
console.log(agent.phone)
console.log(agent.price)

agent.customPrice = 150000
```



## 设计原则验证

- 代理类和目标类分离，隔离开目标类和使用者

- 符合开放封闭原则


## 代理模式vs适配器模式

- 适配器模式： 提供一个不同的接口（如不同版本的插头）

    - 不能使用

- 代理模式： 提供一模一样的接口

    - 无权使用
    


## 代理模式vs装饰器模式

- 装饰器模式： 扩展功能，原有功能不变且可直接使用

- 代理模式： 显示原有功能，但是经过限制或者阉割之后的
