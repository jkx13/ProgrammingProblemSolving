# Vue项目通过Hbuilder 5+app打包问题
## Vue编译后的dist文件夹配置打包
	1.在HbuilderX中新建5+app项目留下mainfest.json文件并新建image文件夹存放启动图片与图标相关
	
	2.把dist下的文件拷贝至 5+app项目根目录下
	
	3.配置名称/版本/图标/启动图/SDK/权限等
	
	4.配置沉浸式在mainfest.json源码字段"plus"的对象中添加开启沉浸式
```
   "plus" : {
		"statusbar" : {
		    "immersed" : true //开启沉浸式
		},
```
	5.需要在Vue项目main入口文件中根据路由页面设置状态栏前景色。
```

watch: {
    "$route.name": function (name) {
      this.menuIndex = this.routerName.indexOf(name);
      if(!window.plus)return;
        if(name=='login' || name=='home' || name=='otc' || name=='my-miner' || name=='otc-manage'){
          window.plus.navigator.setStatusBarStyle('light');
          return;
        }
      window.plus.navigator.setStatusBarStyle('dark');
    },
  },
  
if (!window.plus) return;
plus.navigator.setStatusBarStyle("dark"); //设置状态栏前景色 dark为黑色字体 light为白色字体
//plus.navigator.setStatusBarBackground('#454567');//设置状态栏背景色
```

## Vue项目打包设置沉浸式的状态栏高度问题
	在mainfest.json源码"plus"字段对象中，设置如下
```
    "plus" : {
        "launchwebview" : {//设置后打包会把状态栏高度加上
            "statusbar" : {
                "background" : "#FFF" //状态栏背景色
            }
        },
        "statusbar" : {
            "immersed" : true, //开启沉浸式
            "style" : "dark" //状态栏前景色
        },
```
	注意：
	1.状态栏背景色只能mainfest.json中能改变
	2.状态栏前景色只能用代码plus.navigator.setStatusBarStyle("dark");改变 //设置状态栏前景色 dark为黑色字体 light为白色字体
	
## Vue项目编译后dist文件通过脚本拷贝到hbuilder 5+app项目中
	shell脚步如下:
```
#!/bin/bash
	curpath=$(cd "$(dirname "$0")"; pwd)
	raw_dir=$curpath"/hbuilder"
	rm -rf $raw_dir"/"assets
	rm -rf $raw_dir"/"js
	rm -rf $raw_dir"/"css
	rm -rf $raw_dir"/"index.html
	add_dir=$curpath"/Vue项目名称/dist"
	mv $add_dir"/"* $raw_dir"/" 

```

## 5+app离线打包过程与注意事项(Android/iOS)
离线打包步骤（Android)
[离线打包地址](https://nativesupport.dcloud.net.cn/AppDocs/usesdk/android)
1. （基础库配置 <span style="font-weight:bold;color:green;">@SDK升级时必须更新</span>）拷贝相关SDK文件**(更新SDK时需要同时更新aar/jar文件和build.gradle配置)(保持Hbuilder版本与下载SDK一致)**

2. (应用配置)：注意 **每次更新版本(修改VersionCode与Name和mainfest.json中保持一致)** <span style="font-weight:bold;color:red;">@版本更新必须更新</span>

3. 配置应用名称 **打开app->res -> main -> values -> strings.xml文件，修改“app_name”字段值，该值为安装到手机上桌面显示的应用名称**

4. 配置应用启动页

5. 配置应用图标和启动界面
	制作应用图标用1024*1024图片png为基础图片,在drawable下文件右键New>>选中**Image Asset**
	在ForegroundLayer>>Asset Type选中image中配置Path 设置Resize
	在clip Art中可以设置背景色
	保存即可

6. (资源配置<span style="font-weight:bold;color:green;">@SDK升级时必须更新</span>)新建assets拷贝data

7. 创建apps文件夹并拷贝资源<span style="font-weight:bold;color:red;">@版本更新必须更新</span>

8. apps下面文件为Hbuilder AppId，确保dcloud_control.xml中的appid与manifest.json中的id与文件夹名一致。

9. 配置模块与第三方SDK与权限

[注意事项](https://nativesupport.dcloud.net.cn/AppDocs/FAQ/android)

离线打包步骤(iOS)
[离线打包地址](https://nativesupport.dcloud.net.cn/AppDocs/usesdk/ios)