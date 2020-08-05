# VsCode相关
### vscode快捷键Mac(Win)
多行编写分单选 (option(alt) + 左键)  /  多行一起选 先选择中多行再 (shift + option(alt) + i)
	
复制当前行 (option(alt) + shift + 向上箭头) 保持光标不动，向下箭头光标一起动

移动代码行首或尾 （command(只 Home) + 左箭头） (command(只 End) + 右箭头)

移动到文档首部或尾部(command(Ctrl+Home) + 上箭头) (command(Ctrl+End) + 下箭头)

或到上次光标位置 (command + u)

块注释(option(alt) + shift + A)

删除代码(command(ctrl) + shift + k)

代码格式化(option(alt) + shift + f)

shift + cmd(ctrl) + p ：显示所有命令
cmd(ctrl) + p ：快速打开文件
shift + cmd(ctrl) + enter 则是在上一行重开一行

选中一个词：cmd(ctrl) + d

cmd + f ：搜索
cmd + alt + f： 替换
cmd + shift + f：在项目内搜索


	
### vscode扩展组件
#### Auto Rename Tag 
自动前后便签重命名

#### Code Runner
右键运行代码
	
### open in browser
文件右键open

### gitignore
文件忽略，选中文件右键
	
### import cost
引入文件分析大小
	
### project mananger
项目管理器（可以把多个文件夹项目放一起)
	
### vscode-icons
显示文件类型图标
	
### Document this
快速生成相应的参数 的注释
	
### 用户代码片段
在首选项里>>代码片段>>配置局部或全局的代码片段，通过关键词触发，代码块body中$1是光标位置，Tab后就在$2
```
{
    "Vue component": {
        "prefix": "vuec",
        "body": [
            "<template>",
            "\t$1",
            "</template>",
            "<script>",
            "export default {",
            "\t",
            "}",
            "</script>",
            "<style lang=\"scss\" scoped>",
            "</style>",
            ""
        ]
    }
}
```
	
### vscode 中集成了 Emmet
编写 HTML 或者 CSS 时，需要输入很多字符。而现在有了 Emmet，通过输入简写就行了 
	元素(Elements)：生成一个 HTML 元素
	> ：生成子元素
	+ ：生成元素的兄弟节点
	* ：生成多个相同的元素
	你可以 . 或者 # 来修饰元素，给元素加上 class 或者 id

### Quokka
能够预览变量函数
	
### CSS Peek
当你在 HTML 文件中右键单击选择器时，选择“ Go to Definition 和 Peek definition ”选项，它便会给你发送样式设置的 CSS 代码段
	
### HTML Boilerplate
通过使用 HTML 模版插件，你就摆脱了为 HTML 新文件重新编写头部和正文标签的苦恼。你只需在空文件中输入 html，并按 Tab 键，即可生成干净的文档结构。
	
### Prettier
Prettier 是目前 Web 开发中最受欢迎的代码格式化程序。安装了这个插件，它就能够自动应用 Prettier，并将整个 JS 和 CSS 文档快速格式化为统一的代码样式。如果你还想使用 ESLint，那么还有个 Prettier – Eslint 插件
	
### Color info
这个便捷的插件，将为你提供你在 CSS 中使用颜色的相关信息。你只需在颜色上悬停光标，就可以预览色块中色彩模型的（HEX、 RGB、HSL 和 CMYK）相关信息了
	
### TODO Highlight
这个插件能够在你的代码中标记出所有的 TODO 注释，以便更容易追踪任何未完成的业务。在默认的情况下，它会查找 TODO 和 FIXME 关键字。当然，你也可以添加自定义表达式
	
### Regex Previewer
用于实时测试正则表达式的实用工具

###  VS code 豆沙绿护眼主题 Atom One Light
快捷键输入  Ctrl+Shift+p   ，输入settings,选择open settings (JSON)
```
"workbench.colorTheme": "Atom One Light",
    "workbench.colorCustomizations": {
    "[Atom One Light]": {
            "editor.background": "#C7EDCC",   
        "sideBar.background": "#C7EDCC",
        "activityBar.background": "#C7EDCC",       
        },
    },
```
配置其他
```
 // #值设置为true时，每次保存的时候自动格式化；值设置为false时，代码格式化请按shift+alt+F
	    "editor.formatOnSave": false,
			// vscode默认启用了根据文件类型自动设置tabsize的选项
			  "editor.detectIndentation": false,
			  // 重新设定tabsize
			  "editor.tabSize": 2,
			  // #每次保存的时候自动格式化 
			  "editor.formatOnSave": true,
			  // #每次保存的时候将代码按eslint格式进行修复
			  "eslint.autoFixOnSave": true,
			  // 添加 vue 支持
			  "eslint.validate": [
			    "javascript",
			    "javascriptreact",
			    {
			      "language": "vue",
			      "autoFix": true
			    }
			  ],
			  // #让prettier使用eslint的代码格式进行校验 
			  "prettier.eslintIntegration": true,
			  // #去掉代码结尾的分号 
			  "prettier.semi": false,
			  // #使用带引号替代双引号 
			  "prettier.singleQuote": true,
			  // #让函数(名)和后面的括号之间加个空格
			  "javascript.format.insertSpaceBeforeFunctionParenthesis": true,
			  // #这个按用户自身习惯选择 
			  "vetur.format.defaultFormatter.html": "js-beautify-html",
			  // #让vue中的js按编辑器自带的ts格式进行格式化 
			  "vetur.format.defaultFormatter.js": "vscode-typescript",
			  "vetur.format.defaultFormatterOptions": {
			    "js-beautify-html": {
			      "wrap_attributes": "force-aligned"
			      // #vue组件中html代码格式化样式
			    }
			  },
			  // 格式化stylus, 需安装Manta's Stylus Supremacy插件
			  "stylusSupremacy.insertColons": false, // 是否插入冒号
			  "stylusSupremacy.insertSemicolons": false, // 是否插入分好
			  "stylusSupremacy.insertBraces": false, // 是否插入大括号
			  "stylusSupremacy.insertNewLineAroundImports": false, // import之后是否换行
			  "stylusSupremacy.insertNewLineAroundBlocks": false // 两个选择器中是否换行
```
	