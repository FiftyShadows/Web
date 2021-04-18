# 7.JS特效

## 既能获取又能赋值（行内样式）

* div.style.width                           单个赋值
* div.style\[“width”\]                变量赋值

获取属性值：（只能获取）

* div.currentStyle.width;   IE678        单个获取
* window.getComputedStyle\(div,null\).width;
* div.currentStyle\[“width”\];   IE678        变量获取
* window.getComputedStyle\(div,null\)\[“width”\];

  ```text
  参数1：获取属性的元素。参数2：伪元素，C3学习。
  ```

## 缓动框架封装（回调函数）

```javascript
function animate(ele,json,fn){
            //先清定时器
            clearInterval(ele.timer);
            ele.timer = setInterval(function () {
                //开闭原则
                var bool = true;


                //遍历属性和值，分别单独处理json
                //attr == k(键)    target == json[k](值)
                for(var k in json){
                    //四部
                    var leader = parseInt(getStyle(ele,k)) || 0;
                    //1.获取步长
                    var step = (json[k] - leader)/10;
                    //2.二次加工步长
                    step = step>0?Math.ceil(step):Math.floor(step);
                    leader = leader + step;
                    //3.赋值
                    ele.style[k] = leader + "px";
                    //4.清除定时器
                    //判断: 目标值和当前值的差大于步长，就不能跳出循环
                    //不考虑小数的情况：目标位置和当前位置不相等，就不能清除清除定时器。
                    if(json[k] !== leader){
                        bool = false;
                    }
                }

                console.log(1);
                //只有所有的属性都到了指定位置，bool值才不会变成false；
                if(bool){
                    clearInterval(ele.timer);
                    //所有程序执行完毕了，现在可以执行回调函数了
                    //只有传递了回调函数，才能执行
                    if(fn){
                        fn();
                    }
                }
            },25);
        }




        //兼容方法获取元素样式
        function getStyle(ele,attr){
            if(window.getComputedStyle){
                return window.getComputedStyle(ele,null)[attr];
            }
            return ele.currentStyle[attr];
        }
```

## JS一般不用小数运算，小数运算会造成精度丢失。

