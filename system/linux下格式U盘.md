# linux下格式化U盘方法

今天查了下如何格式化U 盘，这里将方法些出来。

## 预备知识

* U盘的设备表示为：/dev/sdb1
  * 因为如果你只有一块硬盘的话，你自己的硬盘占据了sda，那么U盘就只能使用sdb了。需要特别注意，否则，可能将您的sda上的资料给格式化了!
* U盘要被格式化成为fat格式，而用到的命令是`mkfs.vfat`
  * 这个命令要注意，根据你要格式化分区格式的不 同，这个命令有不同的版本，比如`mkfs.ext2`就是格式化为ext2分区格式.

## 具体方法

如果你的U盘做过镜像，你会发现你的U判会变小很多，那是因为有一部分空间被隐藏了.

首先要查看U盘的设备名，此时必须保证U盘已经跟电脑连接，可以在U盘插入电脑之前和插入电脑之后比对下面命令的结果来得知, 一般是`sdb`对应的设备:

```sh
sudo fdisk -l
```

可以看到, 对应U盘的是:

```sh
Disk /dev/sdb：7.5 GiB，8004304896 字节，15633408 个扇区
单元：扇区 / 1 * 512 = 512 字节
扇区大小(逻辑/物理)：512 字节 / 512 字节
I/O 大小(最小/最佳)：512 字节 / 512 字节
磁盘标签类型：dos
磁盘标识符：0x663eb4c4

设备       启动    起点    末尾    扇区  大小 Id 类型
/dev/sdb1  *          0 3815135 3815136  1.8G  0 空
/dev/sdb2       3737268 3741939    4672  2.3M ef EFI (FAT-12/16/32)
```

卸载U盘，使用如下命令：

```sh
umount /dev/sdb1
```

> 注意：/dev/后面的设备要根据你的实际情况而定，否则后面格式化，丢失数据！！

格式化U盘，并建立vfat文件系统:

```sh
mkfs.vfat /dev/sdb
```

最后再`mount`上U盘，或者把U盘拨了再插上，系统可能会自动mount上, 就可以使用U盘了。

## 其他问题

如果 mkfs.vfat /dev/sdb 出现如下错误：

```sh
mkfs.vfat 3.0.10 (12 Sep 2010)
mkfs.vfat: unable to open /dev/sdb
```

则您需要先格式化`/dev/sdb1`，即使用`mkfs.vfat /dev/sdb1`命令，将`/dev/sdb1`先格式化掉；然后再格式化`/dev/sdb.

如果出现如下错误：

```sh
mkfs.vfat 3.0.10 (12 Sep 2010)
mkfs.vfat: Device partition expected, not making filesystem on entire device '/dev/sdb' (use -I to override)
```

系统提示您需要使用-I参数来完成格式化：`mkfs.vfat -I /dev/sdb`, 这样您就可以完全格式化您的U盘。

## 参考资料

转 linux格式化U盘: <https://blog.csdn.net/huanghuibo/article/details/6721191>
