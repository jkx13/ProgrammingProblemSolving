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