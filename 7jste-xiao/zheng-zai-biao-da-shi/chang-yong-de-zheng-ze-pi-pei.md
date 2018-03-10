##获取中文字符

```
function GetChinese(strValue) {
  if (strValue != null && strValue != "") {
    var reg = /[\u4e00-\u9fa5，。？；]/g;
    strValue = strValue.match(reg).join("");
    return strValue;
  }
  else
    return "";
}
```



##正则表达式方法test、exec、match、replace、search

- replace函数返回根据正则表达式进行文字替换后的字符串的复制

- test函数用法：该方法的返回值是布尔值，通过该值可以匹配字符串中是否存在于正则表达式相匹配的结果

- match函数用法：使用正则表达式模式对字符串执行查找，并将包含查找的结果作为数组返回

- search方法：返回与正则表达式查找内容匹配的第一个子字符串的位置 

- exec方法：通过对指定你的字符串进行一次匹配检测，获取字符串中的第一个与正则表达式的内容，并且将匹配的内容和子匹配的结果存放在返回数组中




