# React模仿大众点评

## Todo组件

```text
submitFn(value){
    const id = this.state.todos.length;
    this.setState({
        todos: this.state.todos.concat({
            id: id,
            text: value
        })
    });
};
deleteFn(id){
    let data = this.state.todos;
    this.setState({
        todos: data.filter(item => {
            if(item.id != id){
                return item
            }
        })
    });
}
```

## Input组件

```text
import React from 'react';
import PureRenderMixin from 'react-addons-pure-render-mixin';

class Input extends React.component {
    constructor(props, context){
        super(props, context);
        this.shouldComponentUpdate = PureRenderMixin.shouldComponentUpdate.bind(this);
        this.state = {
            value: ''
        };
    };
    render(){
        return (
            <input
                style={{width: '100%', height: '40px'}}
                value={this.state.value}
                onChange={this.changeHandler.bind(this)}
                onKeyUp={this.KeyUpHandler.bind(this)}
            />
        );
    };
    changeHandler(e) {
        this.setState({
            value: e.target.value
        });
    };
    KeyUpHandler(e) {
        const value = this.state.value;
        if(keyCode === 13 && value.trim()) {
            this.props.submitFn(value);
            this.setState({
                value: ''
            });
        }
    };
}

export default Input;
```

## List组件

```text
import React from 'react';
import PureRenderMixin from 'react-addons-pure-render-mixin';

class List extends React.component {
    constructor(props, context){
        super(props, context);
        this.shouldComponentUpdate = PureRenderMixin.shouldComponentUpdate.bind(this);
    };
    render() {
        const data = this.props.todos;
        return (
            <ul>
                {data.map((item, index) => {
                    return <li key={index} onClick={this.clickHandler.bind(this, item.id)}>{item.text}</li>
                })}
            </ul>
        );
    };
    clickHandler(id){
        this.props.deleteFn(id);
    };
}

export default List;
```

