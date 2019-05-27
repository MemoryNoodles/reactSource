### react官网高级指南的api
1、React.lazy:目前仅支持默认导出
React.lazy和Suspense尚不可用于服务器端渲染。如果要在服务器渲染的应用程序中进行代码拆分，我们建议使用 Loadable Components或者使用react-loadble,也就是说暂时线上业务可能用不了
示列：
```bash
import loadable from '@loadable/component'

const OtherComponent = loadable(() => import('./OtherComponent'))

function MyComponent() {
  return (
    <div>
      <OtherComponent />
    </div>
  )
}
```

2、Suspense 
加载提示符
```bash
// This component is loaded dynamically
const OtherComponent = React.lazy(() => import('./OtherComponent'));

function MyComponent() {
  return (
    // Displays <Spinner> until OtherComponent loads
    <React.Suspense fallback={<Spinner />}>
      <div>
        <OtherComponent />
      </div>
    </React.Suspense>
  );
}
```