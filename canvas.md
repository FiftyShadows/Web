##requestAnimationFrame和cancelAnimationFrame根据帧率动态调整

- 用于动画，刷新率由浏览器决定，每一次浏览器的帧率刷新之前执行，性能远高于setTimeout和setInterval





##ctx.dawnImage

```
this.ctx.drawImage = {  
    image对象，  
    image的x起始位置，  
    image的y起始位置，  
    image.width,  
    image.height,  
    放置在画布的位置0,  
    0，  
    image.width,      //使用图片的大小
    image.height  
};
```