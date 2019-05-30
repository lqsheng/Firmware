#1.gcc-arm-eabi升级至7解决编译错误
下载:https://developer.arm.com/open-source/gnu-toolchain/gnu-rm/downloads
然后执行以下命令(其实就是将解压后的文件夹bin路径加到PATH环境变量中,因此若曾经安装过gcc-arm-none-eabi,注意前往~/.profile删除,此外,在进行这些操作前需按dev.px4.io教程所述卸载UBUNTU自带的gcc-arm-none-eabi):
tar -jxf gcc-arm-none-eabi-5_4-2016q2-20160622-linux.tar.bz2
exportline="export PATH=$HOME/gcc-arm-none-eabi-5_4-2016q2/bin:\$PATH"
if grep -Fxq "$exportline" ~/.profile; then echo nothing to do ; else echo $exportline >> ~/.profile; fi
. ~/.profile

#2.修改src/modules/mavlink/mavlink_main.cpp中MAVLINK_MODE_ONBOARD里HIGHRES_IMU到200HZ
