# @cl/standard-stylelint

## 功能

- 用来格式化css文件，在less与scss中都可以使用

## 使用方式

- 安装依赖
- 项目根目录添加文件`.stylelintrc.js`
- 添加`rules`配置，可以覆盖默认规则

```javascript
// 安装依赖
yarn install @cl/standard-stylelint -D
```

```javascript
// 创建配置文件
mkdir .stylelintrc.js
cd .stylelintrc.js
```

```javascript
// .stylelintrc.js
const { getStyleLint } = require('@cl/standard-stylelint')

module.exports = {
  ...getStyleLint({
    rules: {
      ...
    }
  })
}
```

```javascript
// 默认配置
exports.getStyleLint = (options = {}) => {
  const rules = options.rules || {}
  return {
    extends: [
      'stylelint-config-standard',
      'stylelint-config-rational-order',
      'stylelint-config-prettier'
    ],
    plugins: [
      'stylelint-order',
      'stylelint-declaration-block-no-ignored-properties'
    ],
    rules: {
      'comment-empty-line-before': null,
      'function-name-case': [
        'lower',
        {
          'ignoreFunctions': [
            '/colorPalette/'
          ]
        }
      ],
      'no-invalid-double-slash-comments': null,
      'no-descending-specificity': null,
      'declaration-empty-line-before': null,
      ...rules
    }
  }
}
```
