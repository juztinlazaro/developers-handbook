# ESLINT SET UP

```
{
  "parser": "babel-eslint",
  "env": {
    "es6": true,
    "browser": true,
    "node": true,
    "jest": true
  },
  "extends": "airbnb",
  "rules": {
    "semi": "off",
    "space-before-function-paren": "error",
    "indent": "error",
    "react/jsx-indent": "error",
    "jsx-quotes": "error",
    "react/prop-types": "error",
    "max-len": [
      "error",
      80,
      {
        "ignoreComments": true,
        "ignoreTrailingComments": true,
        "ignoreUrls": true,
        "ignoreStrings": true,
        "ignoreTemplateLiterals": true
      }
    ],
    "jsx-a11y/no-static-element-interactions": "error",
    "eol-last": "error",
    "import/no-extraneous-dependencies": "warn",
    "no-trailing-spaces": "error",
    "no-multi-spaces": "error",
    "space-in-parens": "error",
    "react/self-closing-comp": "error",
    "object-curly-spacing": "error",
    "key-spacing": "error",
    "comma-dangle": "error",
    "no-unused-vars": "error",
    "prefer-template": "error",
    "react/jsx-closing-bracket-location": "error",
    "no-confusing-arrow": "error",
    "no-nested-ternary": "error",
    "dot-notation": "error",
    "radix": "error",
    "react/jsx-indent-props": "error",
    "arrow-spacing": "error",
    "react/jsx-space-before-closing": "error",
    "arrow-parens": ["error", "as-needed"],
    "react/jsx-tag-spacing": "error",
    "import/prefer-default-export": "error",
    "react/prefer-stateless-function": "error",
    "no-useless-constructor": "error",
    "react/no-array-index-key": "error",
    "react/no-unused-prop-types": "error",
    "react/require-default-props": "error",
    "import/no-named-as-default": "error",
    "import/no-named-as-default-member": "error",
    "object-shorthand": "error",
    "eqeqeq": "error",
    "quotes": "error",
    "comma-spacing": "error",
    "react/jsx-first-prop-new-line": "error",
    "padded-blocks": "error",
    "prefer-const": "warn",
    "curly": "error",
    "no-tabs": "error",
    "react/jsx-no-target-blank": "error",
    "no-else-return": "error",
    "react/jsx-no-undef": "error",
    "jsx-a11y/href-no-hash": "error",
    "react/forbid-prop-types": "error",
    "space-infix-ops": "error",
    "no-var": "error",
    "no-case-declarations": "error",
    "block-scoped-var": "error",
    "no-bitwise": "error",
    "vars-on-top": "error",
    "no-shadow": "error",
    "import/first": "error",
    "arrow-body-style": "error",
    "react/no-find-dom-node": "off",
    "react/no-string-refs": "off",
    "consistent-return": "error",
    "spaced-comment": "error",
    "no-underscore-dangle": "off",
    "react/sort-comp": "error",
    "no-return-assign": "error",
    "react/no-unescaped-entities": "error",
    "no-unused-expressions": "error",
    "no-sequences": "error",
    "no-param-reassign": "error",
    "space-before-blocks": "error",
    "no-use-before-define": "error",
    "react/no-multi-comp": "error",
    "global-require": "warn",
    "import/newline-after-import": "error",
    "react/jsx-wrap-multilines": "error",
    "react/no-did-mount-set-state": "error",
    "react/jsx-curly-spacing": "error",
    "keyword-spacing": "error",
    "jsx-a11y/tabindex-no-positive": "error",
    "no-useless-escape": "error",
    "prefer-arrow-callback": "error",
    "block-spacing": "error",
    "no-undef": "off",
    "no-multiple-empty-lines": "error",
    "no-redeclare": "error",
    "array-callback-return": "error",
    "camelcase": "error",
    "jsx-a11y/img-redundant-alt": "error",
    "jsx-a11y/img-has-alt": "error",
    "brace-style": "error",
    "object-property-newline": "error",
    "jsx-a11y/anchor-has-content": "error",
    "no-plusplus": ["off", { "allowForLoopAfterthoughts": true }],
    "react/no-render-return-value": "error",
    "react/jsx-filename-extension": [
      1,
      {
        "extensions": [".js", ".jsx"]
      }
    ],
    "no-unneeded-ternary": "error",
    "react/jsx-no-bind": "error",
    "no-extra-semi": "error",
    "jsx-a11y/label-has-for": "error",
    "react/no-unknown-property": "error",
    "react/jsx-boolean-value": "error",
    "quote-props": "error",
    "no-undef-init": "error",
    "no-debugger": "warn",
    "no-restricted-syntax": "error",
    "no-lonely-if": "error",
    "comma-style": "error",
    "no-mixed-spaces-and-tabs": "error",
    "default-case": "error",
    "space-unary-ops": "error",
    "wrap-iife": "error",
    "operator-assignment": "error",
    "no-duplicate-case": "error",
    "no-prototype-builtins": 0,
    "class-methods-use-this": "error",
    "semi-spacing": "error",
    "import/no-unresolved": "warn",
    "linebreak-style": 0,
    "func-style": ["error", "declaration", { "allowArrowFunctions": true }],
    "react/no-danger": "off",
    "import/extensions": "warn"
  },
  "globals": {
    "window": true,
    "sessionStorage": true,
    "localStorage": true,
    "document": true,
    "Headers": true
  }
}

```