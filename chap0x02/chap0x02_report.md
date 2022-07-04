# Homework 2
|      版本    | ubuntu                 | CentOS     |
| ---        |    ----              |          ---   |
| 安装应用      | ```apt install```        | ```yum install -y```   |
| 卸载应用      |```sudo apt-get --purge remove tshark```        | ```yum remove ```     |
|查看安装路径|```dpkg -L tmux```|```rpm -qal \| grep ``` |
|查找文件名|```sudo find / -name '*666*'```|``` find / -name '*666*'```|
|查找文件内容|```sudo grep -rn "666" ./ --exclude=*.cast```|```find . \| xargs grep -ri '666'```|
|gzip压缩与解压缩|```gzip```<br>```gzip -d```|```gzip```<br>```gzip -d```|
|bzip2压缩与解压缩|```bzip2```<br>```bzip2 -d test.bz2```|```bzip2```<br>```bzip2 -d  test.bz2```|
|zip压缩与解压缩|```zip test.zip test ```<br>```unzip```|```zip```<br>```unzip -o```|
|tar压缩与解压缩|```tar -cvf```<br>```tar -xvf```|```tar -cvf```<br>```tar -xvf```|
|7z压缩与解压缩|```7z a -t7z -r```<br>```7z x 1.7z -r -o./```|```7za a -t7z ```<br>```7za x 1.7z -r -o./```|
|rar压缩与解压缩|```rar a```<br>```unrar e```|```**rar a```<br>```unrar e```|

# 一、【软件包管理】
在目标发行版上安装 tmux 和 tshark ；查看这 2 个软件被安装到哪些路径；卸载 tshark ；验证 tshark 卸载结果
1. 安装 tmux 和 tshark
安装 tmux：使用命令`sudo apt install tmux`<br />安装tshark：使用命令`sudo apt install tshark`
2. 查看两个软件被安装到了哪些路径
tmux：使用命令`dpkg -L tmux`或`sudo find / -name tmux`
[![asciicast](https://asciinema.org/a/wjlP7zolYidnGeQl1jPbqVTSQ.svg)](https://asciinema.org/a/wjlP7zolYidnGeQl1jPbqVTSQ)
tshark：使用命令`dpkg -L tshark`或`sudo find / -name tshark`
[![asciicast](https://asciinema.org/a/833uAkuMBskA3Q388QZO9dm4H.svg)](https://asciinema.org/a/833uAkuMBskA3Q388QZO9dm4H)
3. 卸载 tshark，验证 tshark 卸载结果
sudo apt purge tshark
[![asciicast](https://asciinema.org/a/A3MXsKOfd9oiVafxRkUW9KSoh.svg)](https://asciinema.org/a/A3MXsKOfd9oiVafxRkUW9KSoh)

# 二、【文件管理】
复制以下 shell 代码`cd /tmp && for i in $(seq 0 1024);do dir="test-$RANDOM";mkdir "$dir";echo "$RANDOM" > "$dir/$dir-$RANDOM";done`到终端运行，在目标 Linux 发行版系统中构造测试数据集，然后回答以下问题：
1. 找到 /tmp 目录及其所有子目录下，文件名包含 666 的所有文件
使用命令`sudo find / -name '*666*'`

2. 找到 /tmp 目录及其所有子目录下，文件内容包含 666 的所有文件
使用命令`sudo grep -rn "666" ./ --exclude=*.cast`
[![asciicast](https://asciinema.org/a/KgPxaGOM6lD6Vesk7DCkQvahr.svg)](https://asciinema.org/a/KgPxaGOM6lD6Vesk7DCkQvahr)

# 三、【文件压缩与解压缩】
练习课件中 文件压缩与解压缩 一节所有提到的压缩与解压缩命令的使用方法
1. 安装：使用命令`sudo apt install``sudo apt install tar``sudo apt-get install p7zip-full``sudo apt install rar``sudo apt install unrar`
2. 使用vi编辑器创建文本文件linux.txt，进行压缩与解压缩操作
[![asciicast](https://asciinema.org/a/WlaMk4Nhid8p05Vs1JBwhLvnS.svg)](https://asciinema.org/a/WlaMk4Nhid8p05Vs1JBwhLvnS)



# 四、【跟练】 
子进程管理实验
[![asciicast](https://asciinema.org/a/eU4RnK8mh8C1nMGVRigpE0hp0.svg)](https://asciinema.org/a/eU4RnK8mh8C1nMGVRigpE0hp0)

# 五、【硬件信息获取】
目标系统的 CPU、内存大小、硬盘数量与硬盘容量
1. 查看cpu型号
`cat /proc/cpuinfo | grep 'model name' | uniq`
2. 查看内存大小
`cat /proc/meminfo head -n 16`
3. 查看硬盘数量与大小
`df -h`