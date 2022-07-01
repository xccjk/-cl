# @cl/standard-commitlint

## 功能

- 用来检测commit提交是否规范
- 通过gitlib hook钩子在提交代码时效验代码格式

## 使用方式

- 安装依赖
- 项目根目录下创建配置文件`.commitlintrc.js`
- 添加`rules`配置，可以覆盖默认规则(尽量不要改变默认规则，保证规范统一。老项目升级时才使用，避免大量改动)

```javascript
// 安装
yarn install @cl/standard-commitlint -D
```

```javascript
// 创建配置文件
mkdir .commitlintrc.js
cd .commitlintrc.js
```

```javascript
// .commitlintrc.js
const { getCommitLint } = require('@cl/standard-commitlint')

module.exports = {
  ...getCommitLint()
}
```

```javascript
// 覆盖默认配置
const { getCommitLint } = require('@cl/standard-commitlint')

module.exports = {
  ...getCommitLint({ 
    rules: {
      ...
    }
  }),
}
```

```javascript
// 默认配置
{
  extends: [
    '@commitlint/config-conventional'
  ],
  rules: {
    'body-leading-blank': [1, 'always'],
    'body-max-line-length': [2, 'always', 100],
    'footer-leading-blank': [1, 'always'],
    'footer-max-line-length': [2, 'always', 100],
    'header-max-length': [2, 'always', 100],
    'scope-case': [2, 'always', 'lower-case'],
    'subject-case': [
      2,
      'never',
      ['sentence-case', 'start-case', 'pascal-case', 'upper-case'],
    ],
    'subject-empty': [2, 'never'],
    'subject-full-stop': [2, 'never', '.'],
    'type-case': [2, 'always', 'lower-case'],
    'type-empty': [2, 'never'],
    'type-enum': [
      2,
      'always',
      [
        'build',
        'chore',
        'ci',
        'docs',
        'feat',
        'feature',
        'fix',
        'bugfix',
        'perf',
        'refactor',
        'revert',
        'style',
        'test',
      ],
    ]
  }
}
```

## 字段含义

- build：主要目的是修改项目构建系统(例如 glup，webpack，rollup 的配置等)的提交
- ci：主要目的是修改项目继续集成流程(例如 Travis，Jenkins，GitLab CI，Circle等)的提交
- docs：文档更新
- feat：新增功能
- feature：新增功能
- fix：bug 修复
- bugfix：bug 修复
- perf：性能优化
- refactor：重构代码(既没有新增功能，也没有修复 bug)
- style：不影响程序逻辑的代码修改(修改空白字符，补全缺失的分号等)
- test：新增测试用例或是更新现有测试
- revert：回滚某个更早之前的提交
- chore：不属于以上类型的其他类型(日常事务)
