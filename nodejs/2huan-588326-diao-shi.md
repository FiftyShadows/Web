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










