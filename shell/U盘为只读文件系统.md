# U盘为只读文件系统

## 问题介绍

插入U盘的时候，文件系统变成了只读，无法修改编辑其中的文件、文件夹。

## 造成原因

不明。

## 解决方案

1. 先卸载U盘，也就是`umount`对应的挂载位置。

  ```shell
  # 在插入U盘的情况下，执行
  tail -f /var/log/syslog
  # 找到对应于U盘的挂载位置，也就是类似`/media/lart/Z`的地址，使用`Ctrl-C`中断`tail`的输出，再执行
  sudo umount /media/lart/Z
  ```

2. 检查修复文件系统

  ```shell
  # 这里的目标路径是前面tail中输出的对应的分区位置，类似于`/dev/sdb1`这样的路径
  sudo dosfsck -v -a /dev/sdb1
  ```

## 参考链接

* https://blog.csdn.net/ITBigGod/article/details/79914534
* 关于dosfsck：http://man.he.net/?topic=dosfsck&section=all
