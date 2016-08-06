常用linux命令
===
1. `Ctrl+z` 挂起当前命令
2. `bg 1`将命令1后台运行
3. `Jobs` 显示后台运行命令
4. `fg 1` 将命令1调回前台
5. `Ctrl+c` 终止当前命令
6. `Nano` 文本编辑器  ctrl+o 写入 ctrl+x 离开
7. `Sudo passwd` 设置root密码
8. 更改开机模式：`/etc/X11/default-display-manager`：
`false`命令行模式
`usr/sbin/lightdm` x window 桌面模式
9. `uname –a` 查看版本
10. radhat或centos存在：`/etc/redhat-release` 这个文件
11. debian或ubuntu 存在 `/etc/debian_version` 这个文件
12. Slackware存在 `/etc/slackware_version` 这个文件
13. ubuntu存在 `/etc/lsb-release` 这个文件
14. `df` 查看linux硬盘空间
15. `du –h –max-depth=1 ./` 查看当前目录下的所有文件及文件夹的大小（当前目录下且深度为1）
16. `du –h –-max-depth=0` 查看当前目录大小
17. `pwd` 查看当前路径
+ linux CPU使用情况：`cat /proc/cpuinfo` 查看每个逻辑processor的信息：
	+ `physical id` 指明当前逻辑处理器属于哪个物理封装
	+ `core id` 	指明当前逻辑处理器属于哪个处理器内核
	+ `cpu cores` 	指明当前逻辑处理器所在物理封装中处理器内核数量
	+ `siblings` 	指明当前逻辑处理器所在物理封装中逻辑处理器个数
	+ 一个cpu物理封装可以有多个处理器内核（多核），每个处理器内核可以有多个逻辑处理器。若一个处理器内核中有一个以上的逻辑处理器，则说明系统支持超线程“HT”技术。若一个物理封装中有一个以上的处理器内核，则说明该系统为多内核处理器。
	+ `cat /proc/cpuinfo| grep "physical id"| sort| uniq| wc -l` 查看物理cpu个数
	+ `cat /proc/cpuinfo| grep "cpu cores"| uniq` 查看每个物理cpu中的核数
	+ `cat /proc/cpuinfo| grep "processor"| wc -l` 查看逻辑cpu的总数
+ 磁盘操作
	+ `fdisk -l` 查看所有分区使用情况，包括未挂载
	+ `df` 查看已挂载的分区情况，`df -h` 查看挂载点
	+ `cfdisk` 查看所有分区使用情况 q退出
	+ `tune2fs`命令能够显示未挂载的分区大小，但只对ext族的文件系统有效, gfs2则无效