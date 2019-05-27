### 用法
```bash
React.cloneElement(
  element,
  [props],
  [...children]
)
```
以 element 元素为样板克隆并返回新的 React 元素。返回元素的 props 是将新的 props 与原始元素的 props 浅层合并后的结果。新的子元素将取代现有的子元素，而来自原始元素的 key 和 ref 将被保留。引入此 API 是为了替换已弃用的 React.addons.cloneWithProps()。