# My Awesome Book

This file file serves as your book's preface, a great place to describe your book's content and ideas.

#顶级标题

##次级标题

###次次级标题

- 列表项1
- 列表项1
- 列表项1
- 列表项1

* 第一个
* 第二个
* 第三个
    * 次级
        * 次次级
        
        
1. first
1. second
1. third

>引用的一段名言

[百度](http://www.baidu.com)

![这是一张图片](https://www.baidu.com/img/bd_logo1.png)

国务院总理 *李克强8月30日主持召开* 国务院常务会议，决定推广一批具备复制条件的 **支持创新改革举措** ，为创新发展营造更好环境；确定促进健康服务业发展的措施， ***满足群众需求*** 、提高健康水平。



# 表格

|表格1|表格2表格2表格2表格2|表格3表格3表格3表格3|
|---|:---:|---:|
| aaa | 123 | 654 |
| bbb | 456 | 789 |





***
* 单行代码
这是一行代码`hello everybody!`哟


* 多行代码

```javascript

    function animate(ele,target){
        //清除定时器
        clearInterval(ele.timer);
        ele.timer = setInterval(function () {
            //四部：
            //获取步长
            var step = (target - ele.offsetLeft)/10;
            //二次处理步长
            step = step>0?Math.ceil(step):Math.floor(step);
            //赋值
            ele.style.left = ele.offsetLeft + step + "px";
            //清除定时器
            console.log(1);
            if(Math.abs(target-ele.offsetLeft)<=Math.abs(step)){
                ele.style.left = target + "px";
                clearInterval(ele.timer);
            }
        },30);
    }

```


<i>你好</i>


1. nihao
nihao

1. nihao



GitBook本地保存位置
C:\Users\Administrator\GitBook\Library\Import\qian_duan


EPLLY