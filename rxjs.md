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






















