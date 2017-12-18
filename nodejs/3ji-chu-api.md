##path

- normalize()    标准化地址

```
const {normalize} = require('path');

console.log(normalize('C:\Users\LY\Desktop\node'));
console.log(normalize('C:\Users\LY\..\node'));
console.log(normalize('/usr//local/bin//main.js'));
```

- join()    拼接路径，并标准化（normalize）

```
const {join} = require('path');

console.log(join('/usr', 'local', 'bin/'));
console.log(join('/usr', '../local', 'bin/'));
```

- resolve() 相对路径解析成绝对路径

```
const {resolve} = require('path');

console.log(resolve('./'));
```


- basename、dirname、extname

文件名、路径、扩展名

```
const { basename, dirname, extname } = require('path');

const filePath = 'C:/Users/LY/Desktop/datepicker/data.js';

console.log(basename(filePath));

console.log(dirname(filePath));

console.log(extname(filePath));
```

- parse、format

把一个文件名解析成上面的几部分，format反操作，会从一个对象返回一个路径字符串(可用于修改文件名)

```
const {parse, format} = require('path');

const filePath = '/usr/local/node_modules/n/package.json';

const ret = parse(filePath);

console.log(ret);

console.log(format(ret));
```

- sep、delimiter、win32、posix

```
const {sep,delimiter,win32,posix} = require('path');

console.log('sep:', sep);
console.log('posix sep:', posix.sep);

console.log('PATH:', process.env.PATH);

console.log('delimiter:', delimiter);
console.log('posix delimiter:', posix.delimiter);

// sep: \
// posix sep: /
// PATH: C: \Windows\system32; C: \Windows; C: \Windows\System32\Wbem; C: \Windows\System32\WindowsPowerShell\v1.0\; C: \Program
// Files\Git\cmd; C: \Program Files\nodejs\; C: \Users\LY\AppData\Local\Microsoft\WindowsApps;; C: \Program Files\Microsoft VS Code\bin; C: \Users\LY\AppData\Roaming\npm
// delimiter: ;
// posix delimiter: :

```
 
- __dirname、process.cwd()、path.resolve('./')区别

`__dirname、__filename`总是返回文件的绝对路径

process.cwd()总是返回执行node命令所在的文件夹

`./`在resolve方法中总是相对当前文件所在文件夹

在其他地方和process.cwd()一样，相对node启动文件夹




##Buffer

- Buffer用于处理二进制数据流

- 实例类似整数数组，大小固定

- C++代码在V8堆外分配物理内存


####创建Buffer

```
console.log(Buffer.alloc(10));
console.log(Buffer.alloc(20));
console.log(Buffer.alloc(5, 1));
console.log(Buffer.allocUnsafe(10));

console.log(Buffer.from([1, 2, 3]));
console.log(Buffer.from('test'));
console.log(Buffer.from('test', 'base64'));

```

- Buffer类的常用方法

```
/*
Buffer.byteLength
Buffer.isBuffer()
Buffer.concact()
*/

console.log(Buffer.byteLength('test'));
console.log(Buffer.byteLength('测试'));

console.log(Buffer.isBuffer({}));
console.log(Buffer.isBuffer(Buffer.from([1, 2, 3])));

const buf1 = Buffer.from('this ');
const buf2 = Buffer.from('is ');
const buf3 = Buffer.from('a ');
const buf4 = Buffer.from('test');
const buf5 = Buffer.from('.');
const buf = Buffer.concat([buf1, buf2, buf3, buf4, buf5]);
console.log(buf.toString());
```

- 实例的常用方法

```
/*
buf.length
buf.toString()
buf.fill()
buf.equals()
buf.indexof()
buf.copy()
*/

const buf1 = Buffer.from('This is a test.');
console.log(buf1.length);
console.log(buf1.toString('base64'));
const buf2 = Buffer.from('测试');
console.log(buf2.length);
const buf3 = Buffer.allocUnsafe(10);
buf3[0] = 2;
console.log(buf3.length);

const buf4 = Buffer.allocUnsafe(10);
console.log(buf4.fill(10, 2, 6));

const buf5 = Buffer.from('test');
const buf6 = Buffer.from('test');
const buf7 = Buffer.from('test!');
console.log(buf5.equals(buf6));
console.log(buf5.equals(buf7));

console.log(buf5.indexOf('es'));
console.log(buf5.indexOf('esa'));
```


- 中文乱码问题


