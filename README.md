# Automatic-start
Linux开机自动启动某个脚本

**通过sysv-rc-conf命令设置**


1.在/etc/init.d 里面建立一个test.sh(启动文件前面务必添加如下三行代码，否侧会提示sysv-rc-conf不支持。
```
#!/bin/sh                             告诉系统使用的shell,所以的shell脚本都是这样
#sysv-rc-conf: 35 20 80               分别代表运行级别，启动优先权，关闭优先权，此行代码必须
#description: v2ray server            自己随便发挥！！！，此行代码必须
```

2.内容如下：

```
#!/bin/sh
#sysv-rc-conf: 35 20 80
#description: v2ray server
cd /root/v2
bash start.sh
```
3.增加脚本的可执行权限
```
chmod +x  /etc/init.d/test.sh
```
4.然后安装sysv-rc-conf
```
apt-get install sysv-rc-conf
```
5.添加脚本到开机自动启动项目中。添加到sysv-rc-conf，开机自启动。
```
cd /etc/init.d
sysv-rc-conf --add test.sh
sysv-rc-conf test.sh on
```
6.关闭开机启动 
```
sysv-rc-conf test.sh off
```
7.从sysv-rc-conf管理中删除test.sh
```
sysv-rc-conf --del test.sh
```
8.查看sysv-rc-conf管理
```
sysv-rc-conf --list test.sh
```
