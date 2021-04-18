# 6.本地构建

## 版本号X.Y.Z

* Z bugfix升级Z位
* Y 新增功能，向后兼容
* X 大版本升级，不保证兼容。Linux的X偶数代表稳定版，奇数位代表不稳定版
* 1.2.\* 同 ~1.2.0 Z位自动升
* 2.x 同 ^2.0.0 Y位和Z位自动升

## gulp

* npm run gulp

```text
"main": "index.js",
  "scripts": {
    "gulp": "gulp"
  },
  "author": "",
```

### glob

* \*匹配任意个字符
* ?匹配一个字符
* \[...\]匹配范围内字符
* !\(pattern1\|pattern2\)匹配取反
* ?\(pattern1\|pattern2\)匹配0或1个
* +\(pattern1\|pattern2\)匹配1或多个
* \*\(a\|b\|c\)匹配任意个
* @\(pattern\|pat\*\|pat?erN\)匹配特定的一个
* \*\*匹配任意层级

```javascript
const gulp = require('gulp');
const less = require('gulp-less');
const autoprefixer = require('gulp-autoprefixer');
const cleanCss = require('gulp-clean-css');
const del = require('del');

gulp.task('clean', () => {
    del.sync('build');
});

gulp.task('less', () => {
    gulp.src('./src/**/*.less')
    .pipe(less())
    .pipe(autoprefixer({
        browsers: ['last 5 versions', 'firefox > 20'],
        cascade: false
    }))
    .pipe(cleanCss())
    .pipe(gulp.dest('build'));
});

gulp.task('default', ['clean', 'less'], () => {
    console.info('done!');
});

gulp.task('watch', () => {
    const watcher = gulp.watch('./src/**/*', ['default']);
    watcher.on('change', function (event) {
        console.log('File ' + event.path + ' was ' + event.type + ', running tasks...');
    });
});
```

## babel

## webpack

