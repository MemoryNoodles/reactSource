### isValidElement
```bash
React.isValidElement(object)
```
验证对象是否为 React 元素，返回值为 true 或 false。

### React.Children.map
```bash
React.Children.map(children, (child, i) => {
  // Ignore the first child
  if (i < 1) return
  return child
})
```
可以对他的child做一些操作
