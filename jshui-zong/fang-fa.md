##in关键字的用法

1. 最常用的是在for in 循环中遍历对象的键

```

```


##window.innerWidth




##this本身表示函数运行时自动生成的内部对象，只能在函数内部使用，随着函数使用场合的不同，this的值会发生变化。总的原则：this指得是调用函数的对象。

1. 当其出现在setTimeout的函数参数中时，函数参数是一个纯粹的函数调用，并不隶属于哪个对象，属于全局调用，这种情况下this指的是全局对象global。

2. 当this出现在对象的函数中时，this指的是对象。

3. 在构造函数中，指的是new生成的空对象。

4. apply,call,bind方法中的第一个参数。




##try catch finally

- catch子句包含try块中抛出异常时要执行的语句。也就是，你想让try语句中的内容成功， 如果没成功，你想控制接下来发生的事情，这时你可以在catch语句中实现。 如果有在try块中有任何一个语句（或者从try块中调用的函数）抛出异常，控制立即转向catch子句。如果在try块中没有异常抛出，会跳过catch子句。

- finally子句在try块和catch块之后执行但是在下一个try声明之前执行。无论是否有异常抛出或着是否被捕获它总是执行。




##encodeURIComponent

- encodeURIComponent 转义除了字母、数字、(、)、.、!、~、*、'、-和_之外的所有字符。

- 为了避免服务器收到不可预知的请求，对任何用户输入的作为URI部分的内容你都需要用encodeURIComponent进行转义。比如，一个用户可能会输入"Thyme &time=again"作为comment变量的一部分。如果不使用encodeURIComponent对此内容进行转义，服务器得到的将是comment=Thyme%20&time=again。请注意，"&"符号和"="符号产生了一个新的键值对，所以服务器得到两个键值对（一个键值对是comment=Thyme，另一个则是time=again），而不是一个键值对。