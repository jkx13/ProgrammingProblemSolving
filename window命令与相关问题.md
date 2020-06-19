# window命令与相关问题
## 快捷键
	按快捷键win+R后，输入“sysdm.cpl”打开环境变量

## 配置node环境变量
	配置node:path
	D:\Program\nodejs\node-global
	D:\Program\nodejs\node_modules
## 配置java环境变量
	JAVA_HOME: D:\Program Files\Java\jdk1.8.0_77
	CLASSPATH: .;%JAVA_HOME%\lib;%JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar;
	path： %JAVA_HOME%\bin

## 配置Android环境变量
	ANDROID_HOME: C:\Users\jack\AppData\Local\Android\Sdk
	path:
	%ANDROID_HOME%\platform-tools
	%ANDROID_HOME%\emulator
	%ANDROID_HOME%\tools
	%ANDROID_HOME%\tools\bin
## keytool查看keystore签名信息
	keytool -list -v -keystore my_android.keystore -storepass keystore_password

## 配置node 配置文件夹路径
	npm config set prefix "E:\Program~1\nodejs\node_global"
	npm config set cache "E:\Program~1\nodejs\node_cache"
## 安装镜像npm安装
	npm install -g mirror-config-china --registry=http://registry.npm.taobao.org
	
	npm install -g cnpm --registry=https://registry.npm.taobao.org
	cnpm install node-sass
	
## windows进入指定路径 并执行
	cmd /k "cd /d D:\rn_work\Ls.Trade.WebApp&&执行命令"
