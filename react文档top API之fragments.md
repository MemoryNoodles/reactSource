### 用法
其实就是不想嵌套多层时，的一个使用，除了这个还可以用数组
```bash
render() {
  return (
    <React.Fragment>
      <ChildA />
      <ChildB />
      <ChildC />
    </React.Fragment>
  );
}
```
```bash
render() {
  return (
    [ 
      <ChildA />,
      <ChildB />,
      <ChildC />
      ]
  );
}
```

还有一个不太支持的用法，知道一下就行了
```bash
render() {
  return (
   <>
      <ChildA />
      <ChildB />
      <ChildC />
    </>
  );
}
```
