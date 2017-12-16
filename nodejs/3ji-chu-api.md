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
```
 










