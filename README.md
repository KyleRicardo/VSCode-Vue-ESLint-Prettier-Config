# VSCode-Vue-ESLint-Prettier-Config

I was almost driven mad in the latest 2 months just because of the conflict among these vscode extensions - vetur, eslint and prettier. I have to admit that these extensions are all fantastic, but get them to cooperate seemed to be the *Mission: Impossible*. Finally I made up my mind to stick to it and I found a workaround. Maybe it is not the best, but at least it works.

### Extensions you need

- Vetur - for vue snippets & syntax highlighting & format
- ESLint - for linting
- Prettier - for general code formatting
- Manta's Stylus Supremacy - for formatting stylus

### vue-cli config option

When choosing `Pick a linter/formatter config`， it is recommended that we use the `ESLint + Standard config` option, this can save us a lot of time. The reason why we don't choose other options is `Airbnb` often goes with React.js, not Vue.js, and `Prettier` will make things very complex.

In a word, choosing **STANDARD** config will make your life much easier.

### vscode workspace settings.json

File located at `.vscode/settings.json`

```json
{
  "editor.formatOnSave": true,
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
  },
  "stylusSupremacy.insertColons": false,
  "stylusSupremacy.insertSemicolons": false,
  "stylusSupremacy.insertBraces": false,
  "stylusSupremacy.insertNewLineAroundImports": false,
  "stylusSupremacy.insertNewLineAroundBlocks": false,
  "vetur.format.defaultFormatter.html": "js-beautify-html",
  "vetur.format.defaultFormatter.js": "none",
  "vetur.format.defaultFormatter.ts": "none",
  "vetur.format.defaultFormatterOptions": {
    "js-beautify-html": {
      "wrap_attributes": "force-aligned",
      "wrap_line_length": 100
    },
    "prettyhtml": {
      "printWidth": 100,
      "singleQuote": false,
      "wrapAttributes": false,
      "sortAttributes": false
    }
  },
  "prettier.disableLanguages": ["vue"]
}

```

### .prettierrc

```json
{
  "printWidth": 100,
  "singleQuote": true, 
  "semi": false 
}
```

### .eslintrc.js

```javascript
module.exports = {
  root: true,
  env: {
    node: true
  },
  extends: ['plugin:vue/strongly-recommended', '@vue/standard'],
  rules: {
    'no-console': process.env.NODE_ENV === 'production' ? 'error' : 'off',
    'no-debugger': process.env.NODE_ENV === 'production' ? 'error' : 'off',
    'generator-star-spacing': 'off',
    'no-mixed-operators': 0,
    'vue/max-attributes-per-line': [
      2,
      {
        singleline: 3,
        multiline: {
          max: 1,
          allowFirstLine: true
        }
      }
    ],
    'vue/attribute-hyphenation': 0,
    'vue/html-self-closing': 0,
    'vue/component-name-in-template-casing': 0,
    'vue/html-closing-bracket-spacing': 0,
    'vue/singleline-html-element-content-newline': 0,
    'vue/no-unused-components': 0,
    'vue/multiline-html-element-content-newline': 0,
    'vue/no-use-v-if-with-v-for': 0,
    'vue/html-closing-bracket-newline': 0,
    'vue/no-parsing-error': 0,
    'no-tabs': 0,
    quotes: [
      2,
      'single',
      {
        avoidEscape: true,
        allowTemplateLiterals: true
      }
    ],
    semi: [
      2,
      'never',
      {
        beforeStatementContinuationChars: 'never'
      }
    ],
    'no-delete-var': 2,
    'prefer-const': [
      2,
      {
        ignoreReadBeforeAssign: false
      }
    ]
  },
  parserOptions: {
    parser: 'babel-eslint'
  }
}

```

