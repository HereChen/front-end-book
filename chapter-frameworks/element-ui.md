# Element

<https://github.com/ElemeFE/element>

## 组件使用

### 自定义表单校验

```javascript
export default {
  data: function () {
    var checkVars = function (rule, value, callback) {
      if (!value) {
        callback(new Error('不能为空'));
      } else {
        callback();
      }
    };
    return {
      rules: {
        vars: [{
          required: true,
          trigger: 'change',
          validator: checkVars
        }]
      }
    }
  }
}
```

## 兼容性

### IE 图标不显示

可用文字替代伪元素中的内容.
