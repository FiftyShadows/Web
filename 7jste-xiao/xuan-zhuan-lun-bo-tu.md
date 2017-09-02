array.push()在最后加入

array.unshift()在最前面加入

array.pop()删除最后一位

array.shift()删除最前边一位


#旋转木马
原理：我们先定义一个数组，数组中的元素是json；json中的元素是属性。
点击一个按钮，按顺序更换数组中元素的位置。
（如果我们想完成旋转木马，只需要更换数组中元素的位置）
步骤：
1.我们必须让页面加载的时候把所有的属性加载出来，让我看看。（核心）
2.鼠标放到大盒子上显示对应的左右切换按钮，移开隐藏
3.获取两个按钮。对他们进行事件绑定。对他们进行判断。
4.如果是左侧的按钮执行一套程序，如果是右侧的按钮执行另一套程序。
5.绑定按钮的函数，一个是正转，一个是反转。（传参确定）
6.调换相应的数组对应的元素。（先删除谁，在怎么添加）

#正转反转的问题
最开始是：12345；我想让他变成：23451
把1删除，在最后添加1；
在数组json中，删除第一个元素，添加到最末尾。（正转）
在数组json中，删除最后一个元素，添加到第一位。（反转）

#函数节流
定义一个变量，只有函数执行完毕在去执行下一个。


```javascript

/**
 * Created by Lenovo on 2016/9/13.
 */
window.onload = function () {
    var arr = [
        {   //  1
            width:400,
            top:70,
            left:50,
            opacity:20,
            zIndex:2
        },
        {  // 2
            width:600,
            top:120,
            left:0,
            opacity:80,
            zIndex:3
        },
        {   // 3
            width:800,
            top:100,
            left:200,
            opacity:100,
            zIndex:4
        },
        {  // 4
            width:600,
            top:120,
            left:600,
            opacity:80,
            zIndex:3
        },
        {   //5
            width:400,
            top:70,
            left:750,
            opacity:20,
            zIndex:2
        }
    ];

    //0.获取元素
    var slide = document.getElementById("slide");
    var liArr = slide.getElementsByTagName("li");
    var arrow = slide.children[1];
    var arrowChildren = arrow.children;
    //设置一个开闭原则变量，点击以后修改这个值。
    var flag = true;

    //1.鼠标放到轮播图上，两侧的按钮显示，移开隐藏。
    slide.onmouseenter = function () {
        //arrow.style.opacity = 1;
        animate(arrow,{"opacity":100});
    }
    slide.onmouseleave = function () {
        //arrow.style.opacity = 1;
        animate(arrow,{"opacity":0});
    }

    move();
    //3.把两侧按钮绑定事件。(调用同一个方法，只有一个参数，true为正向旋转，false为反向旋转)
    arrowChildren[0].onclick = function () {
        if(flag){
            flag = false;
            move(true);
        }
    }
    arrowChildren[1].onclick = function () {
        if(flag){
            flag = false;
            move(false);
        }
    }

    //4.书写函数。
    function move(bool){
        //判断：如果等于undefined,那么就不执行这两个if语句
        if(bool === true || bool === false){
            if(bool){
                arr.unshift(arr.pop());
            }else{
                arr.push(arr.shift());
            }
        }
        //在次为页面上的所有li赋值属性，利用缓动框架
        for(var i=0;i<liArr.length;i++){
            animate(liArr[i],arr[i], function () {
                flag = true;
            });
        }
    }

}
