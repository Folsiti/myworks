## 1.GPU驱动程序

### 安装途径：

ubuntu自带软件与更新--附加驱动470版本

```
NVIDIA-SMI has failed because it couldn't communicate with the NVIDIA driver. 
Make sure that the latest NVIDIA driver is installed and running.
```

### 出现问题：

大概率是Linux内核的问题，目前的内核是5.4.0-42

## 2.系统时间不同步

在使用ubuntu后再换回Windows后系统时间会被改变，造成一些软件无法连接至服务器的问题（如steam、quickq）

### 解决方案

在终端中输入`timedatectl set-local-rtc 1`

输入 `timedatectl`命令，可以看到 `RTC in local TZ: yes`



