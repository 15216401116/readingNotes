# 磁盘操作#
	+ `fdisk -l` 查看所有分区使用情况，包括未挂载，可用于  **分区**
	+ `df` 查看已挂载的分区情况，`df -h` 查看挂载点
	+ `cfdisk` 查看所有分区使用情况 q退出
	+ `tune2fs`命令能够显示未挂载的分区大小，但只对ext族的文件系统有效,gfs2则无效
	+ `dumpe2fs -h /dev/sda1` 查看superblock信息，无h则查看设备所有信息
	+ `ls -li` 查看当前文件夹下所有的文件的inode号码
	+ `ls -l /lib/modules/$(uname -r)/kernel/fs` 查看系统支持的fs
	+ `cat /proc/filesystems` 系统已经加载到内存的支持的fs
	+ `partprobe`强制让内核重新找一次分区表
	+ `mkfs -t ext3 /dev/sda1`**格式化**磁盘分区
	+ `mke2fs -b -i -L -cj`block inode 卷标 日志记录
	+ `fsck -C -f -t ext3 /dev/sda1` 文件系统检查，展示直方图，强制检查，类型
	+ `mount 设备文件名 挂载点`**挂载**设备sda1到某个目录上
	+ `umount -fn`卸载，后可接挂载点或设备文件名
	+ `e2label 设备名称 卷标` 更改设备卷标，可用于挂载
	+ `/etc/fstab` 设置开机自动挂载
	+  `device   | mountpoint| filesystem| parameters |dump| fsck|`
	+  ------------------------------------------------------------------
	+  `/dev/sda5|  /lhr     |   ext3    |	defaults  | 1  |  2  |`
	+  `mount -o loop /lhr/ubuntu.iso /mnt/ubuntu`特殊设备loop挂载
	+  构建swap，新建分区，更改分区ID位82（swap），partprobe更新分区表，mkswap格式化swap分区，swapon启动该swap设备
	+  `free`查看**内存**使用情况

#相关知识#
	+ 一个硬盘最多有四个分区（主分区+扩展分区/dev/sda1，2，3，4），扩展分区不能格式化，可划分逻辑分区sda5,6。。
	+ 硬盘接口 IDE（/dev/hda），SATA，SCSI（多用于服务器）。
	+ `header`表示有多少个磁头，即盘面数
	+ `cylinder` 表示每个盘面有多少个磁道
	+ `sector/track`表示每条磁道有多少扇区。512 Bytes
	+ 扇区是最小的物理存储单位
	+ 柱面是分区（partition）的最小单位
	+ 每个硬盘的第一个扇区最重要：主引导分区（MBR），分区表（PB）
	+ BIOS：开机主动执行，认识第一个可开机的设备
	+ MBR：第一个可开机设备的第一个扇区内的主引导分区块，包含引导加载城区
	+ BOOT Loader：可读取内核来执行的软件。
		+ 提供菜单选择
		+ 载入内核文件
		+ 转交其他loader
	+ Ext2：linux second extended file system(ext2fs)
	+ block是fs分配存储的最小单元，每个block上最多只能有一个文件
	+ 一个文件系统可以理解为一个分区，一个文件系统可有多个block group
	+ block group的内容：
		+ superblock: fs info
		+ filesystem discription:
		+  block bitmap:inuse ,nouse
		+  inode bitmap:inuse, nouse
		+  inode table, date block 