##知识点

- 页面加载过程

- 性能优化

- 安全性



##题目

- 从输入url到得到html的详细过程

- window.onload和DOMContentLoaded的区别




##知识点

- 加载资源的形式

    - 输入url（或跳转页面）加载html
    
    - 加载html中的静态资源(css，js，图片，视频，字体文件)


- 加载一个资源的过程

    - 浏览器根据DNS服务器得到域名的IP地址
    
    - 向这个IP的机器发送http请求
    
    - 浏览器收到、处理并返回http请求
    
    - 浏览器得到返回内容


- 浏览器渲染页面的过程

    - 根据html结构生成DOM Tree
    
    - 根据CSS生成CSSOM
    
    - 将DOM和CSSOM整合形成RenderTree
    
    - 根据RenderTree开始渲染和展示
    
    - 遇到`<script>`时，会执行并阻塞渲染






##思考

- 为何要把js放到body最下面

    - 不会阻塞，性能更好
    
    - 方便获取DOM的标签























