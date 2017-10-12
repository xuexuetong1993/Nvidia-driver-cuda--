# Nvidia-driver-cuda--

1.首先按照NVIDIA document：http://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html#post-installation-actions
上的规范 完成post-install

2.禁止掉nouveau 开源驱动：
查看是不是成功禁止掉开源驱动
$lsmod | grep nouveau
新建文件
sudo gedit /etc/modprobe.d/blacklist-nouveau.conf
将下面两行复制进去保存：
blacklist nouveau
options nouveau modeset=0
运行重新生成kernel inintramfs
$ sudo dracut --force

联网后进入下一步

3.安装驱动：

在你的用户登录界面按ctrl+alt+F1进入tty模式
输入你的账户名和密码
依次运行如下语句：
sudo apt-get purge nvidia-*
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt-get update
sudo apt-get install nvidia-367（根据官网给的推荐选择最新的驱动）
reboot //重启

4.安装cuda:
cuda官网下载 cuda-toolkit  runfile
挪到 Document或者Downloader下面（自己可以找到的位置）
给文件权限：
$sudo chomod a+x cuda------(文件名)
关掉桌面环境：
$sudo service lighdm stop
$cd /Document
$sudo ./cuda----
选择跳过 第一步的驱动安装 然后一直yes，location 选择默认（enter）即可。
安装成功之后添加一下PATH 重启即可





