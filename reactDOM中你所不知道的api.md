
### ReactDOM中你所不知道的API
**hydrate**
```bash
ReactDOM.hydrate()
```

和render方法相同，但它用于在 ReactDOMServer 渲染的容器中对 HTML 的内容进行 hydrate 操作。React 会尝试在已有标记上绑定事件监听器。


```bash
// using Express
import { renderToString } from "react-dom/server"
import MyPage from "./MyPage"
app.get("/", (req, res) => {
  res.write("<!DOCTYPE html><html><head><title>My Page</title></head><body>");
  res.write("<div id='content'>");  
  res.write(renderToString(<MyPage/>));
  res.write("</div></body></html>");
  res.end();
});
```
当您仅在客户端呈现内容时，使用render() 方法，如果你在服务端渲染结果之上再次渲染则使用hydrate()方法。因为React向后兼容，在React 16中，render()方法会继续可用于服务端渲染。但为了不出现警告信息你最好使用hydrate()方法来代替render():


**unmountComponentAtNode()**
```bash
ReactDOM.unmountComponentAtNode(container)
```
从 DOM 中卸载组件，会将其事件处理器（event handlers）和 state 一并清除。如果指定容器上没有对应已挂载的组件，这个函数什么也不会做。如果组件被移除将会返回 true，如果没有组件可被移除将会返回 false。

**findDOMNode()**
注意:
findDOMNode 是一个访问底层 DOM 节点的应急方案（escape hatch）。在大多数情况下，不推荐使用该方法，因为它会破坏组件的抽象结构。严格模式下该方法已弃用。

```bash
ReactDOM.findDOMNode(component)
```
如果组件已经被挂载到 DOM 上，此方法会返回浏览器中相应的原生 DOM 元素。此方法对于从 DOM 中读取值很有用，例如获取表单字段的值或者执行 DOM 检测（performing DOM measurements）。大多数情况下，你可以绑定一个 ref 到 DOM 节点上，可以完全避免使用 findDOMNode。

注意:

findDOMNode 只在已挂载的组件上可用（即，已经放置在 DOM 中的组件）。如果你尝试调用未挂载的组件（例如在一个还未创建的组件上调用 render() 中的 findDOMNode()）将会引发异常。

findDOMNode 不能用于函数组件。

**createPortal**
```bash
ReactDOM.createPortal(child, container)
```
ReactDOM.createPortal(child, container)：第一个参数（child）是任何可渲染的 React 子元素，例如一个元素，字符串或 片段(fragment)。第二个参数（container）则是一个 DOM 元素。感觉是一个操作DOM的API