##ubuntu14.04 安装arm-linux-gcc交叉编译环境
+ 下载文件：arm-linux-gcc-4.5.1-v6-vfp-20120301.tgz
	+ http://pan.baidu.com/s/1pJwQ6Sj
+ 新建文件夹并copy进去该压缩包
	+ sudo tar xvzf arm-linux-gcc-4.5.1-v6-vfp-20120301.tgz 解压，得到./opt
+  进入到./opt/FriendlyARM/toolschain/4.5.1/bin中
+  pwd得到该路径，将该路径加入到环境变量中：
	+  sudo vim /etc/bash.bashrc
	+  在末尾添加如下内容
	+  `if  [ -d /home/???/???/opt/FriendlyARM/toolschain/4.5.1 ] ;  then
PATH=/home/???/???/opt/FriendlyARM/toolschain/4.5.1/bin:"${PATH}"
fi`
+ 刷新 source /etc/bash.bashrc
+ 检查是否将路径加入到PATH中：export $PATH
+ 测试是否安装成功：
	+ arm-linux-gcc -v  输入命令会显示arm-linux-gcc信息和版本.
	+ 编写hello.c
	+ `#include<stdio.h>int main()
{
 printf("Hello,wrld!\n");
 return 0;
}
`
	+ arm-linux-gcc -o hello hello.c
	+ file hello
	+ 显示`hello: ELF 32-bit LSB executable, ARM, version 1 (ARM), for GNU/Linux 2.4.3, dynamically linked (uses shared libs), not stripped`则成功
+ debug：报错
`error while loading shared libraries: libz.so.1: cannot open shared object file: No such file or directory`
+ 原因：64位的操作系统没有32位的类库，而下载的交叉编译环境是32位的
+ sudo apt-get update
+ sudo apt-get install ia32-libs
+ 运行第二个命令时有可能会说找不到或者被其它的所替代,然后再把终端列出的安装就好了.
+ `However the following packages replace it:
  lib32z1 lib32ncurses5 lib32bz2-1.0
`

