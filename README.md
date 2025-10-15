# Smarthome
开源一款使用RK3308BS做主控，系统用linux，应用层使用LVGL开的智慧中控屏幕

01-HW，目录为硬件设计目录，里面包含原理图和PCB源文件；

02-SW  目录为linux驱动文件，下载地址。下载后需要Linux环境进行解压；

03-lvgl_16_91, 是16位智能控制面板的应用层源文件。

04-my_lvgl  是中控屏应用层源文件。

以上设计硬件相同，更换不同的应用层 可实现中控屏和16位按键中控屏幕
应用LVGL代码放置在路径如下，如果有更新替换后编译即可
RK3308BS/media/jin_RK/LVGL/my_lvgl

一、实现步骤如下：
1. 在linux环境下进行解压：
   
在下文件根目录下，执行命令：

tar xvf rk3308bs-250504.tar.gz  -C 3308BS

目录下会出现一个3308BS文件夹 文件命自己可更改

3. 执行命令： build.sh

完成编译后执行SDK根目录下的mkfirmware.sh脚本生成固件

$ ./mkfirmware.sh

所有烧写所需的镜像将都会拷贝于rockdev目录。

**********************************Uboot 编译**********************************

RK3308平台命令

cd u-boot

./make.sh evb-rk3308

编译完，会生成trust.img、rk3308_loader_v1.17.101.bin、uboot.img三个镜像文件。

RK3308 32bit编译

cd u-boot

*********************************Kernel编译************************************

./make.sh evb-aarch32-rk3308
Kernel编译

cd kernel

make rk3308_linux_defconfig 

make rk3308-evb-dmic-i2s-v10.img

编译kernel 需要选择对应的板级配置文件

******************************Buildroot编译 先运行******************************

$ source buildroot/build/envsetup.sh

如选择rockchip_rk3308_release，输入对应序号1。

$make
rockchip_rk3308_bs_release



