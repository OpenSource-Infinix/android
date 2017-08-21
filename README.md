# Compiling and Flashing
</br>
1.Download the source code package
Download the package X556_OPEN_SOURCE_DEV.tar.gz to the Linux server.

2.Uncompressing
 Enter the following command in the root directory of the X556_OPEN_SOURCE_DEV.tar.gz
 ```shell
$ tar xzvf X556_OPEN_SOURCE_DEV.tar.gz
```
3.Build version </br>
**[Prepare the environment]**
```shell
$ source build/envsetup.sh
```
**[Set complier options for the project]**
</br>Type the following command in order to show the complier options
```shell
$ lunch
```
**[Choose the applicable complier option] Options:**
</br>① type 22, build the full_rlk6737m_open_n-eng
</br>② type 23, build full_rlk6737m_open_n-user
</br>③ type 24, build full_rlk6737m_open_n-userdebug
**[Set environment variables]**
```shell
$ source mbldenv.sh
```
**[Start build the project]**
```shell
$ make -j24 2>&1 | tee build.log
```

4.Flashing
**[Prepare]
Enter the developer mode, select OEM unlocking and USB debugging
[Enter fastboot mode]
 Type the following command to put the phone on fastboot mode**
 ```shell
$ adb reboot bootloader
```
**[Unlock the bootloader]**
Type the following command to unlock the bootloader
```shell
$ fastboot flashing unlock
```
then follow the prompts on the screen, unlock the phone.
**[flash boot and system]**
Type the following command after unlocking the phone successfully
```shell
$fastboot flash boot boot.img
$fastboot flash system system.img
```
Type the command if you want to repartition the hard disk
```shell
$ fastboot flash userdata userdata.img
```
**[Reboot the phone]**
Type the command to reboot the phone
```shell
$fastboot reboot
```