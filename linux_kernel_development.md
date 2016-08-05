linux kernel development
=================================
# chapter 2
1. kernel source code:
```
git clone git://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux-2.6.git
git pull
patch -p1 < ../patch-x.y.z
```
2. 内核配置文件位置：内核代码树的根目录下的
```
configure file:.cofig
```
3. 内核提供了各种不同的工具来简化内核配置
```
make config
make defconfig
```
4. 在修改配置文件后，或者在用已有的配置文件配置新的代码树的时候，应该这样验证和更新配置
```
make oldconfig
```
5. 编译内核：
```
make
```
6. 可以衍生出多个编译作业并行进行
```
make -j32
```
7. 内核编程的要点  
  * 内核编程时即不能访问C库也不能访问标准的C头文件
  * 内核编程时必须使用GNU C
  + 内核编程时缺乏像用户空间那样的内存保护机制
  + 内核编程时难以执行浮点运算
  + 内核给每个进程只有一个很小的定长堆栈
  + 由于内核支持异步中断 抢占 SMP，因此必须时刻注意同步和并发
  + 要考虑可移植性的重要性

8. 内核编程使用的头文件均为组成内核源代码树的内核头文件
```
printk(KERN_ERR "this is an error!\n");
```

