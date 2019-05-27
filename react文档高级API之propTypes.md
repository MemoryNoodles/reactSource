### 用法
```bash
import PropTypes from 'prop-types';
class MyTag extends React.Component {
    static propTypes = {
        checked: PropTypes.bool,
        disabled: PropTypes.bool,
        tag:PropTypes.object,
        value:PropTypes.oneOfType([
            PropTypes.string,
            PropTypes.number
        ]),
        onChange:PropTypes.func,
    };
    static defaultProps = {
        checked:false,
        disabled:false,
        tag:{},
        value:"",
        onChange:(value)=>{}
    };
}
```

类型验证详细请参考https://react.docschina.org/docs/typechecking-with-proptypes.html；不过项目中一般使用Flow 和 TypeScript，因为他们可以添加自动完成功能来改善开发人员的工作流程