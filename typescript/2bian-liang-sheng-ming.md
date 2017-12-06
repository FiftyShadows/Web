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























