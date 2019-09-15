# IDE Set Up

### Prettier Setup

We will configure Prettier to format our code based on our ESLint rules.

First we need to install [[prettier-eslint.| https://www.npmjs.com/package/prettier-eslint]]

We want VS Code to format our code using Prettier after saving a file.

Press CMD + , if you’re on a Mac to open your VS Code Workspace Settings then add the following:

```
  // Prettier Code Format
  "editor.formatOnSave": true,
  "prettier.singleQuote": true,
  "prettier.trailingComma": "all"
  "prettier.printWidth": 80,
  "prettier.eslintIntegration": true

  // if js
  "javascript.format.enable": false,
```

### GitLens

- supercharges the built-in Visual Studio Code Git capabilities. It helps you to visualize code authorship at a glance via Git blame annotations and code lens, seamlessly navigate and explore the history of a file or branch, gain valuable insights via powerful comparison commands, and so much more.
  [[download here | https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens ]]

### Code Metrics - Visual Studio Code Extension

Computes complexity in TypeScript / JavaScript files. [[download here | https://marketplace.visualstudio.com/items?itemName=kisstkondoros.vscode-codemetrics]]
