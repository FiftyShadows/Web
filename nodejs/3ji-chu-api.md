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










 










