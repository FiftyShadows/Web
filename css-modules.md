# CSS模块化

原文: [https://www.w3cplus.com/react/css-modules-for-react.html](https://www.w3cplus.com/react/css-modules-for-react.html) © w3cplus.com

## CSS 模块化的解决方案，主要有两类：

* 彻底抛弃 CSS，使用 JS 或 JSON 来写样式。Radium，jsxstyle，react-style 属于这一类。
  * 优点是能给 CSS 提供 JS 同样强大的模块化能力
  * 缺点是不能利用成熟的 CSS 预处理器（或后处理器） Sass/Less/PostCSS，:hover 和 :active 伪类处理起来复杂。
* 另一类是依旧使用 CSS，但使用 JS 来管理样式依赖，代表是 CSS Modules。
  * CSS Modules 内部通过 ICSS 来解决样式导入和导出这两个问题。分别对应 :import 和 :export 两个新增的伪类

## CSS Modules 实现了以下几点

* 所有样式都是 local 的，解决了命名冲突和全局污染问题
* class 名生成规则配置灵活，可以此来压缩 class 名
* 只需引用组件的 JS 就能搞定组件所有的 JS 和 CSS
* 依然是 CSS，几乎 0 学习成本

