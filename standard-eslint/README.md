# @cl/standard-eslint

## 功能

- 格式化代码，采用`standard`风格
- 支持typescript与jsx，通过`useTs`参数区分，默认jsx

## 使用方式

- 安装依赖
- 项目根目录下创建配置文件`.eslintrc.js`与`.eslintignore`
- 代码通过typescript编写时，设置`useTs`为true
- `ignorePatterns`为需要忽略的文件
- 添加`rules`配置，可以覆盖默认规则

```javascript
// 安装依赖
yarn install @cl/standard-eslint -D
```

```javascript
// 创建配置文件
mkdir .eslintrc.js
mkdir .eslintignore
cd .eslintrc.js
```

```javascript
// .eslintrc.js
const { getEslint } = require('@cl/standard-eslint')

module.exports = {
  ...getEslint({
    ignorePatterns: ['.dll', 'build', '.temp'],
    // 默认false
    useTs: false,
    rules: {
      ...
    }
  })
}
```

```javascript
// .eslintignore
dist
build
config
scripts
node_modules
public
.babelrc
package.json
```

```javascript
// 默认配置
{
  extends: [
    'eslint:recommended',
    'plugin:prettier/recommended',
    'plugin:react/recommended',
  ],
  parser: '@babel/eslint-parser',
  parserOptions: {
    ecmaVersion: 2020,
    sourceType: 'module',
    ecmaFeatures: { legacyDecorators: true, jsx: true },
  },
  rules: {
    'no-const-assign': 'error',
    'react/prop-types': 0
  },
  env: {
    browser: true,
    node: true,
    es6: true,
    jest: true
  },
  plugins: ['react', 'prettier'],
  settings: {
    react: {
      version: 'detect', // Tells eslint-plugin-react to automatically detect the version of React to use
    },
    'import/resolver': {
      node: {
        extensions: ['.js', '.jsx', '.ts', '.tsx'],
        paths: ['./src'],
      },
    },
  },
  ignorePatterns: ['node_modules'],
}
```
