## MacOS High Sierra Hackintosh EFI for MSI X470 + AMD R5 3600X + GTX 750TI

### 配置清单

|   类型    |           型号           |
| :-------: | :----------------------: |
|    CPU    |        AMD 3600X         |
|   主版    | MSI X470 GAMING PLUS MAX |
|   显卡    |        GTX 750TI         |
|   内存    |       DDR4 3200 8G       |
| 网卡&蓝牙 |      BCM943224 PCIE      |

### OS & GPU Driver

​	750ti显卡为Maxwell架构，最高可驱动的macOS系统为macOS 10.13.6 HighSierra，且必须安装对应版本的NVIDIA WebDriver 驱动补丁方可驱动，亲测10.13.6(17G65)版本可以通过安装tools文件夹中[NVIDIA WebDriver Updater]可自动检测到对应驱动对完成驱动安装，在测试过程中系统高于10.13.6(17G65版本)的系统如10.13.6(17G66)、10.13.6(17G2112)等版本均未找到对应版本的驱动。

macOS引导版镜像免费下载地址：[/ISO/MacOS/10.13/ (dtops.cc)](https://mirrors.dtops.cc/ISO/MacOS/10.13/)

### 引导

​	下载的macOS镜像自带Clover引导，测试过程中体验不佳、安装失败。后更换为目前更为主流的OC引导方式，OpenCore版本0.66，tools文件中[OpenCore.Configurator.2.29.0.0__HeiPG.cn.dmg](https://github.com/huq7197/MsiX470-AMD3600X-750TI-HighSierra/blob/main/tools/OpenCore.Configurator.2.29.0.0__HeiPG.cn.dmg) 为OpenCore 0.66对应的OpenCore Configurator工具，解压密码为：**heipg.cn**

​	引导启动的GUI界面等待时间设置为10s，且已隐藏了辅助条目，可自行开启或调整。



​	软件来源：[黑苹果星球-分享Mac的精彩世界 (heipg.cn)](https://heipg.cn/)

### 无线网卡 & 蓝牙

​	Broadcom芯片相较于Intel芯片网卡对macOS拥有原生驱动支持，但是比Intel网卡贵。BCM943224无线网卡最高支持10.15 Catalina系统，且向下兼容。该网卡带有2.4G+5G双频300Mbps WLAN和4.0蓝牙，通过转接卡连接后直接插在PCIE接口，通过连接线将蓝牙连接到主版USB接口，在macOS 10.13.6系统下该网卡和蓝牙免驱。注意在10.15 Catalina系统下不免驱，需要安装相应驱动。

​	测试过程中在不添加任何驱动和补丁的情况下，Wi-Fi和Bluetooth均可正常使用，但隔空投送功能不能用，在Kext 中添加  IO80211HighSierra.kext和AirportBrcmFixup.kext后，并在OpenCore Configurator中启用，上传的efi文件为未启用状态。



​	添加补丁之后隔空投送功能可正常使用，经测试iPhone、iPad与该Mac均可双向正常隔空投送。
