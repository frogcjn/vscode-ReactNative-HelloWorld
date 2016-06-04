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
