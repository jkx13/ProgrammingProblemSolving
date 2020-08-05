# node相关问题

## 解决gulp运行时const { Math, Object } = primordials;报错
	node.js版本过高导致的, 尝试降级就可以解决(node降级至10.16或更新glup)

## 安装node版本管理模块n
##### 安装命令
```
sudo npm install n -g
```
##### 安装稳定版
```
sudo n stable
```
##### 版本降级/升级
```
sudo n 版本号
```
##### 切换版本
```
sudo n
```

##### 删除版本
```
sudo n rm 版本号
```

## 在用n 切换node版本时 使用node -v就会报错：Segmentation fault: 11 
首先切换回正常版本 如`sudo n 12.18.3`<br/>
其次删除报错版本 `sudo n rm 10.22.0`<br/>
最后重新安装node版本 `sudo n 10.16.3`

## npm run dev 启动时，报了一大堆错误 ，如下：vue Node Sass could not find a binding for your current environment: OS X 64-bit with Node.js 10.x  Found bindings for the following environments:   - OS X 64-bit with Node.js 9.x  This usually happens because your environment has changed since running `n
执行: npm rebuild node-sass


## 由于国内网络环境原因，npm 安装项目依赖过慢或安装失败
#### 查看Node版本和NPM版本确认已安装Node环境
`node -v`
`npm -v`

#### 安装nrm并设置NPM的淘宝镜像
```
npm i -g nrm
nrm use taobao
```

#### 设置依赖安装过程中内部模块下载Node的淘宝镜像

1. （遇到C++模块需要node-gyp编译，而且node-gyp首次编译会依赖Node源码相关就会下载Node） npm config 提供了一个参数disturl ,可设置node 镜像地址 将其指向国内淘宝镜像
2. node-sass版本兼容性差，必须与Node版本对应使用才行，详情请参考 [node-sass-version-association](https://github.com/sass/node-sass/releases);全局缓存中的binding.node版本与Node版本不兼容(可能存在多个node版本的切换)（解决办法: 清除npm缓存且重新安装)`npm cache clean -f` `npm rebuild node-sass`

```
npm config set disturl https://npm.taobao.org/mirrors/node/
```

#### 设置常用模块的淘宝镜像
```
npm config set sass_binary_site https://npm.taobao.org/mirrors/node-sass/
npm config set sharp_dist_base_url https://npm.taobao.org/mirrors/sharp-libvips/
npm config set electron_mirror https://npm.taobao.org/mirrors/electron/
npm config set puppeteer_download_host https://npm.taobao.org/mirrors/
npm config set phantomjs_cdnurl https://npm.taobao.org/mirrors/phantomjs/
npm config set sentrycli_cdnurl https://npm.taobao.org/mirrors/sentry-cli/
npm config set sqlite3_binary_site https://npm.taobao.org/mirrors/sqlite3/
npm config set python_mirror https://npm.taobao.org/mirrors/python/
```

#### 针对node-sass安装失败情况：
安装rimraf `npm i -g rimraf`并设置package.json,package.json中加入npm scripts：
```
{
  "scripts": {
    "reinstall": "rimraf node_modules && npm i"
  }
}
```

安装前请确保当前的Node版本和node-sass版本已兼容

如安装失败：
```
npm cache clean -f
npm rebuild node-sass 或 npm run reinstall
```

后期可考虑把镜像文件搬到自己服务器上，将镜像地址指向自己的服务器即可。

#### 解决这种「NPM镜像问题」的问题。
- 执行npm i前设置淘宝镜像，保证安装项目依赖时都走国内网络

- 安装不成功时，肯定是在安装过程中该模块内部又去下载了其他国外服务器的文件
- 在Github上克隆一份该模块的源码进行分析，搜索包含base、binary、cdn、config、dist、download、host、mirror、npm、site、url等这样的关键词(自行探索，通常「mirror」的匹配度最高)
- 在搜查结果里查找形态像「镜像地址」的代码块，再分析该代码块的功能并提取最终的「镜像地址」，例如node-sass的sass_binary_site去淘宝镜像官网、百度、谷歌等网站查找你需要的镜像地址，如果实在找不到就规范上网把国外服务器的镜像文件拉下来搬到自己或公司的服务器上
- 设置模块依赖的镜像地址：`npm config set <registry name> <taobao url / yourself url>`
- 重新执行npm i安装项目依赖，大功告成

## npm 命令记录
`npm root` :查看当前包的模块安装路径；<br/>
`npm root -g` :查看全局模块安装路径；<br/>
`npm ls 包名` : 查看本地安装指定包及版本信息；<br/>
`npm info 包名` :获取远程版本信息;<br/>
`npm config list`:查看配置信息;

## node-sass安装失败
1. node-sass 模块是对sass-loader的支持

2. `npm install -g cnpm --registry = https://registry.npm.taobao.org`

3. `cnpm install node-sass -S`
4. win10提示无法加载或系统禁止运行脚本等
5. 运行windows powershell 管理员身份
6. 输入: `set-ExecutionPolicy RemoteSigned`修改权限为 A
7. 输入: `get-ExecutionPolicy`
8. 重新安装: `cnpm install node-sass -S`
