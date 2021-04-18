# 4.构建电影详情页面

## 数据判空

* 二级属性判空

## 图片的裁剪

## 用wx.switchTab\(\)调到选项卡

## CSS3设置图片模糊的属性

```text
    -webkit-filter: blur(5px); /* Chrome, Safari, Opera */
    filter: blur(5px);
```

## 图片预览功能

```text
 viewMoviePostImg: function (e) {
    var src = e.currentTarget.dataset.src;
    wx.previewImage({
      current: src, // 当前显示图片的http链接
      urls: [src] // 需要预览的图片http链接列表
    })
  },
```

## event.detail

* 自定义事件所携带的数据，如表单组件的提交事件会携带用户的输入，媒体的错误事件会携带错误信息，详见组件定义中各个事件的定义。

点击事件的detail 带有的 x, y 同 pageX, pageY 代表距离文档左上角的距离。

