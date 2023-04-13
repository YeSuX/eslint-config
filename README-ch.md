# @suxiong/config

- 📝 使用单引号，而不是分号。
- 🛠️ 自动修复格式（独立使用，**不需要** Prettier）。
- 🎨 TypeScript 和 Vue 开箱即用。
- 🔍 也可用于 JSON、YAML 和 Markdown。
- 📥 导入被排序，允许悬空逗号。
- 🌟 包含合理的默认值和最佳实践，只需一行配置。
- 📌 最小化以提高可读性，稳定以进行差异比较。

## 使用

### 安装

```
pnpm add -D eslint @suxiong/eslint-config

```

### 配置 `.eslintrc`

```
{
  "extends": "@suxiong"
}

```

> 通常情况下，您不需要`.eslintignore`，因为它已经由预设提供。
> 

### 添加 package.json

例如:

```
{
  "scripts": {
    "lint": "eslint .",
    "lint:fix": "eslint . --fix"
  }
}

```

### 配置VS Code自动格式化

安装 [VS Code ESLint 插件](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint) 并且创建 `.vscode/settings.json`

```
{
  "prettier.enable": false,
  "editor.formatOnSave": false,
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
  }
}

```

### TypeScript 注意规则

当项目根目录中存在 `tsconfig.eslint.json` 时，类型校验规则将被启用，这将为您的项目引入一些更严格的规则。如果您想在项目根目录中没有 `tsconfig.eslint.json` 的情况下启用它，您可以通过修改 `ESLINT_TSCONFIG` 环境变量来更改 tsconfig 的名称。

```
// .eslintrc.js
process.env.ESLINT_TSCONFIG = 'tsconfig.json'

module.exports = {
  extends: '@suxiong'
}

```

### Lint Staged

如果您想在每次提交之前应用 lint 和自动修复，可以将以下内容添加到您的 `package.json` 中：

```
{
  "simple-git-hooks": {
    "pre-commit": "pnpm lint-staged"
  },
  "lint-staged": {
    "*": "eslint --fix"
  }
}

```

和

```
npm i -D lint-staged simple-git-hooks

```

## FAQ

### Prettier?

[Why I don't use Prettier](https://antfu.me/posts/why-not-prettier)

### 如何进行 CSS 代码检查？

此配置文件不会检查 CSS 代码。个人建议使用 [UnoCSS](https://github.com/unocss/unocss) 或 [tailwindcss](https://github.com/tailwindlabs/tailwindcss) 来代替手写 CSS。如果您仍然更喜欢 CSS，可以使用 [stylelint](https://stylelint.io/) 来进行 CSS 代码检查。

### 我更喜欢 XXX...

当然，您可以在您的 `.eslintrc` 文件中覆盖这些规则。

<!-- eslint-skip -->

```
{
  "extends": "@antfu",
  "rules": {
    // your rules...
  }
}

```

或者您可以随时 Fork 这个仓库，然后自己制作。

## License

[MIT](notion://www.notion.so/suxiong/LICENSE) License © 2019-PRESENT [Suxiong](https://github.com/YeSuX)
