登录 ./mysql -u root -p
修改密码：set password=password("root");
登录授权：grant all privileges on *.* to'root' @'%' identified by 'root';
授权生效：flush privileges;


配置全局命令：
echo 'export PATH=/application/mysql/bin:$PATH' >>/etc/profile   //echo后必须用单引号，双引号不行
tail -l /etc/profile   //查看配置后的全局路径
source /etc/profile  //执行source使全局路径生效


#####  开启mysql远程连接
1. grant all privileges on *.* to 'root'@'%' identified by 'root' with grant option;
2. flush privileges;刷新权限
3. 查询用户：  SELECT DISTINCT CONCAT('User: ''',user,'''@''',host,''';') AS query FROM mysql.user;
4. 使用exit命令退出MySQL
```
然后打开vim  /etc/mysql/my.cnf

将bind-address    = 127.0.0.1

 设置成bind-address    = 0.0.0.0（设备地址）
 
 重新启动（命令如下）：
 
 /etc/init.d/mysql stop
 
 /etc/init.d/mysql start
```
 
 5. 查看端口号
```
show global variables like 'port';  
```