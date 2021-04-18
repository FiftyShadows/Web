# scroll

```javascript
function scroll(){
            //如果这个属性存在，那么返回值应该是0-无穷大
            //如果没有返回值是undefined；
            //只要判断不是undefined就可以调用此方法
            //练习使用此种封装
            if(window.pageYOffset !== undefined){
//                var json = {
//                    "top": window.pageYOffset,
//                    "left": window.pageXOffset
//                };
//                return json;
                return {
                    "top": window.pageYOffset,
                    "left": window.pageXOffset
                };
            }else if(document.compatMode === "CSS1Compat"){
                return {
                    "top": document.documentElement.scrollTop,
                    "left": document.documentElement.scrollLeft
                };
            }else{
                return {
                    "top": document.body.scrollTop,
                    "left": document.body.scrollLeft
                };
            }

            //简单封装（实际工作使用）
           return {
             "top": window.pageYOffset || document.body.scrollTop || document.documentElement.scrollTop,
              "left":  window.pageXOffset || document.body.scrollLeft || document.documentElement.scrollLeft
          }
        }
```

