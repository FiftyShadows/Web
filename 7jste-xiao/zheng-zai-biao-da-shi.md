#用来记录文本规则的代码

#表单验证、高级搜索、生化科学

#由普通字符和元字符组成

1. 内置对象法，var reg1 = new RegExp(/abc/);(可定义空正则表达式)

1. 字面量  var reg2 = /def/;

#正则表达式有一个方法test(),检测字符串是否符合该规则。返回true或false。

- reg2.test("def");
- /abc/.test("abac");


***

#五大内部类


1. 预定义类
![](/assets/360截图20170902181158621.jpg)

2. 简单类（正则：//中什么特殊符号都不写，和[]的加入）
![](/assets/360截图20170903004655582.jpg)

3. 负向类
中括号内，前面加个元字符^进行取反，不是括号里面的字符（一部分也不行）。
(可以不够，但是不能多)（不够和正好，返回false；多了或者没有返回true）
```
 console.log(/[^abc]/.test('a'));
 console.log(/[^abc]/.test('gg'));
```
注意:  这个符号 ^  一定是写到方括号里面

4. 范围类
有时匹配的东西过多，而且类型又相同，全部输入太麻烦，我们可以在中间加了个横线
```
console.log(/[a-z]/.test('1111'));
console.log(/[A-Z]/.test('aa'));
```

5. 组合类
用中括号匹配不同类型的单个字符。
`console.log(/[a-m1-5]/.test("b"))//true`


#正则边界
^ 会匹配行或者字符串的起始位置
注：^在[]中才表示非！这里表示开始
$ 会匹配行或字符串的结尾位置
^$在一起 表示必须是这个（精确匹配）
```
// 边界可以精确说明要什么
console.log(/lily/.test("lilyname")); // true
console.log(/^lily$/.test("lily"));  // true
console.log(/^lily$/.test("ly"));   // false
```
`console.log(/^andy$/.test("andy"));  // true`
这个的最终意思就是说，必须是 andy 这四个字母
