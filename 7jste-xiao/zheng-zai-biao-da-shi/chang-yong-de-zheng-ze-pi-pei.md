##获取中文字符

```
function getContent() {
  if (strValue != null && strValue != "") {
    var reg = /[\u4e00-\u9fa5，。？；]/g;
    return strValue.match(reg).join("");
  }
  else
    return "";
}
```




