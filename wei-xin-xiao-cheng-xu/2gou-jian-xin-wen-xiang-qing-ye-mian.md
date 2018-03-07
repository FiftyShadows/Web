##template另一种写法

```
//post.wxml
<template is="postItem" data="{{...item}}">


//template.wxml
<template name="postItem">
    <view>{{title}}</view>
</tempalte>
```


- template标签只是一个占位符，所以不能在template上加事件

```
//post.wxml
<block wx:for="{{postList}" wx:for-item="item" wx:for-index="idx">
    <view catchtap="onPostTap" data-postId="{{item.postId}}">
        <template is="postItem" data="{{...item}}"/>
    </view>
</block>


//post.js
Page({
    onPostTap: function(event){
        var postId = event.currentTarget.dataset.postid;
    }
});
```




##样式

- 先静后动，先样式后数据

- 父级盒子设置了`display: flex;`，子盒子也会编程弹性盒子模型，所以不需要再设置`display: flex;`，只需指定盒子模型的流动方向即可





##父组件给子组件传递数据：通过点击事件跳转的url里添加参数的形式

- app通过webview加载html网页

```
//post.js
Page({
    onTap: function(event){
        var postId = event.currentTarget.dataset.postid;
        wx.navigateTo({
            url: 'post-datail/post-datil?id=' + postId
        });
    }
});


//post-detail.js
var postsData = require('../../data/posts-data.js');
Page({
    onLoad: function(option){
        var postId = option.id;
        var postData = postsData.postList[postId];
        this.data.postData = postData;
    }
});
```


##缓存的几个方法

- wx.setStorageSync('key', {});

- wx.getStorageSync('key');

- wx.removeStorage('key');

- wx.clearStorageSync();

- 缓存的上限最大不能超过10M




##收藏功能图片的切换显示

```
//post-detail.wxml
<view class="circle-img">
    <image wx:if="{{collected}}" src="xxx"></iamge>
    <image wx:else src="xxx"></iamge>
</view>

//post-detail.js
Page({
    data:{},
    onLoad: function(option){
        var postId = option.id;
        this.data.currentPostId = postId;
        var postsCollected = wx.getStorageSync('posts_Collected');
        if(postsCollected){
            var collected = postsCollected[postId];
            this.data.collected = postsCollected;
        }else{
            var postsCollected = {};
            postsCollected[postId] = false;
            wx.setStorageSync('posts_Collected', postsCollected);
            this.data.collected = postsCollected;
        }
    },
    onTap: function(event){
        var postsCollected = wx.getStorageSync('posts_Collected');
        var postCollected = this.data.collected[this.data.currentPostId];
        postsCollected[this.data.currentPostId] = !postCollected;
        this.showToast(postsCollected, postCollected);
    } ,
    showModal: function(){},
    showToast: function(postsCollected, postCollected){
        wx.setStorageSync('posts_Collected', postsCollected);
        this.setData({
            collected: postsCollected
        });
        wx.showToast({
            title: postCollected? "收藏成功"： "取消成功",
            duration: 1000,
            icon: "success"
        });
    }
});
```


##showToast,showModal,showActionSheet


##同步和异步的选择

- 优先用同步，如果同步解决不了的问题再用异步

- 需要解耦时，选择异步



##切换图片的两种方式

- src="{{isPlaying? '/xx/xx/xx': '/xx/xx/xx'}}"

- wx:if



##音乐播放控件

```
//post-detail.js
onMusicTap: function(){
    var isPlayingMusic = this.data.isPlayingMusic;
    if(isPlayingMusic){
        wx.pauseBackgroundAuido();
        this.data.isPlayingMusic = false;
    }else{
        wx.playBackgroundAudio({
            dataUrl: "",
            title: "",
            coverImgUrl: ""
        });
        this.data.isPlayingMusic = true;
    }
}
```



##主控开关与音乐播放开关同步

- 事件驱动，在Nodejs，Angular中大量使用，模块与模块之间的松耦合

- 数据绑定，更好的方便做单元测试

```
wx.onBaackgroundAudioPlay(() => {
    this.setData({
        isPlayingMusic: true;
    });
});
```





##全局变量

- 利用全局变量，使跳出页面再返回时图片状态保持一致

- 跳出页面，进入其他页面时的状态

```
//app.js
App({
    globalData: {
        g_isPlayingMusic: false
    },
    onLaunch: function(){},    //切换前后台不会调用
    onShow: function(){},    //切换前后台会调用
    onHide: function(){}    //后台执行
});

//post-detail.js
var app = getApp();
Page({
    onLoad: (option) => {
        var globalData = app.globalDtat
    }
});
```

