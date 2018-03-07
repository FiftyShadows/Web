##知识点

- Swiper组件

- App.json里的关于导航栏、标题配置

- Page页面与应用程序的生命周期

- 数据绑定（核心知识）

- 数据绑定的运算与逻辑

- AppDate区域介绍

- 事件与事件对象

- 缓存

    增强用户体验，手动去清除，否则会一直存在，最大10M
    
- 列表渲染（核心知识）

- Template模板的使用（核心知识）


```
//swipe-item仅可放置在swipe组件中，宽高自动设置为100%，image不会10%

//post.wxml
<view>
    <swipe indicator-dots="true" autoplay="true" interval="5000" vertical="true">
        <swiper-item>
            <image src="/iamges/wx.png"></image>
        </swiper-item>
        <swiper-item>
            <image src="/iamges/vr.png"></image>
        </swiper-item>
        <swiper-item>
            <image src="/iamges/iqiyi.png"></image>
        </swiper-item>
    </swipe>
</view>>


//post.wxss
swipe{
    width: 100%;
    hieght: 600rpx;
}
swipe iamge{
    width: 100%;
    hieght: 600rpx;
}
.post-container{
    display: flex;
    flex-direction: column;
    margin-top: 20rpx;
}

//post.json,页面下的配置文件只能配置window，app下的能够配置很多
{
    "navigationBarBackgroundColor": "#405f80",
    "navgationBarTitleText": "文与字",
    "navigationBarTextStyle": "red"
    
}


//post.js
Page({
    data: {
    },
    image: '/images/...',
    process: function(){},
    onLoad: function(options){},
    onReady: function(){},
    onShow: function(){},
    onHide: function(){},
    onUnload: function(){}
})
```


##if判断和for循环，以及小的细节

- 编写css代码时，要把离散的内容按照规律组合起来

- 生命周期执行顺序onLoad -> onShow -> onReady

- `<swipe indicator-dots="true" autoplay="true" interval="5000" vertical="fase">`小程序会把字符串转换成布尔类型，所以vertical="false"并不会起作用，vertical="{{false}}"

- 控制显隐`<view wx:if="{{img_condition}}"></view>`

- 还可以做字符串的运算`<text>{{'hello' + date}}</text>`,`<text>{{a + b + c}}</text>`这里会做运算并显示，不会直接显示文本

- 循环data里的数据到视图，注意data的设置问题

- wx:for-item和wx:for-index的默认值是item和index

```
<block wx:for="{{posts_key}}" wx:for-item="{{item}}" wx:for-index="idx">
    <view>{{item.title}}{{idx}}</view>
</block>

Page({
    data: {
    posts_key: []
    },
    image: '/images/...',
    process: function(){},
    onLoad: function(options){
        var posts_postcontents = [{title: "123"}, {title: "456"}];
        this.setData({
            posts_key: posts_content
        });
    },
    onReady: function(){},
    onShow: function(){},
    onHide: function(){},
    onUnload: function(){}
})

```



##事件

- tap类似于click事件，点击一次执行两次的bug，关闭重新打开

- redirectTo是两个页面平行跳转，不存在子父页面的关系；navigateTo从父级页面跳转到子级页面的关系，子级最多只能有5级

- navigateTo的生命周期是onHide，父级页面只是被隐藏，所以能做快捷的切换操作；redirectTo的生命周期是onUnload，页面被关闭或卸载了，平行页面被关闭了

- 非冒泡时间：`<form/>`的submit事件，`<input/>`的input事件，`<scroll-view>`的scroll事件

- catchtap能够阻止冒泡，bindtap不能

```
Page({
    onTap: function(){
        wx.navigateTo({
            url: "../posts/post"
        });
        wx.redirectTo({
            url: "../posts/post"
        })
    }
})
```

```
Page({
    onTap: function(){
        wx.navigateTo({
            url: "../posts/post",
            success: function(res){
                //success
            },
            fail: function(){
                //fail
            },
            complete: function(){
                //无论成功失败都会执行
            }
        });
})

```


```
var postsData = require('../../data/posts-data.js');    //必须用相对路径

Page({
    data: {
        //小程序总是会读取data对象来做数据绑定，这个动作我们称为动作A
        //而这个动作A的执行，是在onLoad事件执行之后发生，
    },
    onLoad: function(options){
        //页面初始化options为页面跳转所带来的参数
        
        this.data.postList = postsData.postList;
        //this.setData({
            //posts_key: postsData.postList;
        //});
    }
});
```




##template模板

- 脚本文件无效，小程序的template只是实现了模板化的编程，而没有实现模块化的编程

```
//post-item-template.wxml
<template name="postItem">
    <view></view>
</template>


//post.wxml
<import src="post-item/post-item-template.wxml" />    //少写/会导致出错，相对路径和绝对路径都可以
<block wx:for={{postList}} wx:for-item="item" wx:for-index="index">
    <template is="postItem" data="{{item}}" />    //出发点：并非只是在一个页面中引用，编程的复用思想
</block>


//post.wxss
@import "post-item/post-item-template.wxss";
```