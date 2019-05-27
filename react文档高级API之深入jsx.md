### 组件的真像

```bash
<MyButton color="blue" shadowSize={2}>
  Click Me
</MyButton>
```
编译为
```bash
React.createElement(
  MyButton,
  {color: 'blue', shadowSize: 2},
  'Click Me'
)
```