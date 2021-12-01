# React TypeScript Project with ESLint and Prettier

### Why use ESLint and Prettier?

ESLint is one of the most popular tools for code quality rules check and code formatting.
Prettier is a code formatting tool that works better than ESLint.


#### Index:
1. [Setting up ESLint](#1)
2. [Setting up Prettier](#2)
3. [Checking files content](#3)
4. [Making ESLint and Prettier work together](#4)

#### Prerequisites:
Node >= 10


<a name="1"></a>
## 1. Setting up ESLint

#### Remove pre-setted ESLint:
React initialized with CRA comes with an eslint configuration pre-setted. Let’s remove this configuration so we can set a better one. To do this, remove the follow code from ‘package.json’ file

```
"eslintConfig": {
   "extends":[
      "react-app",
      "react-app/jest"
   ]
}
```
### Install ESLint package:
`npm install eslint --save-dev`

### Setup ESLint:
`npx eslint --init`

When running this command, you will need to answer some questions about the configuration:

| OPTION | SELECTION |
| --- | ------|
| How would you like to use ESLint? | To check syntax, find problems, and enforce code style
| What type of modules does your project use?| JavaScript modules (import/export)
|Which framework does your project use?| React
|Does your project use TypeScript?| Yes
|Where does your code run?| Browser
|How would you like to define a style for your project?| Use a popular style guide
|Which style guide do you want to follow?| Airbnb: https://github.com/airbnb/javascript
|What format do you want your config file to be in?| JSON
|Would you like to install them now with npm?| Yes

### Install VS Code ESLint extension
Install it manually from the VSCode extensions menu or run the following command
`ext install dbaeumer.vscode-eslint`

### Solving remaining problems

TBD

<a name="2"></a>
## 2. Setting up Prettier


### Install Prettier package
`npm install --save-dev --save-exact prettier`

### Install Prettier VSCode extension
Install it manually from the VSCode extensions menu or run the following command
`ext install esbenp.prettier-vscode`


<a name="3"></a>
## 3. Checking files content
Edit the files to match the content

### Package JSON
/package.json
```
"devDependencies": {
    "@typescript-eslint/eslint-plugin": "^5.1.0",
    "@typescript-eslint/parser": "^5.1.0",
    "eslint": "^7.32.0",
    "eslint-config-airbnb": "^18.2.1",
    "eslint-config-prettier": "^8.3.0",
    "eslint-plugin-jsx-a11y": "^6.4.1",
    "eslint-plugin-prettier": "^4.0.0",
    "prettier": "2.4.1"
  }
```

### ESLint JSON
/.eslintrc.json
```{
  "env": {
    "browser": true,
    "es2021": true
  },
  "extends": ["react-app", "airbnb", "plugin:jsx-a11y/recommended", "plugin:prettier/recommended"],
  "plugins": ["jsx-a11y", "prettier"],
  "rules": {
    "eol-last": "error",
    "react/jsx-filename-extension": [
      1,
      {
        "extensions": [".js", ".jsx", ".tsx"]
      }
    ],
    "import/extensions": [
      "error",
      "ignorePackages",
      {
        "js": "never",
        "jsx": "never",
        "ts": "never",
        "tsx": "never"
      }
    ],
    "react/jsx-props-no-spreading": "off",
    "no-use-before-define": "off",
    "@typescript-eslint/no-use-before-define": ["error"],
    "import/no-extraneous-dependencies": "off",
    "no-unused-vars": "off",
    "react/react-in-jsx-scope": "off",
    "@typescript-eslint/no-unused-vars": "error",
    "no-shadow": "off",
    "react/require-default-props": "off",
    "import/no-unresolved": "off",
    "react/jsx-uses-react": "off",
    "jsx-a11y/media-has-caption": "off",
    "react-hooks/rules-of-hooks": "error",
    "react-hooks/exhaustive-deps": "warn",
    "@typescript-eslint/explicit-function-return-type": [
      "warn",
      {
        "allowExpressions": true
      }
    ]
  },
  "settings": {
    "import/resolver": {
      "node": {
        "extensions": [".js", ".jsx", ".ts", ".tsx"]
      }
    }
  },
  "globals": {
    "JSX": "writable"
  }
}
```

### ESLint Ignore
/.eslintignore
```
*.css
*.svg
```

### Prettier JSON
/.prettierrc.json
```
{
    "trailingComma": "es5",
    "tabWidth": 4,
    "printWidth": 120,
    "semi": false,
    "singleQuote": true,
    "endOfLine": "auto"
}
```

### Prettier Ignore
/.prettierignore
```
node_modules

# Ignore artifacts:
build
coverage
```

<a name="4"></a>
## 4. Making ESLint and Prettier work together

### VSCode Settings
/.vscode/settings.json
```
{
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "editor.formatOnSave": true,
  "eslint.alwaysShowStatus": true,
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
  }
}
```

## Extra
Change Prettier's "errors" to "warnings" to avoid compile fail
`
{
...
  "rules": {
    "prettier/prettier": "warn",
  }
...
}
`
