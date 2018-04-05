##模板语法

- mustache语法： {{msg}}

- html赋值：v-html=""

- 绑定属性：v-bind:id=""

- 使用表达式：{{ok? 'YES': 'NO'}}

- 文本赋值：v-text=""

- 指令：v-if=""

- 过滤器：{{ message | capitalize}}和v-bind:id="rawld | formatid"




##class和style绑定

- 对象语法：v-bind:class="{active: isActive, 'text-danger': hasError}"

- 数组语法`<div v-bind:class="[activeClass, errorClass]"></div>`

- style绑定





##条件渲染

- v-if

- v-else

- v-else-if

- v-show

- v-cloak