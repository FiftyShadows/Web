[https://www.imooc.com/video/13640](https://www.imooc.com/video/13640)

上一个流会随着下一个流的产生而被抛弃掉

```js
var text =document.querSelector("#text");
var inputStream = Rx.Observable.fromEvent(text,'keyup')
                .pluck('targeet', 'value')
                .flatMapLatest(url => Http.get(url))
                .subscribe(data => render(data));
```

## 入门

```
var streamA$ = Rx.observable.jsut(2)
                .map(s => s*2);                //事件源 
streamA$.subscribe(v => console.log());                //订阅与响应
```

Rx提供了许多接口

创建、转变、过滤、组合、错误处理

#### 创建

just、fromEvent

#### 转变

map、FlatMap、FlatMapLatest

![](/assets/360截图20171207104022918.jpg)

#### 过滤

filter、debounce(函数过渡)

#### 组合

merge

#### 错误处理

catch                如果可观察者的流出错，则执行catch里的可观察者，成功则返回值，不会返回错误。

![](/assets/360截图20171207104451166.jpg)

![](/assets/360截图20171207104759790.jpg)

![](/assets/360截图20171207105127761.jpg)

## 优点

* 代码简洁

* 函数式

* 可组合

* 伸缩性强（方便改变需求）

* 错误处理

* 并发处理

* 局部到整体

* 同步到异步

* 事件与数据

* 前端和后端

* 与其他框架结合



