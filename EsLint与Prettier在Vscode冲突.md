## 方法一
### 1.安装依赖
```shell
yarn add prettier -D --exact
yarn add eslint-plugin-prettier -D
yarn add eslint-config-prettier -D
```

### 2.修改 eslintrc.js
```javascript
module.exports = {
	extends:[
		//添加
		'plugin:prettier/recommended'
	],
	rules:{
		//添加
		//'prettier/prettier': ['error', { singleQuote: true, parser: 'flow' }],
	}
}
```

### 3.修改本地.vscode 中setting.json
```json
{
    "search.exclude": {
        "**/node_modules": true,
        "**/bower_components": true,
        "**/*.code-search": true
    },
    "editor.formatOnSave": true,
    "[javascript]": {
        "editor.defaultFormatter": "esbenp.prettier-vscode"
    },
    "[javascriptreact]": {
        "editor.defaultFormatter": "esbenp.prettier-vscode"
    },
    "[typescript]": {
        "editor.defaultFormatter": "esbenp.prettier-vscode"
    },
    "[typescriptreact]": {
        "editor.defaultFormatter": "esbenp.prettier-vscode"
    },
    "[json]": {
        "editor.defaultFormatter": "esbenp.prettier-vscode"
    },
    "[html]": {
        "editor.defaultFormatter": "esbenp.prettier-vscode"
    },
    "[markdown]": {
        "editor.defaultFormatter": "esbenp.prettier-vscode"
    },
    "[less]": {
        "editor.defaultFormatter": "esbenp.prettier-vscode"
    },
    "[css]": {
        "editor.defaultFormatter": "esbenp.prettier-vscode"
    },
    "eslint.validate": [
        "javascript",
        "javascriptreact",
        "typescript",
        "typescriptreact"
    ],
    "typescript.tsdk": "./node_modules/typescript/lib",
    "editor.codeActionsOnSave": {
        "source.fixAll.eslint": true
    },
    "eslint.options": {
        "configFile": ".eslintrc.js"
    }
}
//两次格式化 一次是在codeActionsOnSave使用eslint进行格式化，一次是在formatOnSave的时候prettier进行格式化
```

## 方法二
```
// 在vscode中setting.json设置只使用eslint规范进行保存代码格式化
{
	"eslint.format.enable":true,
	"[javascript]":{
		"editor.defaultFormatter":"dbaeumer.vscode-eslint"//规范prettier改为eslint
	}
}
```

## 方法三
## 安装插件 eslint-config-prettier
```shell
yarn add eslint-config-prettier -D
```

```json
//在.eslintrc.js的extends中: 'prettier'放在原来添加的配置的后面
{
	extends:[
		'prettier',
		'prettier/@typescript-eslint',
		'prettier/react',
		'prettier/unicorn'
	]
}
```