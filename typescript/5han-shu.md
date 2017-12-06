##为函数定义类型

```
let myAdd: (x: number, y: number) => number =
    function(x: number, y: number): number { return x + y; };
    
let myAdd: (baseValue: number, increment: number) => number =
    function(x: number, y: number): number { return x + y; };
```

函数类型包含两部分：参数类型和返回值类型。



##可选参数和默认参数

- 在TypeScript里我们可以在参数名旁使用 ?实现可选参数的功能

- 可选参数必须跟在必须参数后面。

- 在TypeScript里，我们也可以为参数提供一个默认值当用户没有传递这个参数或传递的值是undefined时。 它们叫做有默认初始化值的参数。

- 在所有必须参数后面的带默认初始化的参数都是可选的，与可选参数一样，在调用函数的时候可以省略。

- 与普通可选参数不同的是，带默认值的参数不需要放在必须参数的后面。 如果带默认值的参数出现在必须参数前面，用户必须明确的传入 undefined值来获得默认值。



##剩余参数

```
function buildName(firstName: string, ...restOfName: string[]) {
  return firstName + " " + restOfName.join(" ");
}
let employeeName = buildName("Joseph", "Samuel", "Lucas", "MacKinzie");
```














