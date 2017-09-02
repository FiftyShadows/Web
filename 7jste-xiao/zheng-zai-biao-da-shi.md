#用来记录文本规则的代码

#表单验证、高级搜索、生化科学

#由普通字符和元字符组成

1. 内置对象法，var reg1 = new RegExp(/abc/);

1. 字面量  var reg2 = /def/;

#正则表达式有一个方法test(),检测字符串是否符合该规则。返回true或false。

- reg2.test("def");
- /abc/.test("abac");


***

#五大内部类