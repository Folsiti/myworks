# 一.安装Ubuntu

#### 1.前言

> 在去年底我已经成功安装ubuntu，但是在今年6月因操作失误，在BIOS误将整个电脑文件删除，随后重装了Windows系统。

#### 2.步骤

##### ①烧录u盘

从官网下载Ubuntu18.0.4的iso镜像文件，并使用rufes软件将其烧录至u盘

##### ②第一次尝试

因为我电脑储存空间有限便想把系统装到我一个空的32G u盘上，在安装界面英文只检测到我唯一的一个U盘，便直接快速安装。很快便爆出了错误：ext4文件系统创建失败。我想是不是我脸黑失败，又重新试了几次，但也毫不意外地出现了同样的错误。

##### ②第二次尝试

我向百度求助，我没有采取快速安装的方式，在安装中更改了各种配置分区，但几次下来依然还是失败。

##### ③第三次尝试

我随后从我512G的硬盘中忍痛腾出来了80G的空间，再次进入安装界面时，我忽然间发现系统根本没有发现我的硬盘。我随即插入了U盘，U盘可以被识别。我在百度上终于找到了原因：英特尔快速储存技术RST。我了解到如果要安装双系统，就必须放弃RST选择AHCI。在BIOS中我选择了AHCI，安装过程中正常显示512G硬盘，接下来的都很顺利。随后该配置win10了，这里我结合自己情况和网上的方法：

​		(1)因为安装好Ubuntu后我的系统仍处于AHCI，如果此时打开Windows会打不开，因此我将AHCI先暂时改为了RST。

​		(2)进入Windows，此时Windows无法正常运行，但可以进入带cmd的安全模式，在这个安全模式中输入：`bcdedit /set {current} safeboot minimal`随后打`exit`退出安全模式并关机。

​		(3)若此时直接进入Windows，是可以正常运行的，但不能正常运行Ubuntu。因此需要再次进入BIOS把RST改为AHCI，然后再进入Windows，这时系统会自动进入安全模式。打开cmd输入`bcdedit /deletevalue {current} safeboot`，关机。之后电脑就可以在AHCI储存模式下打开两个系统了。

# 二.Ubuntu中一些软件的安装（git、Typora、输入法）

#### 1.前言

> 我安装了好几个软件，针对特殊性，我挑了这三个具有代表性的。



#### 2.git（命令行）

从git的官网来看它有很多东西，只选择Ubuntu的即可。官网的安装是通过终端输入实现，但对于这几个命令我的权限都不够，都需要在命令前面或分号加`sudo`。剩下的配置过程和Windows下的差别不大。

#### 3.Typora（应用商店）

一开始我去了Typora的官网，按照官网的步骤安装，但无奈网速太慢，选择放弃。后来在Ubuntu自带的应用商店中找到了typora，很方便的就一步到位。

#### 4.搜狗输入法（命令的deb包安装）

前一部分是根据官网的步骤来的，需要Ubuntu中安装过fcitx。通常的deb双击点开就可以安装了，也可以通过命令安装。安装方式：`sudo dpkg -i xxx.deb`，如果提示缺失就可以用`sudo apt -f install`解决依赖性问题。

