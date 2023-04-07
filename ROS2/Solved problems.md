## rosdep update:Skip end-of-life distro
https://blog.csdn.net/qq_38313901/article/details/119427055
```
rosdep update --include-eol-distros
rosdep install -y --from-paths src --ignore-src --rosdistro kinetic
```

## c++: internal compiler ereor: killed(program cciplus)
https://blog.csdn.net/u011897411/article/details/89742008
```
1. 创建分区
sudo dd if=/dev/zero of=/swapfile bs=1M count=1024    # 1 * 1024 = 1024 创建 1 g 的内存分区
sudo mkswap /swapfile
sudo swapon /swapfile
free -m    #可以查看内存使用
创建完交换分区之后就可以继续编译
编译完之后记得用以下命令关闭交换分区

2. 关闭分区
sudo swapoff /swapfile
sudo rm /swapfile
但是有可能你运行sudo dd if=/dev/zero of=/swapfile bs=1M count=1024 这条命令的时候它也会给你报个错 比如：
dd: failed to open '/swapfile': Text file busy
这个时候你只需要运行 sudo swapoff -a 即可解决
```




