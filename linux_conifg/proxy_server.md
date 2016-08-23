##代理服务器客户端配置##
1. 
```
export http_proxy=http://10.137.59.22:3128   
```
2. 
```
export https_proxy=https://10.137.59.22:3128   
```
3. 
```
export ftp_proxy=ftp://10.137.59.22:3128`
```
+ 写入~/.bashrc可使当前用户每次打开shell时配置该代理服务器信息
+ source ~/.bashrc 重置.bashrc
+ unset http_proxy用来删除环境变量
##代理服务器服务器端配置## squid安装配置
###redhat###
1. rpm -qa | grep squid* 查看是否已安装squid
2. yum install squid*  安装squid
3. chkconfig squid –list 
4. chkconfig squid on 配置每次启动服务器时都启动squid
5. chkconfig squid –list
6. vim /etc/sysctl.conf
7. net.ipv4.ip_forward = 0->1
8. sysctl –p /etc/sysctl.conf 使ip转发永久生效
9. vim /etc/squid/squid.conf 添加localhost_ip，即添加客户端ip
10. 查看监听端口http_port，默认是3128
11. service squid restart
12. 关闭防火墙

####整体：安装squid，配置quid，重启quid，关闭防火墙
###可以通过wget www.baidu.com来测试是否代理成功
####`wget`：linux系统的下载文件工具，支持http https ftp，支持http代理

##服务器端查看网络流量##
+ `iptraf-ng`工具，需要先下载
##添加环境变量时bashrc和profile的区别##
+ bashrc：用于交互式非登录，即每次打开shell时执行一次
+ profile：用于交互式登录时，包括ssh，bash登录
+ ~/.bashrc 某一单一用户
+ /etc/profile  全局设定