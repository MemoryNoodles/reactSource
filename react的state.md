### state
state一般在constructor里设置，当然也可以作为组件的静态属性出现，比如
```bash
static state={
   
}
```

**setState()**
```bash
setState(updater, [callback])
```
callback这个回调函数执行的时间是，render渲染之后。    
常规用法1
```bash
this.setState({quantity: 2})
```
常规用法2
```bash
this.setState((state, props) => {
  return {counter: state.counter + props.step};
});
```

**forceUpdate**

默认情况下，当组件的 state 或 props 改变时，组件将重新渲染。 如果你的 render() 方法依赖于一些其他数据，你可以告诉 React 组件需要通过调用 forceUpdate() 重新渲染。

调用 forceUpdate() 会导致组件跳过 shouldComponentUpdate() ，直接调用 render()。 这将触发子组件的正常生命周期方法，包括每个子组件的 shouldComponentUpdate() 方法。

forceUpdate就是重新render。有些变量不在state上，但是你又想达到这个变量更新的时候，刷新render；或者state里的某个变量层次太深，更新的时候没有自动触发render。这些时候都可以手动调用forceUpdate自动触发render
```bash
class Sub extends React.Component{
    construcotor(){
        super();
        this.name = "yema";
    }
    refChangeName(name){
        this.name = name;
        this.forceUpdate(); 
    }
    render(){
        return (<div>{this.name}</div>);
    }
}
```
这个方法也可以有回调forceUpdate(callback)