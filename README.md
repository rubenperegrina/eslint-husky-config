# Installation 💻

```bash
  npm i --save-dev @angular-eslint/builder
  npm i --save-dev @angular-eslint/eslint-plugin
  npm i --save-dev @angular-eslint/eslint-plugin-template
  npm i --save-dev @angular-eslint/schematics
  npm i --save-dev @angular-eslint/template-parser
  npm i --save-dev @typescript-eslint/eslint-plugin
  npm i --save-dev @typescript-eslint/parser
  npm i --save-dev eslint
  npm i --save-dev eslint-config-airbnb-typescript
  npm i --save-dev eslint-plugin-import
  npm i --save-dev eslint-plugin-jsdoc
  npm i --save-dev eslint-plugin-n
  npm i --save-dev eslint-plugin-prefer-arrow
  npm i --save-dev eslint-plugin-promise
  npm i --save-dev husky
```

# husky pre-commit 🐺

```bash
#!/usr/bin/env sh
. "$(dirname -- "$0")/_/husky.sh"

npm run lint
```
# angular.json ❤

```json
"lint": {
  "builder": "@angular-eslint/builder:lint",
  "options": {
    "lintFilePatterns": [
      "src/**/*.ts",
      "src/**/*.html",
      "src/**/*.scss"
    ]
  }
}
```
# package.json 🌏

```json
  "scripts": {
    "lint": "ng lint --fix",
    "prepare": "husky install"
  },
```

# eslintrc.json ☑

```json
{
  "overrides": [
    {
      "files": "*.ts",
      "parser": "@typescript-eslint/parser",
      "parserOptions": {
        "project": [
          "tsconfig.json",
          "e2e/tsconfig.json"
        ],
        "createDefaultProgram": true
      },
      "plugins": [
        "@typescript-eslint"
      ],
      "extends": [
        "airbnb-typescript/base",
        "plugin:@angular-eslint/ng-cli-compat",
        "plugin:@angular-eslint/ng-cli-compat--formatting-add-on",
        "plugin:@angular-eslint/template/process-inline-templates"
      ],
      "rules": {
        "class-methods-use-this": [
          "off"
        ],
        "import/no-extraneous-dependencies": [
          "off"
        ],
        "import/prefer-default-export": [
          "off"
        ],
        "@angular-eslint/component-selector": [
          "error",
          {
            "type": "element",
            "prefix": "app",
            "style": "kebab-case"
          }
        ],
        "@angular-eslint/directive-selector": [
          "error",
          {
            "type": "attribute",
            "prefix": "app",
            "style": "camelCase"
          }
        ],
        "comma-dangle": "off",
        "@typescript-eslint/comma-dangle": "off"
      }
    },
    {
      "files": [
        "*.spec.ts"
      ],
      "rules": {
        "@typescript-eslint/dot-notation": [
          "off"
        ]
      }
    },
    {
      "files": [
        "*.html"
      ],
      "extends": [
        "plugin:@angular-eslint/template/recommended"
      ],
      "rules": {}
    }
  ]
}
```