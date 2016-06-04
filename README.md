## Enviroment
# brew install
  1. watchman
  2. git
  3. ideviceinstaller

# npm i -g
  1. typings
  2. typescript
  3. react-native-cli
  4. tslint
  5. eslint

# VSCode extension
  1. ESLint
  2. TSLint
  3. React Native Tools
  4. Document This
  5. Flow Language Support
  6. final-new line
  7. Run on save

## React Native Init

run shell:
```shell
react-native init helloworld
cd helloworld
```
Run iOS:
```
react-native run-ios
```
Run Android:
configure avd as
https://facebook.github.io/react-native/docs/getting-started.html#content
```
 android avd
 react-native run-android
```

## Git

run shell:
```shell
touch .gitignore
```
edit `.gitignore`

run shell:
```
git init
```

## Typings
run shell:

```shell
typings install dt~react dt~react-native -SG (--save --global)
```

## TypeScript

```shell
tsc --init
open tsconfig.json
```
edit `tsconfig.json`

edit `index.ios.js`, `index.android.js`
edit `src/index.ios.tsx`, `src/index.android.js`

## Auto Saving

# User settings
```json
{
    "html.format.endWithNewline": true,
    "files.insertFinalNewline": true,
    "files.trimTrailingWhitespace": true,
    "editor.scrollBeyondLastLine": false,
    "files.autoSave": "onFocusChange",
    "emeraldwalk.runonsave": {
        "autoClearConsole": true,
        "commands": [
            {
                "match": "^$",
                "isAsync": false,
                "cmd": "clear"
            }/*,
            {
                "match": ".ts$",
                "isAsync": false,
                "cmd": "tsc -p {workspaceRoot}"
            }*/
            /*,
            {
                "match": ".js$",
                "isAsync": false,
                "cmd": "cd {workspaceRoot}; node_modules/.bin/babel src --out-dir lib"
            }*/
        ]
    }
}
```

# Workspace settings
edit `.vscode/settings.json`
```json
// 将设置放入此文件中以覆盖默认值和用户设置。
{

    // 配置 glob 模式以排除文件和文件夹。
    "files.exclude": {
        "node_modules": true,
        "build": true,
        "typings": true
    },

    "emeraldwalk.runonsave": {
        "autoClearConsole": true,
        "commands": [
            {
                "match": "\\.tsx?$",
                "isAsync": true,
                "cmd": "tsc -p ${workspaceRoot} && echo Running on save finished."
            }
        ]
    }
}
```

## TSLint
edit `tslint.json`
[`tslint.json`](tslint.json)

## ESLint
edit `.eslintrc.json` and `.eslintignore`
[`eslintrc.json`](.eslintrc.json)

[`.eslintignore`](.eslintignore)

