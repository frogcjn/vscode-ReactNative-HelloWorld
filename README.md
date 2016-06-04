## [brew]
  1. watchman
  2. git

## [npm global]
  1. typings
  2. typescript
  3. react-native-cli
  4. tslint
  5. eslint

## React Native

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
open .gitignore
```
edit `.gitignore`:
```gitignore
# Typescript
build
typings

# OSX
#
.DS_Store

# Xcode
#
build/
*.pbxuser
!default.pbxuser
*.mode1v3
!default.mode1v3
*.mode2v3
!default.mode2v3
*.perspectivev3
!default.perspectivev3
xcuserdata
*.xccheckout
*.moved-aside
DerivedData
*.hmap
*.ipa
*.xcuserstate
project.xcworkspace

# Android/IJ
#
.idea
.gradle
local.properties

# node.js
#
node_modules/
npm-debug.log

# BUCK
buck-out/
\.buckd/
android/app/libs
android/keystores/debug.keystore
```
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
tsconfig.json:
```json
// http://json.schemastore.org/tsconfig
// https://github.com/Microsoft/TypeScript-Handbook/blob/master/pages/tsconfig.json.md
// https://github.com/Microsoft/TypeScript-Handbook/blob/master/pages/Compiler%20Options.md

{
    "compileOnSave": true, // for Visual Studio 2015, atom-typescript plugin.
    "filesGlob": [
        "typings/**/*.d.ts",
        "src/**/*.ts",
        "src/**/*.tsx"
    ],
    "compilerOptions": {

        /* General Compiler Options */
        "target": "es6",
        // "watch": false,
        // "allowJs": true,
        // "charset": "utf8",
        // "newLine": "LF"

        /* Module, Triple-slash References, Lib */
        // "module": "es6",
        // "moduleResolution": "Classic",
        // "isolatedModules": false,
        // "allowSyntheticDefaultImports": false,
        "forceConsistentCasingInFileNames": true,
        // "noResolve": false,
        // "skipDefaultLibCheck": false,
        // "noLib": fasle,

        /* Consule Output */
        "locale": "zh-CN",
        "pretty": true,
        // "listFiles": false
        // "diagnostics": false,

        /* Check */
        // "allowUnreachableCode": false,
        // "allowUnusedLabels": false,
        "noFallthroughCasesInSwitch": true,
        "noImplicitAny": true,
        "noImplicitReturns": true,
        // *"suppressImplicitAnyIndexErrors": true,
        // *"suppressExcessPropertyErrors": true,

        /* Output Files */
        "rootDir": "./src",
        "outDir": "./build",

        // "outFile": false,

        // "sourceMap": false,
        // "declaration": false,

        "inlineSourceMap": true,
        // "inlineSources": false,

        /* Debug Root Path */
        // "mapRoot": null,
        // "sourceRoot": null,

        /* Emit */
        // "emitBOM": false,
        "preserveConstEnums": true,

        // "noEmit": false,
        "noEmitOnError": true,
        // "noEmitHelpers": false,
        // "noImplicitUseStrict": false,
        // "removeComments": false,
        "stripInternal": true,

        /* JSX & React */
        "jsx": "react",
        // "reactNamespace": "React",

        /* Declorator */
        "experimentalDecorators": true
        // "emitDecoratorMetadata": false,
    }
}
```
edit `./index.ios.js`:
```javascript
/**
 * Sample React Native App
 * https://github.com/facebook/react-native
 * @flow
 */

import helloworld from "./build/index.ios";
import { AppRegistry } from "react-native";

AppRegistry.registerComponent("helloworld", () => helloworld);
```
edit `./src/index.ios.tsx`:
```javascript
/**
 * Sample React Native App
 * https://github.com/facebook/react-native
 * @flow
 */

import * as React from "react"
const {Component} = React
import {
    StyleSheet,
    Text,
    View
} from "react-native"

export default class AwesomeProject extends Component<any, any> {
    public render() {
        return (
            <View style={styles.container}>
                <Text style={styles.welcome}>
                    Welcome to React Native!
                </Text>
                <Text style={styles.instructions}>
                    To get started, edit index.ios.js
                </Text>
                <Text style={styles.instructions}>
                    Press Cmd+R to reload, {"\n"}
                    Cmd+D or shake for dev menu
                </Text>
            </View>
        )
    }
}

