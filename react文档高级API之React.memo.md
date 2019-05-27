### 什么是React.memo()
React.memo是一个高阶组件，类似于React.PureComponent，不同于React.memo是function组件，React.PureComponent是class组件。

### PureComponent
```bash
class Child extends React.PureComponent {
    render(){
        console.log('I am rendering');
        return (
            <div>I am update every {this.props.seconds} seconds</div>
        )
    }
}
```
现在新出了一个React.memo()可以满足创建纯函数而不是一个类的需求

### React.memo()
```bash
function Child({seconds}){
    console.log('I am rendering');
    return (
        <div>I am update every {seconds} seconds</div>
    )
};
export default React.memo(Child)
```
React.memo()可接受2个参数，第一个参数为纯函数的组件，第二个参数用于对比props控制是否刷新，与shouldComponentUpdate()功能类似。

```bash
import React from "react";

function Child({seconds}){
    console.log('I am rendering');
    return (
        <div>I am update every {seconds} seconds</div>
    )
};

function areEqual(prevProps, nextProps) {
    if(prevProps.seconds===nextProps.seconds){
        return true
    }else {
        return false
    }

}
export default React.memo(Child,areEqual)
```

