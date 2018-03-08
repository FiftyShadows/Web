##数据判空

- 二级属性判空


##图片的裁剪



##用wx.switchTab()调到选项卡



##CSS3设置图片模糊的属性

```
    -webkit-filter: blur(5px); /* Chrome, Safari, Opera */
    filter: blur(5px);
```




##图片预览功能

```
 viewMoviePostImg: function (e) {
    var src = e.currentTarget.dataset.src;
    wx.previewImage({
      current: src, // 当前显示图片的http链接
      urls: [src] // 需要预览的图片http链接列表
    })
  },
```