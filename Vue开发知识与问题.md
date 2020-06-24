# Vue开发知识与问题

## vue ESLint报No ESLint configuration found
	eslint是用来管理和检测js代码风格的工具，可以和编辑器搭配使用，如vscode的eslint插件当有不符合配置文件内容的代码出现就会报错或者警告.
##### 安装
	npm init -y
	npm install eslint --save-dev
	./node_modules/.bin/eslint --init 初始化配置文件