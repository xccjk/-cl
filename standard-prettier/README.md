# @cl/standard-prettier

## 功能

- 用来美化代码，空格，换行，风格等
- https://prettier.io/docs/en/index.html

## 使用方式

- 安装依赖
- 项目根目录添加文件`.prettierrc.js`与`.prettierignore`
- 添加`rules`配置，可以覆盖默认规则

```javascript
// 安装依赖
yarn install @cl/standard-prettier -D
```

```javascript
// 创建配置文件
mkdir .prettierrc.js
mkdir .prettierignore
cd .prettierrc.js
```

```javascript
// .prettierrc.js
const { getPrettier } = require('@cl/standard-prettier')

module.exports = {
  ...getPrettier({
    options: {}
  })
}
```

```javascript
// .prettierignore
.dll
build/
dist/
/node_modules
.temp
node_modules
.vscode
```

```javascript
// 默认配置
exports.getPrettier = (options = {}) => {
  return {
    semi: false,
    printWidth: 140,
    tabWidth: 2,
    singleQuote: true,
    bracketSpacing: true,
    jsxBracketSameLine: false,
    useTabs: false,
    arrowParens: 'avoid',
    jsxSingleQuote: true,
    trailingComma: 'none',
    ...options
  }
}
```
