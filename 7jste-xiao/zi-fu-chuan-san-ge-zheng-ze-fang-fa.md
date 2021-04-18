# 字符串三个正则方法

* trim\(\);去除前后的空格

  ```text
  var str = "     你好  我很好！     ";
  console.log(str);
  console.log(str.trim());
  ```

* replace\(\); 替换和全局替换值。

  ```text
  var str = "Today is fine day,today is fine day!"
  console.log(str);
  console.log(str.replace(/today/ig,"tomorrow"));
  //i表示忽略大小写，g表示全局替换
  ```

* search\(\);  给字符差索引

  ```text
  var str = "abcdefg";
  console.log(str.search(/bc/));
  console.log(str.indexOf("bc"));
  ```

## 自己封装trim\(\)

```text
        function trim(str){
            var aaa = str.replace(/(^\s+)|(\s+$)/g,"");
            return aaa;
        }
```

## \(?!\) 正向预搜索否定，判断当前位置右侧是否不能够匹配指定表达式

## \(?!th$\) 表示向后面搜索不是已th结尾的

