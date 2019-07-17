# Conda默认会进入base环境

## 问题描述

安装`anaconda`后取消命令行前出现的`base`，取消每次启动自动激活`conda`的基础环境

## 解决方案

1. 方法一：
    * 每次通过进入命令行后通过`conda deactivate`退出`base`环境回到系统自动的环境
2. 方法二
    * 希望在启动时不激活`conda`的`base`环境，通过将`auto_activate_base`参数设置为`false`，`conda config --set auto_activate_base false`
    * 那要进入的话通过`conda activate base`
    * 如果反悔了，还是希望`base`一直留着，通过`conda config --set auto_activate_base true`来恢复

## 参考链接

* https://blog.csdn.net/u014734886/article/details/90718719
