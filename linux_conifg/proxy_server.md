##代理服务器客户端配置##
export http_proxy=http://10.137.59.22:3128
export https_proxy=https://10.137.59.22:3128
export ftp_proxy=ftp://10.137.59.22:3128
+ 写入~/.bashrc可使当前用户每次打开shell时配置该代理服务器信息
 + source ~/.bashrc 重置.bashrc
+ unset http_proxy用来删除环境变量
+ `/etc/network/interfaces`：`dns-nameservers 8.8.8.8`配置dns域名服务器
+ 
##代理服务器服务器端配置## squid安装配置
redhat:
	+ rpm -qa | grep squid*
	+ yum install squid*
	+ chkconfig squid –list
	+ chkconfig squid on
	+ chkconfig squid –list
	+ vim /etc/sysctl.conf
	+ net.ipv4.ip_forward = 0->1
	+ sysctl –p /etc/sysctl.conf使ip转发永久生效
	+ vim /etc/squid/squid.conf添加localhost_ip:port
	+ 查看监听端口http_port，默认是3128
	+ service squid restart
	+ 关闭防火墙
ubuntu：类似
整体：安装squid，配置quid，重启quid，关闭防火墙
可以通过wget www.baidu.com来测试是否代理成功
`wget`：linux系统的下载文件工具，支持http https ftp，支持htt代理


##服务器端查看网络流量##
+ `iptraf-ng`
##添加环境变量时bashrc和profile的区别##
bashrc：用于交互式非登录，即每次打开shell时执行一次
profile：用于交互式登录时，包括ssh，bash登录
~/.bashrc 某一单一用户
/etc/profile  全局设定