## template为空时run dev会报错 Cannot read property 'for' of undefined



![](/assets/360截图18790311314767.png)



## 小程序语法缺点

- 不能使用npm，使用第三方包的方式太原始

- 需要为小程序单独开发代码，不能和web系统重用

- 开发效率和学习成本(小程序特有的语法)




## const在性能上会有提升



## 展开运算符

- [1, 2, ...arr]


## 对象方法简写

```
const key = 'job';

const obj = {
    key,
    num: 1,
    str: 'woniu',
    work(){
    
    },
    [key]: 'fe',
    [key + 'world']: 'fe'
};

console.info(obj);
```



## 解构赋值




## import Todolist from '@/components/Todolist';    @默认为src下




































