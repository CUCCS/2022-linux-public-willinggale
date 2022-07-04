# Homework 3
1. 如何添加一个用户并使其具备sudo执行程序的权限？

添加一个用户：`sudo adduser guest`

使其具备sudo执行程序的权限：`sudo usermod -G sudo -a guest`
![](img\添加用户设置权限.jpg)

2. 如何将一个用户添加到一个用户组？

新建工作组：`groupadd groupname`

将用户添加进工作组：`sudo -- usermod –G groupname username`

3. 如何查看当前系统的分区表和文件系统详细信息？

查看分区表：`sudo fdisk -l`
![](img\查看分区.jpg)
显示目前磁盘空间和使用情况：`df -h`
![](img\查看磁盘空间.jpg)
查看文件系统类型`mount` `dumpe2fs [-h] 文件名`

4. 如何实现开机自动挂载Virtualbox的共享目录分区？

在宿主机上新建文件夹share，在virtualbox的共享文件夹部分完成设置（选择固定分配）
![](img\设置共享文件夹.jpg)
在 Ubuntu 中新建共享文件夹：`sudo mkdir /mnt/share`

挂载：`sudo mount -t vboxsf sharefile /mnt/share`

修改fstab文件：`vim /etc/fstab`, 添加`sharefile /mnt/share/ vboxsf defaults 0 0`
![](img\fstab.jpg)

5. 基于LVM（逻辑分卷管理）的分区如何实现动态扩容和缩减容量？

把分区XXX剩余空间创建分区并改为LVM格式：`fdisk XXX #`

扩容：`lvextend -L +<容量> <目录>`

缩容：`lvreduce -L -<容量> <目录>`

6. 如何通过systemd设置实现在网络连通时运行一个指定脚本，在网络断开时运行另一个脚本？
```
systemctl cat systemd-networkd.service
systemctl daemon-reload
system
```
![](img\system1.jpg)
![](img\system2.jpg)

7. 如何通过systemd设置实现一个脚本在任何情况下被杀死之后会立即重新启动？实现杀不死？
```
vim /usr/lib/systemd/system/foo.service
```
修改配置文件[service]区块，将restart设置为always：`Restart = always`

重新加载配置文件：`sudo systemctl daemon-reload`

重新启动服务：`sudo systemctl restart ××××`