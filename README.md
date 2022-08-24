# Tutorial to flash Redmi AX6

Applications needed
1. [WinSCP](https://winscp.net/eng/download.php)
2. [Putty](https://www.putty.org/)

### Step 1:
1. Open WinSCP connect to router IP Address with **SCP** (File Protocol)
2. Copy [a6minbib.bin](https://github.com/solomonricky/AX6/raw/main/a6minbib.bin) into Redmi AX6's /tmp folder
3. Open Putty, enter router IP Address and click OPEN
4. Type these two commands below:
```
. /lib/upgrade/platform.sh

switch_layout boot; do_flash_failsafe_partition a6minbib "0:MIBIB"
```
5. Done the commands, reboot Redmi AX6 with unplug power

### Step 2:
1. Open WinSCP connect to router IP Address with **SCP** (File Protocol)
2. Copy [openwrt-ipq807x-generic-redmi_ax6-squashfs-nand-factory.ubi](https://github.com/solomonricky/AX6/raw/main/openwrt-ipq807x-generic-redmi_ax6-squashfs-nand-factory.ubi) into Redmi AX6's /tmp folder
3. Open Putty, enter router IP Address and click OPEN
4. Type these three commands below:
```
ubiformat /dev/mtd13 -y -f /tmp/

openwrt-ipq807x-generic-redmi_ax6-squashfs-nand-factory.ubi

fw_setenv flag_last_success 1

fw_setenv flag_boot_rootfs 1
```
5. Type ```reboot``` on Putty
