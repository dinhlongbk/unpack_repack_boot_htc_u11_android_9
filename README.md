cd Magisk-v19.4/x86

copy boot.img to here
cp ../../../kernel_orig/boot.img ./

# unpack
./magiskboot unpack boot.img
ls -la
total 126256
drwxrwxr-x 2 dinhlongbk dinhlongbk     4096 Apr 29 09:43 .
drwxrwxr-x 7 dinhlongbk dinhlongbk     4096 Apr 29 09:41 ..
-rw-r--r-- 1 dinhlongbk dinhlongbk 67108864 Apr 29 09:43 boot.img
-rw-r--r-- 1 dinhlongbk dinhlongbk 33171470 Apr 29 09:44 kernel
-rw-r--r-- 1 dinhlongbk dinhlongbk 19248388 Apr 29 09:43 kernel_dtb
-rwxr-xr-x 1 dinhlongbk dinhlongbk   448520 Aug 14  2016 magiskboot
-rwxr-xr-x 1 dinhlongbk dinhlongbk   576672 Aug 14  2016 magiskinit
-rwxr-xr-x 1 dinhlongbk dinhlongbk   576672 Aug 14  2016 magiskinit64
-rw-r--r-- 1 dinhlongbk dinhlongbk  8137060 Apr 29 09:43 ramdisk.cpio



copy and replace kernel: 
cp ../../../source_kernel_htc_ocn_android_9/arch/arm64/boot/Image.lz4-dtb kernel
# repack
./magiskboot repack boot.img

ls -la
total 180000
drwxrwxr-x 2 dinhlongbk dinhlongbk     4096 Apr 29 09:45 .
drwxrwxr-x 7 dinhlongbk dinhlongbk     4096 Apr 29 09:41 ..
-rw-r--r-- 1 dinhlongbk dinhlongbk 67108864 Apr 29 09:43 boot.img
-rw-r--r-- 1 dinhlongbk dinhlongbk 33171470 Apr 29 09:44 kernel
-rw-r--r-- 1 dinhlongbk dinhlongbk 19248388 Apr 29 09:43 kernel_dtb
-rwxr-xr-x 1 dinhlongbk dinhlongbk   448520 Aug 14  2016 magiskboot
-rwxr-xr-x 1 dinhlongbk dinhlongbk   576672 Aug 14  2016 magiskinit
-rwxr-xr-x 1 dinhlongbk dinhlongbk   576672 Aug 14  2016 magiskinit64
-rw-r--r-- 1 dinhlongbk dinhlongbk 55033856 Apr 29 09:45 new-boot.img
-rw-r--r-- 1 dinhlongbk dinhlongbk  8137060 Apr 29 09:43 ramdisk.cpio



# flash
adb reboot download
fastboot flash boot new-boot.img
fastboot reboot