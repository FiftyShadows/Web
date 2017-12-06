##泛型

```
function identity<T>(arg: T): T {
    return arg;
}
```

我们给identity添加了类型变量T。 T帮助我们捕获用户传入的类型（比如：number），之后我们就可以使用这个类型。 之后我们再次使用了 T当做返回值类型。现在我们可以知道参数类型与返回值类型是相同的了。 这允许我们跟踪函数里使用的类型的信息。

- 定义了泛型函数后，可以用两种方法使用。 第一种是，传入所有的参数，包含类型参数：

`let output = identity<string>("myString");  // type of output will be 'string'`

- 第二种方法更普遍。利用了类型推论 -- 即编译器会根据传入的参数自动地帮助我们确定T的类型：

`let output = identity("myString");  // type of output will be 'string'`

```
function loggingIdentity<T>(arg: Array<T>): Array<T> {
    console.log(arg.length);  // Array has a .length, so no more error
    return arg;
}
```















