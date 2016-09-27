# Linux系统连接Android设备

一般来说，使用Ubuntu、Arch这些发行版，都会默认对Android设备有良好的支持，但其实支持的力度不是太好的，比如你想用`adb sideload`的时候就会发现系统提示错误。所以，要实现对Android的全面支持还是要我们自己花点功夫改下Linux系统配置才行。

## UDEV

一般的Linux发行版都是用UDEV来管理USB设备的，比如我现在使用的Ubuntu。因此只要对udev配置就可以了，具体步骤如下：

1. 确认系统登陆账号属于`plugdev`用户组，不清楚的话键入
  `groups`
  从列表上查看用户组信息，如果没有看到`plugdev`的话，那就要加入该组了：
  `sudo gpasswd -a <username> plugdev  # 其中username为你的用户名`
2. 创建`/etc/udev/rules.d/51-android.rules`配置文件
3. 在`/etc/udev/rules.d/51-android.rules`写入Android设备相关配置

## UDEV参考配置

Google官方的配置只有它出的Nexus系列的，所以我这里参考了[Cyanogenmod][0]的：

```sh
#Acer
SUBSYSTEM=="usb", ATTR{idVendor}=="0502", MODE="0664", GROUP="plugdev"
#ASUS
SUBSYSTEM=="usb", ATTR{idVendor}=="0b05", MODE="0664", GROUP="plugdev"
#Dell
SUBSYSTEM=="usb", ATTR{idVendor}=="413c", MODE="0664", GROUP="plugdev"
#Foxconn
SUBSYSTEM=="usb", ATTR{idVendor}=="0489", MODE="0664", GROUP="plugdev"
#Fujitsu & Fujitsu Toshiba
SUBSYSTEM=="usb", ATTR{idVendor}=="04c5", MODE="0664", GROUP="plugdev"
#Garmin-Asus
SUBSYSTEM=="usb", ATTR{idVendor}=="091e", MODE="0664", GROUP="plugdev"
#Google
SUBSYSTEM=="usb", ATTR{idVendor}=="18d1", MODE="0664", GROUP="plugdev"
#Haier
SUBSYSTEM=="usb", ATTR{idVendor}=="201e", MODE="0664", GROUP="plugdev"
#Hisense
SUBSYSTEM=="usb", ATTR{idVendor}=="109b", MODE="0664", GROUP="plugdev"
#HTC
SUBSYSTEM=="usb", ATTR{idVendor}=="0bb4", MODE="0664", GROUP="plugdev"
#Huawei
SUBSYSTEM=="usb", ATTR{idVendor}=="12d1", MODE="0664", GROUP="plugdev"
#K-Touch
SUBSYSTEM=="usb", ATTR{idVendor}=="24e3", MODE="0664", GROUP="plugdev"
#KT Tech
SUBSYSTEM=="usb", ATTR{idVendor}=="2116", MODE="0664", GROUP="plugdev"
#Kyocera
SUBSYSTEM=="usb", ATTR{idVendor}=="0482", MODE="0664", GROUP="plugdev"
#Lenovo
SUBSYSTEM=="usb", ATTR{idVendor}=="17ef", MODE="0664", GROUP="plugdev"
#LG
SUBSYSTEM=="usb", ATTR{idVendor}=="1004", MODE="0664", GROUP="plugdev"
#Motorola
SUBSYSTEM=="usb", ATTR{idVendor}=="22b8", MODE="0664", GROUP="plugdev"
#MTK
SUBSYSTEM=="usb", ATTR{idVendor}=="0e8d", MODE="0664", GROUP="plugdev"
#NEC
SUBSYSTEM=="usb", ATTR{idVendor}=="0409", MODE="0664", GROUP="plugdev"
#Nook
SUBSYSTEM=="usb", ATTR{idVendor}=="2080", MODE="0664", GROUP="plugdev"
#Nvidia
SUBSYSTEM=="usb", ATTR{idVendor}=="0955", MODE="0664", GROUP="plugdev"
#OTGV
SUBSYSTEM=="usb", ATTR{idVendor}=="2257", MODE="0664", GROUP="plugdev"
#Pantech
SUBSYSTEM=="usb", ATTR{idVendor}=="10a9", MODE="0664", GROUP="plugdev"
#Pegatron
SUBSYSTEM=="usb", ATTR{idVendor}=="1d4d", MODE="0664", GROUP="plugdev"
#Philips
SUBSYSTEM=="usb", ATTR{idVendor}=="0471", MODE="0664", GROUP="plugdev"
#PMC-Sierra
SUBSYSTEM=="usb", ATTR{idVendor}=="04da", MODE="0664", GROUP="plugdev"
#Qualcomm
SUBSYSTEM=="usb", ATTR{idVendor}=="05c6", MODE="0664", GROUP="plugdev"
#SK Telesys
SUBSYSTEM=="usb", ATTR{idVendor}=="1f53", MODE="0664", GROUP="plugdev"
#Samsung
SUBSYSTEM=="usb", ATTR{idVendor}=="04e8", MODE="0664", GROUP="plugdev"
#Sharp
SUBSYSTEM=="usb", ATTR{idVendor}=="04dd", MODE="0664", GROUP="plugdev"
#Sony
SUBSYSTEM=="usb", ATTR{idVendor}=="054c", MODE="0664", GROUP="plugdev"
#Sony Ericsson
SUBSYSTEM=="usb", ATTR{idVendor}=="0fce", MODE="0664", GROUP="plugdev"
#Teleepoch
SUBSYSTEM=="usb", ATTR{idVendor}=="2340", MODE="0664", GROUP="plugdev"
#Toshiba
SUBSYSTEM=="usb", ATTR{idVendor}=="0930", MODE="0664", GROUP="plugdev"
#ZTE
SUBSYSTEM=="usb", ATTR{idVendor}=="19d2", MODE="0664", GROUP="plugdev"
```

[0]: https://wiki.cyanogenmod.org/w/UDEV

