## rosdep update:Skip end-of-life distro
https://blog.csdn.net/qq_38313901/article/details/119427055


## c++: internal compiler ereor: killed(program cciplus)
https://blog.csdn.net/u011897411/article/details/89742008
# 1. 创建分区
sudo dd if=/dev/zero of=/swapfile bs=1M count=1024    # 1 * 1024 = 1024 创建 1 g 的内存分区
sudo mkswap /swapfile
sudo swapon /swapfile

# free -m    #可以查看内存使用
# 创建完交换分区之后就可以继续编译
# 编译完之后记得用以下命令关闭交换分区
# 某次我就是忘了关闭交换分区，导致开不了机，然后切换 tty1 ，登进去之后关闭交换分区才可以进入桌面的。

#2. 关闭分区
sudo swapoff /swapfile
sudo rm /swapfile
————————————————
版权声明：本文为CSDN博主「Hzhihua」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/u011897411/article/details/89742008
