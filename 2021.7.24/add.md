## 显卡驱动问题，解决！！！

#### 1.更改内核的方式

我通过下面的指令安装了低版本内核：

`sudo apt install linux-image-<version>-generic`

`sudo apt install linux-headers-<version>-generic`

#### 2.选择内核

重启，开机时选择ubuntu高级选项，这时选择新安装的内核。

​		第一次，选择4.15.0-130：由于无线网卡、蓝牙驱动缺失，又懒得去接家里网线，直接放弃。

​		第二次，选择5.3.0-26：无线网卡、蓝牙驱动正常，但nvidia-smi还是报错

​		第三次，依然是5.3.0-26：我注意到BIOS应该在security boot为disabled的状态下才能装NVIDIA驱动，于是在BIOS中修改后进入系统，但还是失败。

​		第四次，还是5.3.0-26：后面我发现安装缺少了一个步骤，需要以下命令：

​		`sudo dkms install -m nvidia -v <version>` 

​		(version为显卡驱动版本，我用的是460.91.03)

​		解决了，niceeeeeee！

#### 3.测试

5.3.0版本可以用460的驱动，那么5.4.0是不是就可以用4.7.0的驱动了？我切换到了4.5.0-80的内核，发现在上述中第四步的命令报错，找不到文件，那么这也就是说4.7.0的驱动不完整。随后再次更换驱动版本为460.91.03，运行nvidia-smi报错。 

因为我刚安装ubuntu时，其内核版本为5.4.0-42，所以在新的一轮尝试中选择了5.4.0-42，这回nvidia-smi正常

#### 4.总结

​	（1从5.x.x的内核回到4.x.x的内核回有驱动程序的缺失。

​	（2安装显卡驱动要确保BIOS中的security boot为disabled。（虽然这会影响电脑的安全性）

​	（3目前5.4.0-80太新，显卡驱动不兼容。

​	（4遇到几乎所有网上的方法都没有用的时候，一定要从底层开始检查。

​	（5上图

​		![](https://github.com/Folsiti/myworks/blob/main/img/pic.png)

