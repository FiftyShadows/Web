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
let input = [1, 2];
function f([first, second]: [number, number]) {
    console.log(first);
    console.log(second);
}
f(input);
```