const styles = StyleSheet.create({
    container: {
        flex: 1,
        justifyContent: "center",
        alignItems: "center",
        backgroundColor: "#F5FCFF"
    },
    welcome: {
        fontSize: 20,
        textAlign: "center",
        margin: 10
    },
    instructions: {
        textAlign: "center",
        color: "#333333",
        marginBottom: 5
    }
})
```
工作区设置
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
TSLint
```json
{
    "rules": {
        // "member-access": false,
        "member-ordering": [
            true,
            {
                "order": "fields-first"
            }
        ],
        // "no-any": false,
        "no-inferrable-types": [
            true,
            "ignore-params"
        ],
        "no-internal-module": true,
        "no-namespace": [
            true,
            "allow-declarations"
        ],
        "no-reference": true,
        "no-var-requires ": true,
        // "typedef": false
        "typedef-whitespace": [
            true,
            {
                "call-signature": "nospace",
                "index-signature": "nospace",
                "parameter": "nospace",
                "property-declaration": "nospace",
                "variable-declaration": "nospace"
            },
            {
                "call-signature": "onespace",
                "index-signature": "onespace",
                "parameter": "onespace",
                "property-declaration": "onespace",
                "variable-declaration": "onespace"
            }
        ],
        // "ban": false,
        "curly": true,
        // "forin": false,
        "label-position": true,
        "label-undefined": true,
        "no-arg": true,
        "no-bitwise": true,
        "no-conditional-assignment": true,
        // "no-console": false,
        "no-construct": true,
        // "no-debugger": false,
        "no-duplicate-key": true,
        "no-duplicate-variable": true,
        "no-empty": true,
        "no-eval": true,
        "no-invalid-this": [
            true,
            "check-function-in-method"
        ],
        "no-null-keyword": true,
        "no-shadowed-variable": true,
        "no-string-literal": true,
        "no-switch-case-fall-through": true,
        "no-unreachable": true,
        "no-unused-expression": true,
        "no-unused-variable": [
            true,
            "check-parameters",
            "react",
            {
                "ignore-pattern": "^_"
            }
        ],
        // "no-use-before-declare": false,
        "no-var-keyword": true,
        "radix": true,
        "switch-default": true,
        "triple-equals": true,
        "use-isnan": true,
        "use-strict": [
            true,
            "check-module",
            "check-function"
        ],
        "eofline": true,
        "indent": [
            true,
            "spaces"
        ],
        "max-line-length": [
            true,
            120
        ],
        // "no-default-export": false,
        "no-require-imports": true,
        "no-trailing-whitespace": true,
        // "object-literal-sort-keys": false,
        "trailing-comma": [
            true,
            {
                "singleline": "never",
                "multiline": "never"
            }
        ],
        "align": [
            true,
            "parameters",
            "arguments",
            "statements"
        ],
        "class-name": true,
        "comment-format": [
            true,
            "check-space"
        ],
        "interface-name": [
            true,
            "always-prefix"
        ],
        "jsdoc-format": true,
        "new-parens": true,
        "no-angle-bracket-type-assertion": true,
        "no-consecutive-blank-lines": true,
        // "no-constructor-vars": false,
        "one-line": [
            true,
            "check-else",
            "check-catch",
            "check-finally",
            "check-open-brace",
            "check-whitespace"
        ],
        "one-variable-per-declaration": [
            true,
            "ignore-for-loop"
        ],
        "quotemark": [
            true,
            "double",
            "jsx-double"
        ],
        "semicolon": [
            true,
            "never"
        ],
        "variable-name": [
            true,
            "check-format",
            "allow-leading-underscore",
            "allow-trailing-underscore",
            "allow-pascal-case",
            "ban-keywords"
        ],
        "whitespace": [
            true,
            "check-branch",
            "check-decl",
            "check-operator",
            "check-module",
            "check-separator",
            "check-type",
            "check-typecast"
        ]
    }
}
```
ESLint
edit `eslintrc.json`
```json
{
    "parserOptions": {
        "ecmaVersion": 7,
        "sourceType": "module",
        "ecmaFeatures": {
            "globalReturn": false,
            "impliedStrict": true,
            "jsx": true,
            "experimentalObjectRestSpread": true
        }
    },
    "env": {
        "es6": true
    },
    "extends": "eslint:recommended",
    "rules": {
        "indent": [
            "warn",
            4
        ],
        "linebreak-style": [
            "warn",
            "unix"
        ],
        "quotes": [
            "warn",
            "double"
        ],
        "semi": [
            "warn",
            "never"
        ],
        "no-unused-vars": [
            "warn",
            {
                "vars": "all",
                "args": "all",
                "caughtErrors": "all",
                "varsIgnorePattern": "^_",
                "argsIgnorePattern": "^_",
                "caughtErrorsIgnorePattern": "^_"
            }
        ]
    }
}
```
`.eslintignore`
```
# /node_modules/* and /bower_components/* ignored by default

# Ignore built files except build/index.js
build/*
!build/index.js
```


