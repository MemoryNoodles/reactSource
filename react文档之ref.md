### 何时使用 Refs
下面有一些正好使用 refs 的场景:

处理focus、文本选择或者媒体播放
触发强制动画
集成第三方DOM库
如果可以通过声明式实现，就尽量避免使用 refs 。


### forwardRef用法
ref.current 将指向button DOM节点。
```bash
const FancyButton = React.forwardRef((props, ref) => (
  <button ref={ref} className="FancyButton">
    {props.children}
  </button>
));

// You can now get a ref directly to the DOM button:
const ref = React.createRef();
<FancyButton ref={ref}>Click me!</FancyButton>;
```

### createRef用法
```bash
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.myRef = React.createRef();
  }
  render() {
    return <div ref={this.myRef} />;
    //or
    return <div ref={(node) => this.funRef = node} />
  }
}
```

