## Usage

build kernel image:

	build/mk-kernel.sh rk3288-evb
    
build u-boot image:

	build/mk-uboot.sh rk3288-evb
    
build rootfs image:

	follow readme in rk-rootfs-build

build one system image:

	build/mk-image.sh -c rk3288 -t system -s 4000 -r rk-rootfs-build/linaro-rootfs.img

update image: 

	eMMC: build/flash_tool.sh   -c rk3288 -p system  -i  out/system.img
	sdcard: build/flash_tool.sh -c rk3288  -d /dev/sdb -p system  -i  out/system.img 

### Tips
* You must boot into maskrom to flash the eMMC. Booting into rkusb mode will not work.
  * An easy way to enter maskrom is by erasing the eMMC and rebooting.
* Provide the chip name for `-c` parameters, _not_ the board name! (e.g. rk3288 instead of rk3288-evb).
