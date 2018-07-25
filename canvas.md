##requestAnimationFrame和cancelAnimationFrame根据帧率动态调整

- 用于动画，刷新率由浏览器决定，每一次浏览器的帧率刷新之前执行，性能远高于setTimeout和setInterval





##ctx.drawImage

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



ctx.moveTo(100,100)

ctx.lineTo(700,700)

ctx.lineWidth = 5

ctx.strokeStyle = "#005588"

ctx.stroke()

ctx.fillStyle = "rgb(2,100,30)"

ctx.fill()    closePath不会起作用，自动首尾相连，填充

canvas的绘制是基于状态的

ctx.beginPath()

ctx.closePath()    会自动连接首尾

ctx.arc(centerx, centery, radius, startingAngle, endingAngle, anticlockwise = false)

ctx.arc(300, 300, 200, 0, 1.5*Math.PI)

ctx.clearRect(0, 0, ctx.canvas.width, ctx.canvas.height)