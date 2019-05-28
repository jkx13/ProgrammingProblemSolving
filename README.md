# ProgrammingProblemSolving
主要更新收集前端后端遇到的编程问题及解答

前端用HBuilderX IDE用uni-app框架开发app
1.遇到一个报 [错误] ERR: ./pages/xxxx.vue(405:6): unexpected `{` ?
解答: 查找发现是sytle中用scss编译报错 如下格式报错：-webkit-/-ms-等前缀
