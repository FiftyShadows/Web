```js
var text =document.querSelect("#text");
var inputStream = Rx.Observable.fromEvent(text,'keyup')
                                .pluck('targeet', 'value')
                                .flatMapLatest(url => Http.get(url))
                                .subscribe(data => render(data));
```