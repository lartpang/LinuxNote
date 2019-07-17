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

## 文档建议

有一种更合适的方法，就是直接取消conda默认的显示环境的设置，如下所述：

> To simply return to the `base` environment, it's better to call `conda activate` with no environment specified, rather than to try to deactivate. If you run `conda deactivate` from your `base` environment, *you may lose the ability to run conda at all*. Don't worry, that's local to this shell - you can start a new one.
>
> By default, the command prompt is set to show the name of the active environment. To disable this option:
>
>```shell
>conda config --set changeps1 false
>```
>
>To re-enable this option:
>
>```shell 
>conda config --set changeps1 true
>```

## 参考链接

* https://blog.csdn.net/u014734886/article/details/90718719
* https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html#determining-your-current-environment
