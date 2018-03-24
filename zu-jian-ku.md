china-division    中国省市区

g2    g2-react    数据可视化

Immutable    数据不可变

JSZip    js压缩

lie    promise垫片

moment    日期处理类库

prop-types    对组件的props中的变量进行类型检测;http://www.css88.com/react/docs/typechecking-with-proptypes.html

qrcode.react    二维码生成

qs    字符串转对象和对象转字符串

React DnD    react高阶组件，拖拽

react-color    选取颜色

react-draggable    元素可拖拽

react-media    css媒体查询组件

react-responsive    响应式设计的媒体查询模块

react-virtualized    有效的渲染大的列表和表格数据

recharts    图表库

reqwest    发送请求

rc-animate

rc-banner-anim

rc-form

rc-queue-anim

rc-scroll-anim

rc-tween-one




##单例模式

- 基于es6实现单例模式

```
export class Director{
    constructor(){
        console.info('构造器初始化');
    }
    static getInstance(){
        if(!Director.instance){
            Director.instance = new Director;
        }
        return Director.instance;
    }
}
```





##drawImage

this.ctx.drawImage = {
    image对象，
    image的x起始位置，
    image的y起始位置，
    image.width,
    image.height,
    放置在画布的位置0,
    0，
    image.width,
    image.height
};





##精灵基类，负责初始化精灵加载的资源和大小以及位置












