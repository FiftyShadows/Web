# 3.电影资讯页面

## 配置选项卡tabBar

* 从welcome页面跳进tabBar页面时，需要用wx.navigateTo\(\),否则wx.directedTo不显示
* app.json里配好路径，会自动生成模板文件

```text
//app.json
{
    "tabBar": {
        "borderStyle": "white",
        "position": "bottom",
        "list": [
            {
                "pagePath": "pages/posts/post",
                "text": "阅读",
                "iconPath": "xxx",
                selectedIconPath: "xx"
            },{

            }
        ]
    }
}
```

## 电影组件的编写

* 豆瓣api，只有Required Scope\(movie\_basic\_r\)
* template的引用关系\(movie-list\) -&gt; \(movie\) -&gt; \(star\)
* template里的样式类最好加上相应的前缀
* 从最小的模板到大的模板编写
* justify-content可以用来代替float，但是子元素的vertical-align: middle;将会无效
* 设计中一般很少用纯黑色，最常用的是333和666，注释999
* 用wx:if实现星星显示或不显示

```text
//从movie-list传递数据到stars
<template is="starsTemplate" data="{{starts:stars,score:average}}" />




//半星的实现，假定处理的数组为[1,1,1,2,0]
<block wx.for="{{starts}}" wx.for-item="i">
    <image wx.if="{{i==1}}" src="xxx"></image>
    <image wx.elif="{{i==2}}" src="xxx"></image>
    <image wx.else="{{i==0}}" src="xxx"></image>
</block>
```

## 从服务器的RESTful API调用数据

* wx.request\(\)失败时调用fail;失败指的是断网或者请求超时
* 减少服务器的压力，客户端的缓存和优化
* template占位符加样式无效

```text
wx.request({
      url: url,
      method: 'GET', // OPTIONS, GET, HEAD, POST, PUT, DELETE, TRACE, CONNECT
      header: {
        "Content-Type": "json"
      },
      success: function (res) {
        that.processDoubanData(res.data, settedKey, categoryTitle)
      },
      fail: function (error) {
        // fail
        console.log(error)
      }
    })
```

## 把api获取的数据封装到Data当中

* 通过for in 的形式把res.data写入到Page.Data当中，注意title的长度的处理if{title.length &gt;= 6} title = title.substring\(0, 6\) + '...'
* this.setData\({'top250': {}}\);这个top250的key值不能通过变量的形式传递，所以需要用readyData\[settedKey\]的形式来赋值。
* 需要给Data设置初始值，因为http请求是异步的，不设置则会读取不到

```text
Data:{
    inTheaters: {movies: []},
    comingSoon: {movies: []},
    top250: {movies: []}
}
//以展开的形式向子组件传递值
```

## 组件间传递数据的方式

* 全局变量
* 缓存
* Url
* 发射事件和接收事件

## 导航栏动态标题的显示

* onLoad是页面初始化，不应该操作跟UI相关的东西的
* 要在onReady后面的生命周期中设置

## 上拉加载更多，数据的concat

* 在more-grid中加入`<scroll-view class="grid-container" scroll-y="true" scroll-x="false" bindscrolltolower="onScrollLower">`，并设置高度
* 一个方法最多不超过10行，方法越小越灵活，代码重发的可能性就越小

## wx.showNavigationBarLoading\(\)和wx.hideNavigationBarLoading\(\);在导航栏上加载loading图标

## 下拉刷新

* 在more-movie.json中配置{"enablePullDownRefresh": true}
* 停止刷新wx.stopPullDownRefresh\(\);

## window配置下的backgroundColor指的是下拉刷新空白区域的颜色

## 搜索页面的显隐

## 搜索功能，input标签bindchange

## app.json的list绝对路径前不能加/

