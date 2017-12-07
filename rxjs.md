```js
var text =document.querSelector("#text");
var inputStream = Rx.Observable.fromEvent(text,'keyup')
                .pluck('targeet', 'value')
                .flatMapLatest(url => Http.get(url))
                .subscribe(data => render(data));
```


##入门

```
var streamA$ = Rx.observable.jsut(2)
                .map(s => s*2);                //事件源 
streamA$.subscribe(v => console.log());                //订阅与响应 
```

Rx提供了许多接口

创建、转变、过滤、组合、错误处理



####创建

just、fromEvent


####转变

map、FlatMap、FlatMapLatest

![](/assets/360截图20171207104022918.jpg)


####过滤

filter、debounce


####组合

merge



####错误处理

catch

![](/assets/360截图20171207104451166.jpg)


![](/assets/360截图20171207104759790.jpg)


![](/assets/360截图20171207105127761.jpg)




##优点

- 代码简洁

- 函数式

- 可组合

- 伸缩性强（方便改变需求）

- 错误处理







