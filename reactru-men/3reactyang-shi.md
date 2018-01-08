## 内联样式

* CSS命名规范： dialog\_\_confirm-button--highlight

* const styleHeaderComponent = {  
           header: {  
               backgroundColor: '\#000',  
               color: '\#fff',  
               paddingTop: '30px',  
               paddingBottom: '15px'  
           },

* 注意样式的驼峰写法

* style={styleHeaderComponent.header}

* 文件中引用css的形式

* 注意class需要更改成className

* 缺点是动画、伪类等不能





## 内联样式中的表达式

* paddingBottom: \(this.state.miniHeader\)? '3px' : '30px';





## CSS模块化

- "babel-plugin-react-html-attrs": "^2.0.0",    解决class的冲突，拷贝代码

- "style-loader": "^0.13.1",

- "css-loader": "0.25.0"































