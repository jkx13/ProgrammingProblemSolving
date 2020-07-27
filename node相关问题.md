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

##在用n 切换node版本时 使用node -v就会报错：Segmentation fault: 11 
首先切换回正常版本 如`sudo n 12.18.3`
其次删除报错版本 `sudo n rm 10.22.0`
最后重新安装node版本 `sudo n 10.16.3`

## npm run dev 启动时，报了一大堆错误 ，如下：vue Node Sass could not find a binding for your current environment: OS X 64-bit with Node.js 10.x  Found bindings for the following environments:   - OS X 64-bit with Node.js 9.x  This usually happens because your environment has changed since running `n
	执行: npm rebuild node-sass
