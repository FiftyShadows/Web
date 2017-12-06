##let,const和var

const是对let的一个增强，它能阻止对一个变量再次赋值。

var作用域或函数作用域。函数参数也使用函数作用域。

```
const numLivesForCat = 9;
const kitty = {
    name: "Aurora",
    numLives: numLivesForCat,
}

// Error
kitty = {
    name: "Danielle",
    numLives: numLivesForCat
};

// all "okay"
kitty.name = "Rory";
kitty.name = "Kitty";
kitty.name = "Cat";
kitty.numLives--;
```

**实际上const变量的内部状态是可修改的。**

使用最小特权原则，所有变量除了你计划去修改的都应该使用const。 基本原则就是如果一个变量不需要对它写入，那么其它使用这些代码的人也不能够写入它们，并且要思考为什么会需要对这些变量重新赋值。 使用 const也可以让我们更容易的推测数据的流动。



##解构数组

- 解构赋值

```
let input = [1, 2];
let [first, second] = input;
console.log(first); // outputs 1
console.log(second); // outputs 2
```

- 解构作用于已声明的变量会更好

```
// swap variables
[first, second] = [second, first];
```

- 作用于函数参数

```
function f([first, second]: [number, number]) {
    console.log(first);
    console.log(second);
}
f([4582, 16762]);
```

- 在数组里使用...语法创建剩余变量

```
let [first, ...rest] = [1, 2, 3, 4];
console.log(first); // outputs 1
console.log(rest); // outputs [ 2, 3, 4 ]
```

- 由于是JavaScript, 你可以忽略你不关心的尾随元素

```
let [first] = [1, 2, 3, 4];
console.log(first); // outputs 1

let [, second, , fourth] = [1, 2, 3, 4];
```



##对象解构

- 也可以解构对象

```
let o = {
    a: "foo",
    b: 12,
    c: "bar"
};
let { a, b } = o;
```

- 在对象里使用...语法创建剩余变量

```
let o = {
    a: "foo",
    b: 12,
    c: "bar"
};
let { a, ...passthrough } = o;
let total = passthrough.b + passthrough.c.length;
```



##属性重命名

- 给属性以不同的名字

```
let o = {
    a: "foo",
    b: 12,
    c: "bar"
};
let { a: newName1, b: newName2 }: {a: string, b: number} = o;
```

这里的冒号不是指示类型的。 如果你想指定它的类型， 仍然需要在其后写上完整的模式。

let {a, b}: {a: string, b: number} = o;



##默认值




##函数声明

解构也能用于函数声明。 看以下简单的情况

```
type C = { a: string, b?: number }
function f({ a, b }: C): void {
    // ...
}
```




##展开

展开操作符正与解构相反。 它允许你将一个数组展开为另一个数组，或将一个对象展开为另一个对象.

```
let first = [1, 2];
let second = [3, 4];
let bothPlus = [0, ...first, ...second, 5];
```

展开操作创建了 first和second的一份**浅拷贝**。 它们不会被展开操作所改变。


####展开对象

```
let defaults = { food: "spicy", price: "$$", ambiance: "noisy" };
let search = { ...defaults, food: "rich" };
```

search的值为{ food: "rich", price: "$$", ambiance: "noisy" }。 对象的展开比数组的展开要复杂的多。 像数组展开一样，它是从左至右进行处理，但结果仍为对象。 这就意味着出现在展开对象后面的属性会覆盖前面的属性。 因此，如果我们修改上面的例子，在结尾处进行展开的话：

```
let defaults = { food: "spicy", price: "$$", ambiance: "noisy" };
let search = { food: "rich", ...defaults };
```

那么，defaults里的food属性会重写food: "rich"


######对象展开还有其它一些意想不到的限制

- 它仅包含对象 自身的可枚举属性。 大体上是说当你展开一个对象实例时，你会丢失其方法：










