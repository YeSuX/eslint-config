# @suxiong/config

- 📝 Use single quotes, not semicolons.
- 🛠️ Automatically fix formatting (designed to be used standalone, **without** Prettier).
- 🎨 Designed to work with TypeScript and Vue out-of-the-box.
- 🔍 Linting also available for JSON, YAML, and Markdown.
- 📥 Imports are sorted and dangling commas are allowed.
- 🌟 Includes reasonable defaults and best practices, with only one line of configuration.
- 📌 Minimal for readability, stable for diffs.

## Usage

### Install

```
pnpm add -D eslint @suxiong/eslint-config

```

### Config `.eslintrc`

```
{
  "extends": "@suxiong"
}

```

> You don't need .eslintignore normally as it has been provided by the preset.
> 

### Add script for package.json

For example:

```
{
  "scripts": {
    "lint": "eslint .",
    "lint:fix": "eslint . --fix"
  }
}

```

### Config VS Code auto fix

Install [VS Code ESLint extension](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint) and create `.vscode/settings.json`

```
{
  "prettier.enable": false,
  "editor.formatOnSave": false,
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
  }
}

```

### TypeScript Aware Rules

Type aware rules are enabled when a `tsconfig.eslint.json` is found in the project root, which will introduce some stricter rules into your project. If you want to enable it while have no `tsconfig.eslint.json` in the project root, you can change tsconfig name by modifying `ESLINT_TSCONFIG` env.

```
// .eslintrc.js
process.env.ESLINT_TSCONFIG = 'tsconfig.json'

module.exports = {
  extends: '@suxiong'
}

```

### Lint Staged

If you want to apply lint and auto-fix before every commit, you can add the following to your `package.json`:

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

and then

```
npm i -D lint-staged simple-git-hooks

```

## FAQ

### Prettier?

[Why I don't use Prettier](https://antfu.me/posts/why-not-prettier)

### How to lint CSS?

This config does NOT lint CSS. I personally use [UnoCSS](https://github.com/unocss/unocss) or [tailwindcss](https://github.com/tailwindlabs/tailwindcss) so I don't write CSS. If you still prefer CSS, you can use [stylelint](https://stylelint.io/) for CSS linting.

### I prefer XXX...

Sure, you can override the rules in your `.eslintrc` file.

<!-- eslint-skip -->

```
{
  "extends": "@antfu",
  "rules": {
    // your rules...
  }
}

```

Or you can always fork this repo and make your own.

## License

[MIT](notion://www.notion.so/suxiong/LICENSE) License © 2019-PRESENT [Suxiong](https://github.com/YeSuX)
