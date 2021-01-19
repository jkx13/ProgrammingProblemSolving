#打包低版本手机有两个错：
### Uncaught SyntaxError: Use of const in strict mode.
### Cannot read property 'call' of undefined

	部分参考自：https://blog.csdn.net/qq_25186543/article/details/80484215

1. 安装 babel-polyfill 、es6-promise ，然后在配置文件里改动一下

```
npm install --save-dev babel-polyfill

npm install --save-dev es6-promise
```

2. 写入mian.js

```
import 'babel-polyfill'
import Es6Promise from 'es6-promise'

require('es6-promise').polyfill();
Es6Promise.polyfill();
```


3. 在  webpack.base.conf.js 里

```
把
entry: {
    app: './src/main.js'
  }
改为：
 entry: {
    app: ["babel-polyfill", "./src/main.js"]
  }
```

4. 在  webpack.base.conf.js 里 module => rules

```
{
        test: /\.js$/,
        loader: 'babel-loader',
        include: [resolve('src'), resolve('test'), 
        resolve('node_modules/webpack-dev-server/client'),
        resolve('/node_modules/muse-ui/dist/muse-ui.esm.js'),]
}

```

	这个项目使用了muse-ui。 muse-ui.esm.js这个js文件在低版本手机上不能把es6语法转化为es5。
	这里添加转化。如果还有错误可能还有js文件未转化。可以在这里统一添加