##CommonJS

- 每个文件是一个模块，有自己的作用域

- 在模块内部module变量代表模块本身

- module.exports属性代表模块对外接口



##require规则

- /表示绝对路径，./表示相对于当前文件的

- 支持js、json、node扩展名，不写依次尝试

- 不写路径则认为是build-in模块或者各级node_modules内的第三方模块



##require特性

- module被加载的时候执行，加载后缓存

- 一旦出现某个模块被循环加载，就只输出已经执行的部分，还未执行的部分不会输出




##exports和module.exports的区别

exports相当于module.exports的快捷方式， `const exports = module.exports;`

不能改变exports的指向，否则不生效

```js
// const exports = module.exports;

// (
//     function(exports, require, module, __filename, __dirname) {
//         //code
//     }
// );

// exports.test = 100;

exports = {
    a: 1,
    b: 2,
    test: 100
}; 
```

CommonJS对外输出的永远是module.exports




##global

- CommonJS

- Buffer、process、console

- timer

`global.testVar2 = 200;`




##process

####argv

node --inspect .\10_argv.js -test a=1 b=2

```js
const {argv, argv0, execArgv, execPath} = process;

argv.forEach(function(item){
    console.log(item);
});

console.log(argv0);

console.log(execArgv);

console.log(execPath);
```

####env

```
const {env} = process;

console.log(env);
```

####cwd

```
console.log(process.cwd());

process.cwd();
```


####setImmediate和precess.nextTick

下一个事件队列执行，同步执行完后执行

```js
//最慢，放在下个队列的队首，常用
setImmediate(() => {
    console.log('setImmediate');
});

setTimeout(() => {
    console.log('setTimeout');
}, 0);

//最快,放在当前事件队列最后一个，内部的循环调用，长时间调用会影响异步程序
process.nextTick(() => {
    console.log('nextClick');
});

```



##调试

####chrome
- chrome://inspect

- 安装chrome插件NIM

- node --inspect-brk 14_debug.js

####VSCode

