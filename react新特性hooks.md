### useState
*出现这个钩子的动机是*
 1、在组件之间复用状态逻辑很难（除非你使用 render props 和 高阶组件）
 2、复杂组件变得难以理解
 3、难以理解的 class（this等不好理解， class不能很好的压缩）
```bash
import { useState } from 'react';
function ExampleWithManyStates() {
  // 声明多个状态变量！
  const [count, setCount] = useState(0);    
  const [age, setAge] = useState(42);
  const [fruit, setFruit] = useState('banana');
  const [todos, setTodos] = useState([{ text: 'Learn Hooks' }]);
  // ...
  return (
    <div>
      <p>You clicked {count} times</p>
      //两种用法              setCount(prevCount => prevCount + 1)}
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}
```

### 副作用钩子（Effect Hook）
与componentDidMount ，componentDidUpdate和 componentWillUnmount具有相同的用途
```bash
import { useState, useEffect } from 'react';

function Example() {
  const [count, setCount] = useState(0);

  // 类似于 componentDidMount 和 componentDidUpdate:
  useEffect(() => {
    // 使用浏览器API更新文档标题
    document.title = `You clicked ${count} times`;
  });
  // 可以多次使用
  useEffect(() => {
    // == componentDidMount 
    ChatAPI.subscribeToFriendStatus(props.friend.id, handleStatusChange);
    // 明确在这个 effect 之后如何清理它 ==  componentWillUnmount
    return function cleanup() {
      ChatAPI.unsubscribeFromFriendStatus(props.friend.id, handleStatusChange);
    };
  });
  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}
```
有了钩子，你可以在组件中按照代码块的相关性组织副作用，而不是基于生命周期方法强制进行切分。

### 钩子的使用规则
1、只能在顶层（函数内==没嵌套）调用钩子。不要在循环，控制流和嵌套的函数中调用钩子。
2、只能从React的函数式组件中调用钩子。不要在常规的JavaScript函数中调用钩子。（此外，你也可以在你的自定义钩子中调用钩子。我们马上就会讲到它。）


### 难点理解
**新旧数据比较**
```bash
componentDidUpdate(prevProps, prevState) {
  if (prevState.count !== this.state.count) {
    document.title = `You clicked ${this.state.count} times`;
  }
}
```
这个用useEffect怎么写啦
```bash
useEffect(() => {
  document.title = `You clicked ${count} times`;
}, [count]); 
```

**卸载**
```bash
  componentDidMount() {
    ChatAPI.subscribeToFriendStatus(
      this.props.friend.id,
      this.handleStatusChange
    );
  }

  componentWillUnmount() {
    ChatAPI.unsubscribeFromFriendStatus(
      this.props.friend.id,
      this.handleStatusChange
    );
  }
```
这个用useEffect怎么写,看下面简单的骚操作
```bash
useEffect(() => {
    ChatAPI.subscribeToFriendStatus(props.friend.id, handleStatusChange);
    return () => {
      ChatAPI.unsubscribeFromFriendStatus(props.friend.id, handleStatusChange);
    };
  });
```

### 其他的支持
如果你使用eslint的话，你可能要这样安装
```bash
npm install eslint-plugin-react-hooks@next
```
下面是配置
```
// Your ESLint configuration
{
  "plugins": [
    // ...
    "react-hooks"
  ],
  "rules": {
    // ...
    "react-hooks/rules-of-hooks": "error"
  }
}
```