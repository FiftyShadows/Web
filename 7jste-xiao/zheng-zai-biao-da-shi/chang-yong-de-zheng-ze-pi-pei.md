##获取中文字符

```
function GetChinese(strValue) {
  if (strValue != null && strValue != "") {
    var reg = /[\u4e00-\u9fa5，。？；]/g;
    strValue = strValue.match(reg).join("");
    //去掉指定字符
    strValue = strValue.replace(/\u67e5\u770b\u77e5\u4e4e\u8ba8\u8bba/, '。');
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

- exec方法：通过对指定的字符串进行一次匹配检测，获取字符串中的第一个与正则表达式的内容，并且将匹配的内容和子匹配的结果存放在返回数组中




##()的作用

- 分组

```
var regex = /(ab)+/g;
var string = "ababa abbb ababab";
console.log( string.match(regex) ); 
// => ["abab", "ab", "ababab"]
```

- 分支结构，而在多选分支结构(p1|p2)中，此处括号的作用也是不言而喻的，提供了子表达式的所有可能

- 提取数据

- 替换

```
//1
var regex = /(\d{4})-(\d{2})-(\d{2})/;
var string = "2017-06-12";
var result = string.replace(regex, "$2/$3/$1");
console.log(result); 
// => "06/12/2017"


//2
var regex = /(\d{4})-(\d{2})-(\d{2})/;
var string = "2017-06-12";

regex.test(string); // 正则操作即可，例如
//regex.exec(string);
//string.match(regex);

console.log(RegExp.$1); // "2017"
console.log(RegExp.$2); // "06"
console.log(RegExp.$3); // "12"


//3
var regex = /(\d{4})-(\d{2})-(\d{2})/;
var string = "2017-06-12";
var result = string.replace(regex, function() {
	return RegExp.$2 + "/" + RegExp.$3 + "/" + RegExp.$1;
});
console.log(result); 
// => "06/12/2017"



//4
var regex = /\d{4}(-|\/|\.)\d{2}\1\d{2}/;
var string1 = "2017-06-12";
var string2 = "2017/06/12";
var string3 = "2017.06.12";
var string4 = "2016-06/12";
console.log( regex.test(string1) ); // true
console.log( regex.test(string2) ); // true
console.log( regex.test(string3) ); // true
console.log( regex.test(string4) ); // false
//注意里面的\1，表示的引用之前的那个分组(-|\/|\.)。不管它匹配到什么（比如-），\1都匹配那个同样的具体某个字符
//我们知道了\1的含义后，那么\2和\3的概念也就理解了，即分别指代第二个和第三个分组。
```

- 括号嵌套怎么办？以左括号（开括号）为准

```
var regex = /^((\d)(\d(\d)))\1\2\3\4$/;
var string = "1231231233";
console.log( regex.test(string) ); // true
console.log( RegExp.$1 ); // 123
console.log( RegExp.$2 ); // 1
console.log( RegExp.$3 ); // 23
console.log( RegExp.$4 ); // 3
```

- \10是表示第10个分组

```
var regex = /(1)(2)(3)(4)(5)(6)(7)(8)(9)(#) \10+/;
var string = "123456789# ######"
console.log( regex.test(string) );
// => true
```

- 引用不存在的分组会怎样？引用了不存在的分组时，此时正则不会报错，只是匹配反向引用的字符本身。例如\2，就匹配”\2”。注意”\2”表示对”2”进行了转意。

- 非捕获分组：如果只想要括号最原始的功能，但不会引用它，即，既不在API里引用，也不在正则里反向引用。此时可以使用非捕获分组(?:p)

- trim方法模拟

```
function trim(str) {
	return str.replace(/^\s+|\s+$/g, '');
}
console.log( trim("  foobar   ") ); 
// => "foobar"


function trim(str) {
	return str.replace(/^\s*(.*?)\s*$/g, "$1");
}
console.log( trim("  foobar   ") ); 
// => "foobar"
```

- 将每个单词的首字母转换为大写

```
function titleize(str) {
	return str.toLowerCase().replace(/(?:^|\s)\w/g, function(c) {
		return c.toUpperCase();
	});
}
console.log( titleize('my name is epeli') ); 
// => "My Name Is Epeli"
```

- 驼峰化

```
function camelize(str) {
	return str.replace(/[-_\s]+(.)?/g, function(match, c) {
		return c ? c.toUpperCase() : '';
	});
}
console.log( camelize('-moz-transform') ); 
// => "MozTransform"
```

- 中划线化

```
function dasherize(str) {
	return str.replace(/([A-Z])/g, '-$1').replace(/[-_\s]+/g, '-').toLowerCase();
}
console.log( dasherize('MozTransform') ); 
// => "-moz-transform"
```

- html转义和反转义

```
// 将HTML特殊字符转换成等值的实体
function escapeHTML(str) {
	var escapeChars = {
	  '¢' : 'cent',
	  '£' : 'pound',
	  '¥' : 'yen',
	  '€': 'euro',
	  '©' :'copy',
	  '®' : 'reg',
	  '<' : 'lt',
	  '>' : 'gt',
	  '"' : 'quot',
	  '&' : 'amp',
	  '\'' : '#39'
	};
	return str.replace(new RegExp('[' + Object.keys(escapeChars).join('') +']', 'g'), function(match) {
		return '&' + escapeChars[match] + ';';
	});
}
console.log( escapeHTML('<div>Blah blah blah</div>') );
// => "&lt;div&gt;Blah blah blah&lt;/div&gt";


// 实体字符转换为等值的HTML。
function unescapeHTML(str) {
	var htmlEntities = {
	  nbsp: ' ',
	  cent: '¢',
	  pound: '£',
	  yen: '¥',
	  euro: '€',
	  copy: '©',
	  reg: '®',
	  lt: '<',
	  gt: '>',
	  quot: '"',
	  amp: '&',
	  apos: '\''
	};
	return str.replace(/\&([^;]+);/g, function(match, key) {
		if (key in htmlEntities) {
			return htmlEntities[key];
		}
		return match;
	});
}
console.log( unescapeHTML('&lt;div&gt;Blah blah blah&lt;/div&gt;') );
// => "<div>Blah blah blah</div>"
```

- 匹配成对标签

```
var regex = /<([^>]+)>[\d\D]*<\/\1>/;
var string1 = "<title>regular expression</title>";
var string2 = "<p>laoyao bye bye</p>";
var string3 = "<title>wrong!</p>";
console.log( regex.test(string1) ); // true
console.log( regex.test(string2) ); // true
console.log( regex.test(string3) ); // false
```



##(?:)不捕获里面的内容(?=n)匹配任何其后紧接指定字符串n的字符串，不捕获，不使用反向引用

```js
(?!_)　　不能以_开头

(?!.*?_$)　　不能以_结尾
```

