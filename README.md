![64-bit RISC-V Sophgo SG2000 (T-Head C906 / Milk-V Duo S)](https://lupyuen.github.io/images/sg2000-title.jpg)

[(Watch the Demo on YouTube)](https://youtu.be/24azql1rzc4?si=rMId8LWVEM4_Wj4D)

# Apache NuttX RTOS on 64-bit RISC-V Sophgo SG2000 (T-Head C906 / Milk-V Duo S)

[![Daily Build of NuttX for SG2000](https://github.com/lupyuen/nuttx-sg2000/actions/workflows/sg2000.yml/badge.svg)](https://github.com/lupyuen/nuttx-sg2000/actions/workflows/sg2000.yml)
[![Daily Test of NuttX for SG2000](https://github.com/lupyuen/nuttx-sg2000/actions/workflows/sg2000-test.yml/badge.svg)](https://github.com/lupyuen/nuttx-sg2000/actions/workflows/sg2000-test.yml)

Read the articles...

- ["Apache NuttX RTOS on Sophgo SG2000 RISC-V SoC (Milk-V Duo S SBC)"](https://lupyuen.github.io/articles/sg2000)

- ["Daily Automated Testing for Milk-V Duo S RISC-V SBC (IKEA TRETAKT / Apache NuttX RTOS)"](https://lupyuen.github.io/articles/sg2000a)

- ["RISC-V Emulator for Sophgo SG2000 SoC (Pine64 Oz64 / Milk-V Duo S)"](https://lupyuen.github.io/articles/sg2000b)

- ["Test Bot for Pull Requests ... Tested on Real Hardware (Apache NuttX RTOS / Oz64 SG2000 RISC-V SBC)"](https://lupyuen.org/articles/testbot.html)

__UPDATE:__ Sophgo SG2000 is officially supported by NuttX Mainline! (Including Milk-V Duo S and Pine64 Oz64)

- ["NuttX Mainline now supports SG2000"](https://lupyuen.github.io/articles/sg2000#appendix-nuttx-mainline-now-supports-sg2000)

- ["NuttX for Milk-V Duo S"](https://nuttx.apache.org/docs/latest/platforms/risc-v/sg2000/boards/milkv_duos/index.html)

- ["NuttX for Pine64 Oz64"](https://lupyuen.github.io/articles/sg2000#appendix-apache-nuttx-rtos-for-pine64-oz64-sbc)

Here's how everything got started...

<hr>

64-bit RISC-V Sophgo SG2000 SoC ... Will it boot Apache NuttX RTOS? 🤔 (T-Head C906 / Milk-V Duo S)

- [SG2000 Overview](https://www.cnx-software.com/2024/02/07/sophgo-sg2000-sg2002-ai-soc-features-risc-v-arm-8051-cores-android-linux-freertos/)

- [SG2000 Reference Manual](https://github.com/sophgo/sophgo-doc/releases)

Let's find out!

_Is this a sponsored review?_

I was given a Milk-V Duo S, and I bought another. So it cancels out, I guess?

_Why are we doing all this?_

1.  We hear that there will be plenty of interesting new SBCs based on Sophgo SG2000 and SG2002. Perfect for NuttX!

1.  NuttX has been ported from QEMU RISC-V to Star64 JH7110 to Ox64 BL808 and now Sophgo SG2000. Let's find the most efficient way to port NuttX to new RISC-V Devices!

![Sophgo SG2000 RISC-V SoC](https://lupyuen.github.io/images/sg2000-soc.jpg)

# NuttX Automated Daily Build for SG2000

NuttX for SG2000 is now built automatically every day via GitHub Actions.

The Daily Releases are available here...

- [nuttx-sg2000/releases](https://github.com/lupyuen/nuttx-sg2000/tags)

  (Skip the Special Builds)

[nuttx.hash](https://github.com/lupyuen/nuttx-sg2000/releases/download/nuttx-sg2000-2024-06-18/nuttx.hash) contains the Commit Hash of the NuttX Kernel and NuttX Apps repos...

```text
NuttX Source: https://github.com/apache/nuttx/tree/28ae3b38499c6c7bac0d432658da263b9eab2981
NuttX Apps: https://github.com/apache/nuttx-apps/tree/00f98947786892eaabf60b2e61fad553aee1c36c
```

The GitHub Actions Workflow is here...

- [sg2000.yml](https://github.com/lupyuen/nuttx-sg2000/blob/main/.github/workflows/sg2000.yml)

We are now running Daily Automated Testing of NuttX on a Real Milk-V Duo S SBC...

1.  Download the Daily Build to TFTP Server

1.  Power on our SBC with an [IKEA Smart Power Plug via Home Assistant](https://github.com/lupyuen2/autotest-nuttx-sg2000#control-our-sbc-with-an-ikea-smart-power-plug-and-home-assistant)

1.  Our SBC boots the Daily Build over TFTP

1.  Capture the Automated Testing Log and write to the Release Notes

    [(See the Automated Test Logs)](https://github.com/lupyuen/nuttx-sg2000/releases)

    [(See the Automated Test Script)](https://github.com/lupyuen2/autotest-nuttx-sg2000)

We are also running Daily Automated Testing with an SG2000 Emulator (in GitHub Actions)...

- [See the Automated Test Logs](https://github.com/lupyuen/nuttx-sg2000/actions/workflows/sg2000-test.yml)

- [See the GitHub Actions Workflow](https://github.com/lupyuen/nuttx-sg2000/blob/main/.github/workflows/sg2000-test.yml)

- ["Emulate Sophgo SG2000 SoC / Milk-V Duo S SBC with TinyEMU RISC-V Emulator"](https://github.com/lupyuen2/sg2000-emulator)

# Sophgo SG2000 RISC-V SoC

Read the article...

- ["Apache NuttX RTOS on Sophgo SG2000 RISC-V SoC (Milk-V Duo S SBC)"](https://lupyuen.github.io/articles/sg2000)

__Sophgo SG2000 SoC__ has a fascinating mix of 64-bit RISC-V Cores (Arm too)...

- __Main Processor:__ 64-bit RISC-V Core

  __T-Head C906__ _(1.0 GHz)_

  (For NuttX and Linux)

- __Co-Processor:__ 64-bit RISC-V Core

  __T-Head C906__ _(700 MHz)_

  (No Cache)

- __Alt-Main Processor:__ 64-bit Arm Core

  __Cortex-A53__ _(1.0 GHz)_

Plus a __Low-Power 8051 MCU__ (for wakeup duties) and a __Tensor Processing Unit__ (for image recognition, not LLM)

![Sophgo SG2000 RISC-V SoC](https://lupyuen.github.io/images/sg2000-arch.jpg)

_Whoa RISC-V AND Arm CPUs in a single SoC?_

Actually there's a __Hardware Switch__ that selects the Main CPU: __RISC-V OR Arm__.

(Don't let yer pet hamster flip it... It will get super frustrating!)

![Milk-V Duo S](https://lupyuen.github.io/images/sg2000-board.jpg)

# Boot Milk-V Duo S without MicroSD

Read the article...

- ["Apache NuttX RTOS on Sophgo SG2000 RISC-V SoC (Milk-V Duo S SBC)"](https://lupyuen.github.io/articles/sg2000)

_What happens if we boot Milk-V Duo S? Fresh from the box?_

Connect our __USB UART Dongle__ like so (pic above)...

| Milk-V Duo S | USB UART |
|:------------:|:--------:|
| __GND__ (Pin 6)	| __GND__ |
| __TX__ (Pin 8) |	__RX__ |
| __RX__ (Pin 10)	| __TX__ |

[(Source)](https://milkv.io/docs/duo/getting-started/duos#uart-serial-console)

USB UART Dongle must be [__CP2102__](http://sun-light.com.sg/index.php?route=product/product&product_id=2367), it doesn't like [__CH340G__](https://pine64.com/product/serial-console-woodpecker-edition/) 😬

Flip the switch so it's set to "__`RV`__" (RISC-V) instead of "__`Arm`__"...

![Switch to "RV" (RISC-V) instead of "Arm"](https://lupyuen.github.io/images/sg2000-switch.jpg)

Power up the board via the USB-C Port. We should see...

https://gist.github.com/lupyuen/a7c3af98be36dcd5cc5b45f5aadc5d16

```bash
C.SCS/0/0.WD.URPL.USBI.USBEF.BS/EMMC.EMI/25000000/12000000. E:bm_emmc_send_cmd_without_data CMD: 1 INT_STAT: 0x E:bm_emmc_send_cmd_without_data CMD: 0 INT_STAT: 0x E:eMMC init failed, 3
 E:eMMC initializing failed
PS. E:bm_emmc_send_cmd_without_data CMD: 6 INT_STAT: 0x E:load param1 (-5)
 E:Boot failed (8).
 E:RESET:plat/mars/platform.c:114
WD.C.SCS/0/0.WD.URPL.USBI.USBEF.BS/EMMC.EMI/25000000/12000000. E:bm_emmc_send_cmd_without_data CMD: 1 INT_STAT: 0x E:bm_emmc_send_cmd_without_data CMD: 0 INT_STAT: 0x E:eMMC init failed, 3
 E:eMMC initializing failed
```

If we see `B.SCS` instead of `C.SCS`...

https://gist.github.com/lupyuen/d55b77a51ee8b258d6d1c0799770742a

```bash
B.SCS/0/0.WD.URPL.USBI.USBEF.BS/EMMC.EMI/25000000/12000000.
```

Nope we're in Arm Mode! Flip the switch back to RISC-V!

[If we use CH340G](https://pine64.com/product/serial-console-woodpecker-edition/) (instead of [CP2102](http://sun-light.com.sg/index.php?route=product/product&product_id=2367)): UART Output will be garbled (happens on Linux and macOS, maybe Windows too)...

https://gist.github.com/lupyuen/1d5ba1b2a47c110ee7ff265102b1aae5

Milk-V Duo S doesn't ship with U-Boot Bootloader preinstalled in Flash Memory. We'll need U-Boot on MicroSD...

# Boot Linux on Milk-V Duo S

Read the article...

- ["Apache NuttX RTOS on Sophgo SG2000 RISC-V SoC (Milk-V Duo S SBC)"](https://lupyuen.github.io/articles/sg2000)

_Milk-V Duo S won't boot without MicroSD. How now?_

Let's boot __Linux on MicroSD__, thanks to the awesome work by [__Justin Hammond__](https://github.com/Fishwaldo) (Fishwaldo)...

- [__Debian Images for Sophgo SG2000__](https://github.com/Fishwaldo/sophgo-sg200x-debian/releases)

We download the Latest Release for __Milk-V Duo S__ (SG2000)...

- [__duos_sd.img.lz4__](https://github.com/Fishwaldo/sophgo-sg200x-debian/releases/download/v1.2.0/duos_sd.img.lz4)

```bash
$ brew install lz4
$ lz4 ~/Downloads/duos_sd.img.lz4
## TODO: Write duos_sd.img to MicroSD with Balena Etcher

→ ls -l /Volumes/boot
total 17488
-rwxrwxrwx  1 Luppy  staff  3494900 Apr 24 11:33 System.map-5.10.4-20240329-1+
-rwxrwxrwx  1 Luppy  staff   125534 Apr 24 11:33 config-5.10.4-20240329-1+
drwxrwxrwx  1 Luppy  staff     2048 Apr 24 11:33 extlinux
drwxrwxrwx  1 Luppy  staff     2048 Apr 24 11:33 fdt
-rwxrwxrwx  1 Luppy  staff   388608 Apr 24 11:33 fip.bin
-rwxrwxrwx  1 Luppy  staff  4937389 Apr 24 11:33 vmlinuz-5.10.4-20240329-1+

→ ls -l /Volumes/boot/extlinux
total 4
-rwxrwxrwx  1 Luppy  staff  749 Apr 24 11:33 extlinux.conf

→ ls -l /Volumes/boot/fdt
total 4
drwxrwxrwx  1 Luppy  staff  2048 Apr 24 11:33 linux-image-duos-5.10.4-20240329-1+

→ ls -l /Volumes/boot/fdt/linux-image-duos-5.10.4-20240329-1+
total 44
-rwxrwxrwx  1 Luppy  staff  21575 Apr 24 11:33 cv181x_milkv_duos_sd.dtb
```

Here's the Boot Config...

```bash
→ cat /Volumes/boot/extlinux/extlinux.conf
## /boot/extlinux/extlinux.conf
##
## IMPORTANT WARNING
##
## The configuration of this file is generated automatically.
## Do not edit this file manually, use: u-boot-update

default l0
menu title U-Boot menu
prompt 1
timeout 50


label l0
  menu label Debian GNU/Linux trixie/sid 5.10.4-20240329-1+
  linux /vmlinuz-5.10.4-20240329-1+

  fdtdir /fdt/linux-image-duos-5.10.4-20240329-1+/

  append root=/dev/root console=ttyS0,115200 earlycon=sbi root=/dev/mmcblk0p2 rootwait rw

label l0r
  menu label Debian GNU/Linux trixie/sid 5.10.4-20240329-1+ (rescue target)
  linux /vmlinuz-5.10.4-20240329-1+

  fdtdir /fdt/linux-image-duos-5.10.4-20240329-1+/
  append root=/dev/root console=ttyS0,115200 earlycon=sbi root=/dev/mmcblk0p2 rootwait rw single
```

Yep Linux boots OK on Milk-V Duo S! (Together with OpenSBI and U-Boot Bootloader)

https://gist.github.com/lupyuen/01d409b7bde9607a96cd4d460e53330a

```bash
OpenSBI v0.9
   ____                    _____ ____ _____
  / __ \                  / ____|  _ \_   _|
 | |  | |_ __   ___ _ __ | (___ | |_) || |
 | |  | | '_ \ / _ \ '_ \ \___ \|  _ < | |
 | |__| | |_) |  __/ | | |____) | |_) || |_
  \____/| .__/ \___|_| |_|_____/|____/_____|
        | |
        |_|

Platform Name             : Milk-V DuoS
Platform Features         : mfdeleg
Platform HART Count       : 1
Platform IPI Device       : clint
Platform Timer Device     : clint
Platform Console Device   : uart8250
Platform HSM Device       : ---
Platform SysReset Device  : ---
Firmware Base             : 0x80000000
Firmware Size             : 132 KB
Runtime SBI Version       : 0.3

Domain0 Name              : root
Domain0 Boot HART         : 0
Domain0 HARTs             : 0*
Domain0 Region00          : 0x0000000074000000-0x000000007400ffff (I)
Domain0 Region01          : 0x0000000080000000-0x000000008003ffff ()
Domain0 Region02          : 0x0000000000000000-0xffffffffffffffff (R,W,X)
Domain0 Next Address      : 0x0000000080200020
Domain0 Next Arg1         : 0x0000000080080000
Domain0 Next Mode         : S-mode
Domain0 SysReset          : yes

Boot HART ID              : 0
Boot HART Domain          : root
Boot HART ISA             : rv64imafdcvsux
Boot HART Features        : scounteren,mcounteren,time
Boot HART PMP Count       : 16
Boot HART PMP Granularity : 4096
Boot HART PMP Address Bits: 38
Boot HART MHPM Count      : 8
Boot HART MHPM Count      : 8
Boot HART MIDELEG         : 0x0000000000000222
Boot HART MEDELEG         : 0x000000000000b109
...
Debian GNU/Linux trixie/sid duos ttyS0
duos login: 
```

Let's dump the U-Boot Config...

https://gist.github.com/lupyuen/000b55a46336cddf217a589f469d60e2

```bash
U-Boot 2021.10-ga57aa1f2-dirty (May 07 2024 - 08:13:12 +0000) cvitek_cv181x
DRAM:  510 MiB
gd->relocaddr=0x9fbc6000. offset=0x1f9c6000
set_rtc_register_for_power
MMC:   cv-sd@4310000: 0, wifi-sd@4320000: 1
Loading Environment from FAT... mmc1 : finished tuning, code:53
OK
In:    serial
Out:   serial
Err:   serial
Net:   
Warning: ethernet@4070000 (eth0) using random MAC address - 0a:fa:e9:48:cc:c1
eth0: ethernet@4070000
Hit any key to stop autoboot:  0

cv181x_c906# printenv
arch=riscv
baudrate=115200
board=mars
board_name=mars
boot_a_script=load ${devtype} ${devnum}:${distro_bootpart} ${scriptaddr} ${prefix}${script}; source ${scriptaddr}
boot_efi_binary=load ${devtype} ${devnum}:${distro_bootpart} ${kernel_addr_r} efi/boot/bootriscv64.efi; if fdt addr ${fdt_addr_r}; then bootefi ${kernel_addr_r} ${fdt_addr_r};else bootefi ${kernel_addr_r} ${fdtcontroladdr};fi
boot_efi_bootmgr=if fdt addr ${fdt_addr_r}; then bootefi bootmgr ${fdt_addr_r};else bootefi bootmgr;fi
boot_extlinux=sysboot ${devtype} ${devnum}:${distro_bootpart} any ${scriptaddr} ${prefix}${boot_syslinux_conf}
boot_prefixes=/ /boot/
boot_script_dhcp=boot.scr.uimg
boot_scripts=boot.scr.uimg boot.scr
boot_syslinux_conf=extlinux/extlinux.conf
boot_targets=mmc0 dhcp pxe 
bootcmd=run distro_bootcmd || run sdboot || run sdbootauto
bootcmd_dhcp=devtype=dhcp; if dhcp ${scriptaddr} ${boot_script_dhcp}; then source ${scriptaddr}; fi;setenv efi_fdtfile ${fdtfile}; setenv efi_old_vci ${bootp_vci};setenv efi_old_arch ${bootp_arch};setenv bootp_vci PXEClient:Arch:00027:UNDI:003000;setenv bootp_arch 0x1b;if dhcp ${kernel_addr_r}; then tftpboot ${fdt_addr_r} dtb/${efi_fdtfile};if fdt addr ${fdt_addr_r}; then bootefi ${kernel_addr_r} ${fdt_addr_r}; else bootefi ${kernel_addr_r} ${fdtcontroladdr};fi;fi;setenv bootp_vci ${efi_old_vci};setenv bootp_arch ${efi_old_arch};setenv efi_fdtfile;setenv efi_old_arch;setenv efi_old_vci;
bootcmd_mmc0=devnum=0; run mmc_boot
bootcmd_pxe=dhcp; if pxe get; then pxe boot; fi
bootdelay=1
consoledev=ttyS0
cpu=generic
distro_bootcmd=for target in ${boot_targets}; do run bootcmd_${target}; done
efi_dtb_prefixes=/ /dtb/ /dtb/current/
fdt_addr_r=0x81200000
fdtcontroladdr=9f27f810
fdtfile=cv181x_milkv_duos_sd.dtb
fdtoverlay_addr_r=0x81300000
gatewayip=192.168.0.11
ipaddr=192.168.0.3
kernel_addr_r=0x80200000
kernel_comp_addr_r=0x81800000
kernel_comp_size=0x1000000
load_efi_dtb=load ${devtype} ${devnum}:${distro_bootpart} ${fdt_addr_r} ${prefix}${efi_fdtfile}
mmc_boot=if mmc dev ${devnum}; then devtype=mmc; run scan_dev_for_boot_part; fi
netdev=eth0
netmask=255.255.255.0
othbootargs=earlycon=sbi riscv.fwsz=0x80000   loglevel=9
pxefile_addr_r=0x81400000
ramdisk_addr_r=0x84000000
root=root=/dev/mmcblk0p2 rootwait rw
scan_dev_for_boot=echo Scanning ${devtype} ${devnum}:${distro_bootpart}...; for prefix in ${boot_prefixes}; do run scan_dev_for_extlinux; run scan_dev_for_scripts; done;run scan_dev_for_efi;
scan_dev_for_boot_part=part list ${devtype} ${devnum} -bootable devplist; env exists devplist || setenv devplist 1; for distro_bootpart in ${devplist}; do if fstype ${devtype} ${devnum}:${distro_bootpart} bootfstype; then run scan_dev_for_boot; fi; done; setenv devplist
scan_dev_for_efi=setenv efi_fdtfile ${fdtfile}; for prefix in ${efi_dtb_prefixes}; do if test -e ${devtype} ${devnum}:${distro_bootpart} ${prefix}${efi_fdtfile}; then run load_efi_dtb; fi;done;run boot_efi_bootmgr;if test -e ${devtype} ${devnum}:${distro_bootpart} efi/boot/bootriscv64.efi; then echo Found EFI removable media binary efi/boot/bootriscv64.efi; run boot_efi_binary; echo EFI LOAD FAILED: continuing...; fi; setenv efi_fdtfile
scan_dev_for_extlinux=if test -e ${devtype} ${devnum}:${distro_bootpart} ${prefix}${boot_syslinux_conf}; then echo Found ${prefix}${boot_syslinux_conf}; run boot_extlinux; echo SCRIPT FAILED: continuing...; fi
scan_dev_for_scripts=for script in ${boot_scripts}; do if test -e ${devtype} ${devnum}:${distro_bootpart} ${prefix}${script}; then echo Found U-Boot script ${prefix}${script}; run boot_a_script; echo SCRIPT FAILED: continuing...; fi; done
scriptaddr=0x81500000
sdboot=setenv bootargs ${reserved_mem} ${root} ${mtdparts} console=$consoledev,$baudrate $othbootargs;echo Boot from SD dev ${sddev} ...;mmc dev ${sddev} && fatload mmc ${sddev} ${uImage_addr} boot.sd;if test $? -eq 0; then bootm ${uImage_addr}#config-cv181x_milkv_duos_sd;fi;
sdbootauto=cvi_sd_boot;setenv bootargs ${reserved_mem} ${root} ${mtdparts} console=$consoledev,$baudrate $othbootargs;echo Boot from SD dev ${sddev} auto ...;mmc dev ${sddev} && fatload mmc ${sddev} ${uImage_addr} boot.sd;if test $? -eq 0; then bootm ${uImage_addr}#config-cv181x_milkv_duos_sd;fi;
sddev=0
serverip=192.168.56.101
stderr=serial
stdin=serial
stdout=serial
uImage_addr=0x81800000
update_addr=0x9fe00000
vendor=cvitek
Environment size: 4333/131068 bytes
```

Aha Ethernet Driver is available in U-Boot. Which means we can boot NuttX over TFTP yay!

```bash
$ net list

eth0 : ethernet@4070000 00:00:00:00:00:00 active
```

(See below for the U-Boot Commands)

Here's another Linux Image: https://github.com/logicethos/Milk-V_Duo_Linux2SD

# Boot Milk-V Duo S over TFTP 

Read the article...

- ["Apache NuttX RTOS on Sophgo SG2000 RISC-V SoC (Milk-V Duo S SBC)"](https://lupyuen.github.io/articles/sg2000)

We'll port NuttX by booting over TFTP, but let's test TFTP first. Here are the steps to boot Milk-V Duo S over TFTP...

https://lupyuen.github.io/articles/tftp#configure-u-boot-for-tftp

```bash
## Set the U-Boot TFTP Server
setenv tftp_server 192.168.31.10
printenv tftp_server

## If Initial RAM Disk is needed (like for Linux)...
## Set the RAM Disk Size (assume the max)
## setenv ramdisk_size 0x1000000
## printenv ramdisk_size

## Save the U-Boot Config for future reboots
saveenv
```

We load the NuttX Image over TFTP...

```bash
## Fetch the IP Address over DHCP
## Load the NuttX Image from TFTP Server
## kernel_addr_r=0x80200000
## tftp_server=192.168.x.x
dhcp ${kernel_addr_r} ${tftp_server}:Image-sg2000

## Load the Device Tree from TFTP Server
## fdt_addr_r=0x81200000
## TODO: Fix the Device Tree, it's not needed by NuttX
tftpboot ${fdt_addr_r} ${tftp_server}:jh7110-star64-pine64.dtb

## Set the RAM Address of Device Tree
## fdt_addr_r=0x81200000
## TODO: Fix the Device Tree, it's not needed by NuttX
fdt addr ${fdt_addr_r}

## If Initial RAM Disk is needed...
## Load the Intial RAM Disk from TFTP Server
## ramdisk_addr_r=0x81600000
## tftpboot ${ramdisk_addr_r} ${tftp_server}:initrd

## Boot the NuttX Image with the Device Tree
## kernel_addr_r=0x80200000
## fdt_addr_r=0x81200000
## TODO: Fix the Device Tree, it's not needed by NuttX
booti ${kernel_addr_r} - ${fdt_addr_r}

## For Linux: We need the RAM Disk Address
## ramdisk_addr_r=0x81600000
## ramdisk_size=0x1000000
## booti ${kernel_addr_r} ${ramdisk_addr_r}:${ramdisk_size} ${fdt_addr_r}
```

Which becomes this, mashed up in a single line...

```bash
## Boot NuttX Image over TFTP
dhcp ${kernel_addr_r} ${tftp_server}:Image-sg2000 ; tftpboot ${fdt_addr_r} ${tftp_server}:jh7110-star64-pine64.dtb ; fdt addr ${fdt_addr_r} ; booti ${kernel_addr_r} - ${fdt_addr_r}
```

Now we automate the TFTP Booting for future reboots...

```bash
## Add the Boot Command for TFTP
setenv bootcmd_tftp 'dhcp ${kernel_addr_r} ${tftp_server}:Image-sg2000 ; tftpboot ${fdt_addr_r} ${tftp_server}:jh7110-star64-pine64.dtb ; fdt addr ${fdt_addr_r} ; booti ${kernel_addr_r} - ${fdt_addr_r}'
## Check that it's correct
printenv bootcmd_tftp
## Save it for future reboots
saveenv

## Test the Boot Command for TFTP, then reboot
run bootcmd_tftp

## Remember the Original Boot Targets
setenv orig_boot_targets "$boot_targets"
## Should show `mmc0 dhcp pxe`
printenv orig_boot_targets
## Save it for future reboots
saveenv

## Prepend TFTP to the Boot Targets
setenv boot_targets "tftp $boot_targets"
## Should show `tftp mmc0 dhcp pxe`
printenv boot_targets
## Save it for future reboots
saveenv
```

_What happens when we run it at the U-Boot Command Prompt?_

This happens...

```bash
$ setenv tftp_server 192.168.31.10
$ printenv tftp_server
tftp_server=192.168.31.10

$ setenv ramdisk_size 0x1000000
$ printenv ramdisk_size
ramdisk_size=0x1000000

$ dhcp ${kernel_addr_r} ${tftp_server}:Image
Speed: 100, full duplex
BOOTP broadcast 1
BOOTP broadcast 2
*** Unhandled DHCP Option in OFFER/ACK: 43
*** Unhandled DHCP Option in OFFER/ACK: 43
DHCP client bound to address 192.168.31.47 (550 ms)
Using ethernet@4070000 device
TFTP from server 192.168.31.10; our IP address is 192.168.31.47
Filename 'Image'.
Load address: 0x80200000
Loading: #################################################################
. 1.2 MiB/s
done
Bytes transferred = 2097800 (200288 hex)

$ tftpboot ${fdt_addr_r} ${tftp_server}:jh7110-star64-pine64.dtb
Speed: 100, full duplex
Using ethernet@4070000 device
TFTP from server 192.168.31.10; our IP address is 192.168.31.47
Filename 'jh7110-star64-pine64.dtb'.
Load address: 0x81200000
Loading: ####
. 1.1 MiB/s
done
Bytes transferred = 50235 (c43b hex)

$ fdt addr ${fdt_addr_r}

$ booti ${kernel_addr_r} - ${fdt_addr_r}
## Flattened Device Tree blob at 81200000
   Booting using the fdt blob at 0x81200000
   Loading Ramdisk to 9e27f000, end 9f27f000 ... OK
   Loading Device Tree to 000000009e26f000, end 000000009e27e43a ... OK

Starting kernel ...
```

NuttX Kernel hangs, but that's OK! We haven't modified NuttX Kernel for SG2000 yet. Let's print something...

# UART Controller for SG2000

Read the article...

- ["Apache NuttX RTOS on Sophgo SG2000 RISC-V SoC (Milk-V Duo S SBC)"](https://lupyuen.github.io/articles/sg2000)

According to the [SG2000 Reference Manual](https://github.com/sophgo/sophgo-doc/releases), the UART Controller Base Addresses are...

| GPIO Module | Base Address |
|-------------|--------------|
| UART0 | 0x04140000 |
| UART1 | 0x04150000 |
| UART2 | 0x04160000 |
| UART3 | 0x04170000 |
| UART4 | 0x041C0000 |
| RTCSYS_UART | 0x05022000 |

We'll print to UART0 in NuttX.

_What UART Controller is inside SG2000 / Milk-V Duo S?_

According to the OpenSBI Log above: The UART Controller is `uart8250`.

Which is supported by NuttX yay!

Let's modify the NuttX Boot Code to write to the UART Output Register. We'll do this in RISC-V Assembly...

# Print to SG2000 UART in RISC-V Assembly

Read the article...

- ["Apache NuttX RTOS on Sophgo SG2000 RISC-V SoC (Milk-V Duo S SBC)"](https://lupyuen.github.io/articles/sg2000)

Here's how we print to 8250 UART in RISC-V Assembly...

https://lupyuen.github.io/articles/nuttx2#print-to-qemu-console

From the previous section: SG2000 UART0 Controller is at 0x04140000. We'll write to that address, to print something to Serial Console.

We insert this RISC-V Assembly at the top of the NuttX Boot Code...

https://github.com/lupyuen2/wip-nuttx/blob/sg2000/arch/risc-v/src/bl808/bl808_head.S#L70-L89

```c
/* RISC-V Boot Code for Apache NuttX RTOS */
real_start:

  /* Print `123` to UART */
  /* Load UART Base Address to Register t0 */
  li  t0, 0x04140000

  /* Load `1` to Register t1 */
  li  t1, 0x31
  /* Store byte from Register t1 to UART Base Address, Offset 0 */
  sb  t1, 0(t0)

  /* Load `2` to Register t1 */
  li  t1, 0x32
  /* Store byte from Register t1 to UART Base Address, Offset 0 */
  sb  t1, 0(t0)

  /* Load `3` to Register t1 */
  li  t1, 0x33
  /* Store byte from Register t1 to UART Base Address, Offset 0 */
  sb  t1, 0(t0)
```

Which will print `123` when NuttX boots. Let's build and test this!

# Build Apache NuttX RTOS for Milk-V Duo S

Read the article...

- ["Apache NuttX RTOS on Sophgo SG2000 RISC-V SoC (Milk-V Duo S SBC)"](https://lupyuen.github.io/articles/sg2000)

Follow these steps to build (work-in-progress) Apache NuttX RTOS for SG2000 / Milk-V Duo S...

```bash
## TODO: Set PATH
export PATH="$HOME/riscv64-unknown-elf-toolchain-10.2.0-2020.12.8-x86_64-apple-darwin/bin:$PATH"

set -e  #  Exit when any command fails
set -x  #  Echo commands

## Build NuttX
function build_nuttx {

  ## Go to NuttX Folder
  pushd ../nuttx

  ## Build NuttX
  make -j 8

  ## Return to previous folder
  popd
}

## Build Apps Filesystem
function build_apps {

  ## Go to NuttX Folder
  pushd ../nuttx

  ## Build Apps Filesystem
  make -j 8 export
  pushd ../apps
  ./tools/mkimport.sh -z -x ../nuttx/nuttx-export-*.tar.gz
  make -j 8 import
  popd

  ## Return to previous folder
  popd
}

## Download WIP NuttX for SG2000 (based on Ox64 BL808)
git clone --branch sg2000 \
  https://github.com/lupyuen2/wip-nuttx \
  nuttx
git clone --branch sg2000 \
  https://github.com/lupyuen2/wip-nuttx-apps \
  apps
cd nuttx

## Pull updates
git pull && git status && hash1=`git rev-parse HEAD`
pushd ../apps
git pull && git status && hash2=`git rev-parse HEAD`
popd
echo NuttX Source: https://github.com/apache/nuttx/tree/$hash1 >nuttx.hash
echo NuttX Apps: https://github.com/apache/nuttx-apps/tree/$hash2 >>nuttx.hash

## Show the version of GCC
riscv64-unknown-elf-gcc -v

## Configure build
tools/configure.sh ox64:nsh

## Build NuttX
build_nuttx

## Build Apps Filesystem
build_apps

## Generate Initial RAM Disk
genromfs -f initrd -d ../apps/bin -V "NuttXBootVol"

## Show the size
riscv64-unknown-elf-size nuttx

## Export the Binary Image to `nuttx.bin`
riscv64-unknown-elf-objcopy \
  -O binary \
  nuttx \
  nuttx.bin

## Prepare a Padding with 64 KB of zeroes
head -c 65536 /dev/zero >/tmp/nuttx.pad

## Append Padding and Initial RAM Disk to NuttX Kernel
cat nuttx.bin /tmp/nuttx.pad initrd \
  >Image

## Copy the config
cp .config nuttx.config

## Dump the disassembly to nuttx.S
riscv64-unknown-elf-objdump \
  --syms --source --reloc --demangle --line-numbers --wide \
  --debugging \
  nuttx \
  >nuttx.S \
  2>&1

## Dump the init disassembly to init.S
riscv64-unknown-elf-objdump \
  --syms --source --reloc --demangle --line-numbers --wide \
  --debugging \
  ../apps/bin/init \
  >init.S \
  2>&1

## Dump the hello disassembly to hello.S
riscv64-unknown-elf-objdump \
  --syms --source --reloc --demangle --line-numbers --wide \
  --debugging \
  ../apps/bin/hello \
  >hello.S \
  2>&1

## Copy NuttX Image to TFTP Server
scp Image tftpserver:/tftpboot/Image-sg2000
ssh tftpserver ls -l /tftpboot/Image-sg2000
```

Build Outputs are here: https://github.com/lupyuen2/wip-nuttx/releases/tag/sg2000-1

We have copied the NuttX Image to our TFTP Server. Let's boot this on Milk-V Duo S...

# Apache NuttX RTOS boots a tiny bit on Milk-V Duo S

Read the article...

- ["Apache NuttX RTOS on Sophgo SG2000 RISC-V SoC (Milk-V Duo S SBC)"](https://lupyuen.github.io/articles/sg2000)

Earlier we have...

- Inserted the RISC-V Boot Code to print `123` (at NuttX Startup)

- Compiled Apache NuttX RTOS for Milk-V Duo S

- Copied the NuttX Image to our TFTP Server

Let's boot NuttX over TFTP, with a little help from U-Boot Bootloader! Run these commands at the U-Boot Command Prompt...

https://gist.github.com/lupyuen/78b54326daf0894a2c23ab6d2c03456d

```bash
## TODO: Change to your TFTP Server IP Address
$ setenv tftp_server 192.168.31.10

## Download NuttX Image from TFTP Server
$ dhcp ${kernel_addr_r} ${tftp_server}:Image-sg2000
Speed: 100, full duplex
BOOTP broadcast 1
BOOTP broadcast 2
*** Unhandled DHCP Option in OFFER/ACK: 43
*** Unhandled DHCP Option in OFFER/ACK: 43
DHCP client bound to address 192.168.31.243 (424 ms)
Using ethernet@4070000 device
TFTP from server 192.168.31.10; our IP address is 192.168.31.243
Filename 'Image-sg2000'.
Load address: 0x80200000
Loading: #################################################################
. 1.2 MiB/s
done
Bytes transferred = 14195281 (d89a51 hex)

## TODO: NuttX doesn't need the Device Tree. Remove this.
$ tftpboot ${fdt_addr_r} ${tftp_server}:jh7110-star64-pine64.dtb
Speed: 100, full duplex
Using ethernet@4070000 device
TFTP from server 192.168.31.10; our IP address is 192.168.31.243
Filename 'jh7110-star64-pine64.dtb'.
Load address: 0x81200000
Loading: ####
. 1.2 MiB/s
done
Bytes transferred = 50235 (c43b hex)

## TODO: NuttX doesn't need the Device Tree. Remove this.
$ fdt addr ${fdt_addr_r}

## Boot NuttX from RAM. RAM Disk Address must be `-`!
$ booti ${kernel_addr_r} - ${fdt_addr_r}

## For Linux: We need the RAM Disk Address
## booti ${kernel_addr_r} ${ramdisk_addr_r}:${ramdisk_size} ${fdt_addr_r}
```

NuttX boots a tiny bit, and prints `123` yay!

```bash
## Boot NuttX from RAM
$ booti ${kernel_addr_r} - ${fdt_addr_r}

## Flattened Device Tree blob at 81200000
Booting using the fdt blob at 0x81200000
Loading Ramdisk to 9fe00000, end 9fe00000 ... OK
Loading Device Tree to 000000009f26f000, end 000000009f27e43a ... OK

Starting kernel ...
123
```

Our NuttX Boot Code is actually running on SG2000 / Milk-V Duo S!

Coming up...

1.  Fix the Boot Address of NuttX, so the rest of NuttX can start

1.  Configure the 16550 UART Driver for NuttX, so can see the Console Output

TODO: Can we run `expect` with `screen` to automate the testing of NuttX on SG2000?

TODO: If we prefer to boot NuttX with MicroSD instead of TFTP, try this [MicroSD Multiplexer (USB / FTDI)](https://www.tindie.com/products/badgerdnl/sdwire-usb-c-sd-card-reader-sd-mux/)

# Set the NuttX Memory Map for SG2000

Read the article...

- ["Apache NuttX RTOS on Sophgo SG2000 RISC-V SoC (Milk-V Duo S SBC)"](https://lupyuen.github.io/articles/sg2000)

From the U-Boot Bootloader Config above: We see that SG2000 boots at this address...

```bash
kernel_addr_r=0x80200000
```

Thus we define the NuttX Memory Map for SG2000 like so...

https://github.com/lupyuen2/wip-nuttx/commit/c6c0bd3882a855420acf0d53fa9d37bbd9d125b2

NuttX Kernel will boot at 0x8020_0000, NuttX Apps will run at Virtual Address 0xC000_0000.

Here's the NuttX Config: [boards/risc-v/bl808/ox64/configs/nsh/defconfig](https://github.com/lupyuen2/wip-nuttx/commit/c6c0bd3882a855420acf0d53fa9d37bbd9d125b2#diff-fa4b30efe1c5e19ba2fdd2216528406d85fa89bf3d2d0e5161794191c1566078)

```bash
## Kernel RAM
CONFIG_RAM_START=0x80200000
CONFIG_RAM_SIZE=1048576

## Kernel Paged Pool (Allocated to NuttX Apps)
CONFIG_ARCH_PGPOOL_PBASE=0x80600000
CONFIG_ARCH_PGPOOL_VBASE=0x80600000
CONFIG_ARCH_PGPOOL_SIZE=4194304

## Virtual Memory for NuttX App Code
CONFIG_ARCH_TEXT_VBASE=0xC0000000
CONFIG_ARCH_TEXT_NPAGES=128

## Virtual Memory for NuttX App Data
CONFIG_ARCH_DATA_VBASE=0xC0100000
CONFIG_ARCH_DATA_NPAGES=128

## Virtual Memory for NuttX App Heap
CONFIG_ARCH_HEAP_VBASE=0xC0200000
CONFIG_ARCH_HEAP_NPAGES=128
```

And here's the NuttX Linker Script: [boards/risc-v/bl808/ox64/scripts/ld.script](https://github.com/lupyuen2/wip-nuttx/commit/c6c0bd3882a855420acf0d53fa9d37bbd9d125b2#diff-769e7c2389b298f666c84b92f36d3c42fa852fda61dbf20b93e603df98b7bd37)

```c
MEMORY {
    kflash (rx) : ORIGIN = 0x80200000, LENGTH = 2048K   /* w/ cache */
    ksram (rwx) : ORIGIN = 0x80400000, LENGTH = 2048K   /* w/ cache */
    pgram (rwx) : ORIGIN = 0x80600000, LENGTH = 4096K   /* w/ cache */
    ramdisk (rwx) : ORIGIN = 0x80A00000, LENGTH = 16M   /* w/ cache */
}
...
SECTIONS {
  . = 0x80200000;
```

# Disable the PLIC Interrupt Controller

Read the article...

- ["Apache NuttX RTOS on Sophgo SG2000 RISC-V SoC (Milk-V Duo S SBC)"](https://lupyuen.github.io/articles/sg2000)

Most RISC-V SBCs (Ox64, Star64) will manage Interrupts with a Platform-Level Interrupt Controller (PLIC). For now, let's disable PLIC in NuttX...

https://github.com/lupyuen2/wip-nuttx/commit/6d66caa1408d7a7d7b21b0e876ce32ceb5b93ec4

Later we'll dump the SG2000 Linux Device Tree to understand the Interrupt Controller.

# Select the NuttX Driver for 16550 UART

Read the article...

- ["Apache NuttX RTOS on Sophgo SG2000 RISC-V SoC (Milk-V Duo S SBC)"](https://lupyuen.github.io/articles/sg2000)

From the OpenSBI Log above: We see that SG2000 operates with a 8250 UART Controller.

Thus we select the NuttX Driver for 16550 UART, which is compatible with 8250...

https://github.com/lupyuen2/wip-nuttx/commit/8f8831d15d6ddc913e6dd1c6c49fb0067640f6ec

Here's the NuttX Config: [boards/risc-v/bl808/ox64/configs/nsh/defconfig](https://github.com/lupyuen2/wip-nuttx/commit/8f8831d15d6ddc913e6dd1c6c49fb0067640f6ec#diff-fa4b30efe1c5e19ba2fdd2216528406d85fa89bf3d2d0e5161794191c1566078)

```bash
CONFIG_16550_ADDRWIDTH=0
CONFIG_16550_REGINCR=4
CONFIG_16550_UART0=y
CONFIG_16550_UART0_BASE=0x04140000
CONFIG_16550_UART0_CLOCK=23040000
CONFIG_16550_UART0_SERIAL_CONSOLE=y
CONFIG_16550_UART=y
CONFIG_16550_WAIT_LCR=y
CONFIG_SERIAL_UART_ARCH_MMIO=y
```

Don't update the NuttX Config File directly! We ran `make menuconfig` to generate the above file...

```bash
## Update NuttX Config
make menuconfig \
  && make savedefconfig \
  && grep -v CONFIG_HOST defconfig \
  >boards/risc-v/bl808/ox64/configs/nsh/defconfig
```

To find the menuconfig settings: Press "`/`" and enter  the name of the setting, like "16550_ADDRWIDTH". This ensures that the Kconfig Dependencies are correctly updated.

_How did we get IRQ 69 for UART?_

https://github.com/lupyuen2/wip-nuttx/commit/122c717447f81c310a4fb082101213ad338dfb0e

```bash
CONFIG_16550_UART0_IRQ=69
```

We saw this in the [SG2000 Reference Manual](https://github.com/sophgo/sophgo-doc/releases)...

> 3.1 Interrupt Subsystem

> Table 3.2: Interrupt number and Interrupt source mapping for Master RISCV C906 @ 1.0Ghz

> Int #44: UART0

Linx Device Tree also says UART0 IRQ is 44 (0x2C)...

```c
serial@04140000 {
  compatible = "snps,dw-apb-uart";
  reg = <0x00 0x4140000 0x00 0x1000>;
  clock-frequency = <0x17d7840>;
  reg-shift = <0x02>;
  reg-io-width = <0x04>;
  status = "okay";
  interrupts = <0x2c 0x04>;
  interrupt-parent = <0x04>;
};
```

Thus we compute [NuttX IRQ](https://lupyuen.github.io/articles/plic2#uart-interrupt) = 25 + RISC-V IRQ = 69

TODO: Fix the UART Clock: 16550_UART0_CLOCK

# Enable Logging for NuttX Scheduler and Binary Loader

Read the article...

- ["Apache NuttX RTOS on Sophgo SG2000 RISC-V SoC (Milk-V Duo S SBC)"](https://lupyuen.github.io/articles/sg2000)

For easier troubleshooting: We enable the Logging for NuttX Scheduler and Binary Loader...

https://github.com/lupyuen2/wip-nuttx/commit/4cee79630359f6b31fc9fa40f31bb476c8bc4d47

Here's the NuttX Config: [boards/risc-v/bl808/ox64/configs/nsh/defconfig](https://github.com/lupyuen2/wip-nuttx/commit/4cee79630359f6b31fc9fa40f31bb476c8bc4d47#diff-fa4b30efe1c5e19ba2fdd2216528406d85fa89bf3d2d0e5161794191c1566078)

```bash
CONFIG_DEBUG_BINFMT=y
CONFIG_DEBUG_BINFMT_ERROR=y
CONFIG_DEBUG_BINFMT_WARN=y
CONFIG_DEBUG_SCHED=y
CONFIG_DEBUG_SCHED_ERROR=y
CONFIG_DEBUG_SCHED_INFO=y
CONFIG_DEBUG_SCHED_WARN=y
```

Remember: Always use `make menuconfig` to update the settings!

# NuttX Crash Dump on SG2000

Read the article...

- ["Apache NuttX RTOS on Sophgo SG2000 RISC-V SoC (Milk-V Duo S SBC)"](https://lupyuen.github.io/articles/sg2000)

We apply the fixes above. Now NuttX boots some more on RISC-V SG2000 SoC / Milk-V Duo S. And shows our very first NuttX Crash Dump yay!

https://gist.github.com/lupyuen/594f0df20d39001bac171412d594d517

```bash
## Flattened Device Tree blob at 81200000
   Booting using the fdt blob at 0x81200000
   Loading Ramdisk to 9fe00000, end 9fe00000 ... OK
   Loading Device Tree to 000000009f26f000, end 000000009f27e43a ... OK

Starting kernel ...

123ABCnx_start: Entry
uart_register: Registering /dev/console
uart_register: Registering /dev/ttyS0
work_start_lowpri: Starting low-priority kernel worker thread(s)
nxtask_activate: lpwork pid=1,TCB=0x80408130
nxtask_activate: AppBringUp pid=2,TCB=0x80408740
nx_start_application: Starting init task: /system/bin/init
elf_symname: Symbol has no name
elf_symvalue: SHN_UNDEF: Failed to get symbol name: -3
elf_relocateadd: Section 2 reloc 2: Undefined symbol[0] has no name: -3
_assert: Current Version: NuttX  12.4.0 f37a380-dirty May  7 2024 10:31:33 risc-v
_assert: Assertion failed 0x17 == (insn & 0x7F): at file: machine/risc-v/arch_elf.c:494 task: AppBringUp process: Kernel 0x80200f34
up_dump_register: EPC: 000000008021087a
up_dump_register: A0: 0000000080401b70 A1: 00000000000001ee A2: 0000000080228ef8 A3: 0000000000000000
up_dump_register: A4: 0000000000000017 A5: 0000000000000002 A6: 000000000000ab9c A7: fffffffffffffff8
up_dump_register: T0: 000000000000002e T1: 0000000000000007 T2: 00000000000001ff T3: 000000008040c3fc
up_dump_register: T4: 000000008040c3f0 T5: 0000000000000009 T6: 000000000000002a
up_dump_register: S0: 0000000000000000 S1: 0000000080408740 S2: 0000000000000017 S3: 0000000000000000
up_dump_register: S4: 0000000080228ef8 S5: 0000000080228de8 S6: 0000000080401e10 S7: 8000000201842022
up_dump_register: S8: 00000000000001ee S9: 000000008040b9a0 S10: 0000000000000070 S11: 000000008040b990
up_dump_register: SP: 000000008040c330 FP: 0000000000000000 TP: 0000000000000000 RA: 000000008021087a
dump_stack: User Stack:
dump_stack:   base: 0x8040c030
dump_stack:   size: 00002000
dump_stack:     sp: 0x8040c330
```

_What's this Assertion Failure?_

```bash
_assert: Assertion failed 0x17 == (insn & 0x7F):
at file: machine/risc-v/arch_elf.c:494
task: AppBringUp process: Kernel 0x80200f34
```

Oops we goofed and used the wrong U-Boot Command...

```bash
## Nope! This won't work for NuttX. RAM Disk Address must be `-`!
setenv tftp_server 192.168.31.10 ; dhcp ${kernel_addr_r} ${tftp_server}:Image-sg2000 ;
tftpboot ${fdt_addr_r} ${tftp_server}:jh7110-star64-pine64.dtb ; fdt addr ${fdt_addr_r} ;
booti ${kernel_addr_r} ${ramdisk_addr_r}:${ramdisk_size} ${fdt_addr_r}
```

Which overwrites the NuttX Image in RAM. Watch what happens when we use the correct U-Boot Command...

![NuttX Kernel Boots OK on SG2000](https://lupyuen.github.io/images/sg2000-kernel.png)

# NuttX Kernel Boots OK on SG2000

Read the article...

- ["Apache NuttX RTOS on Sophgo SG2000 RISC-V SoC (Milk-V Duo S SBC)"](https://lupyuen.github.io/articles/sg2000)

Earlier we made these fixes...

1.  We set the __NuttX Memory Map__ for SG2000: [nsh/defconfig](https://github.com/lupyuen2/wip-nuttx/commit/c6c0bd3882a855420acf0d53fa9d37bbd9d125b2#diff-fa4b30efe1c5e19ba2fdd2216528406d85fa89bf3d2d0e5161794191c1566078)

    ```bash
    ## Kernel RAM
    CONFIG_RAM_START=0x80200000
    CONFIG_RAM_SIZE=1048576
    ```

1.  Also the __NuttX Linker Script__: [ld.script](https://github.com/lupyuen2/wip-nuttx/commit/c6c0bd3882a855420acf0d53fa9d37bbd9d125b2#diff-769e7c2389b298f666c84b92f36d3c42fa852fda61dbf20b93e603df98b7bd37)

    ```c
    MEMORY {
      kflash (rx) : ORIGIN = 0x80200000, LENGTH = 2048K   /* w/ cache */
      ...
    SECTIONS {
      . = 0x80200000;
    ```

1.  We select the __NuttX Driver for 16550 UART__: [nsh/defconfig](https://github.com/lupyuen2/wip-nuttx/commit/8f8831d15d6ddc913e6dd1c6c49fb0067640f6ec#diff-fa4b30efe1c5e19ba2fdd2216528406d85fa89bf3d2d0e5161794191c1566078)

    ```bash
    CONFIG_16550_REGINCR=4
    CONFIG_16550_UART0=y
    CONFIG_16550_UART0_BASE=0x04140000
    CONFIG_16550_UART0_SERIAL_CONSOLE=y
    CONFIG_16550_UART=y
    CONFIG_16550_WAIT_LCR=y
    CONFIG_SERIAL_UART_ARCH_MMIO=y
    ```

1.  Enable Logging for __NuttX Scheduler and Binary Loader__: [nsh/defconfig](https://github.com/lupyuen2/wip-nuttx/commit/4cee79630359f6b31fc9fa40f31bb476c8bc4d47#diff-fa4b30efe1c5e19ba2fdd2216528406d85fa89bf3d2d0e5161794191c1566078)

    ```bash
    CONFIG_DEBUG_BINFMT=y
    CONFIG_DEBUG_BINFMT_ERROR=y
    CONFIG_DEBUG_BINFMT_WARN=y
    CONFIG_DEBUG_SCHED=y
    CONFIG_DEBUG_SCHED_ERROR=y
    CONFIG_DEBUG_SCHED_INFO=y
    CONFIG_DEBUG_SCHED_WARN=y
    ```

1.  And disable the __PLIC Interrupt Controller__ (until we figure it out)

Also we used the correct U-Boot Command...

```bash
## This works OK for NuttX. RAM Disk Address must be `-`!
setenv tftp_server 192.168.31.10 ; dhcp ${kernel_addr_r} ${tftp_server}:Image-sg2000 ;
tftpboot ${fdt_addr_r} ${tftp_server}:jh7110-star64-pine64.dtb ; fdt addr ${fdt_addr_r} ; 
booti ${kernel_addr_r} - ${fdt_addr_r}
```

NuttX Kernel boots OK on SG2000 yay!

https://gist.github.com/lupyuen/aaa0a6646490d45e5cd99b781cbe59f8

```bash
## Flattened Device Tree blob at 81200000
   Booting using the fdt blob at 0x81200000
   Loading Device Tree to 000000009f26f000, end 000000009f27e43a ... OK

Starting kernel ...

123ABCnx_start: Entry
uart_register: Registering /dev/console
uart_register: Registering /dev/ttyS0
work_start_lowpri: Starting low-priority kernel worker thread(s)
nxtask_activate: lpwork pid=1,TCB=0x80408130
nxtask_activate: AppBringUp pid=2,TCB=0x80408740
nx_start_application: Starting init task: /system/bin/init
elf_symname: Symbol has no name
elf_symvalue: SHN_UNDEF: Failed to get symbol name: -3
elf_relocateadd: Section 2 reloc 2: Undefined symbol[0] has no name: -3
nxtask_activate: /system/bin/init pid=3,TCB=0x80409140
nxtask_exit: AppBringUp pid=2,TCB=0x80408740
```

[(Watch the Demo on YouTube)](https://www.youtube.com/watch?v=pPNDiC5NLqM)

_But where's the NuttX Shell?_

We won't see the NuttX Shell until we fix the Interrupt Controller for SG2000. Which is NOT documented!

Let's sniff around and find out how it works...

# Dump the SG2000 Linux Device Tree

Read the article...

- ["Apache NuttX RTOS on Sophgo SG2000 RISC-V SoC (Milk-V Duo S SBC)"](https://lupyuen.github.io/articles/sg2000)

Let's dump the SG2000 Linux Device Tree to understand the Interrupt Controller.

From the SG2000 Debian Release: https://github.com/Fishwaldo/sophgo-sg200x-debian/releases

We pick the Latest Release for Milk-V Duo S: https://github.com/Fishwaldo/sophgo-sg200x-debian/releases/download/v1.2.0/duos_sd.img.lz4

We copy out the SG2000 Device Tree Binary: [cv181x_milkv_duos_sd.dtb](cv181x_milkv_duos_sd.dtb)

And convert it to Device Tree Source: [cv181x_milkv_duos_sd.dts](cv181x_milkv_duos_sd.dts)

```bash
## Convert the SG2000 Device Tree
dtc \
  -o cv181x_milkv_duos_sd.dts \
  -O dts \
  -I dtb \
  cv181x_milkv_duos_sd.dtb
```

# Interrupt Controller for SG2000

Read the article...

- ["Apache NuttX RTOS on Sophgo SG2000 RISC-V SoC (Milk-V Duo S SBC)"](https://lupyuen.github.io/articles/sg2000)

We dumped the SG2000 Linux Device Tree. Let's extract the Interrupt Controller to understand it.

Based on the SG2000 Device Tree: [cv181x_milkv_duos_sd.dts](cv181x_milkv_duos_sd.dts)

```c
cpus {
  #address-cells = <0x01>;
  #size-cells = <0x00>;
  timebase-frequency = <0x17d7840>;

  cpu-map {

    cluster0 {

      core0 {
        cpu = <0x01>;
      };
    };
  };

  cpu@0 {
    device_type = "cpu";
    reg = <0x00>;
    status = "okay";
    compatible = "riscv";
    riscv,isa = "rv64imafdvcsu";
    mmu-type = "riscv,sv39";
    clock-frequency = <0x17d7840>;

    interrupt-controller {
      #interrupt-cells = <0x01>;
      interrupt-controller;
      compatible = "riscv,cpu-intc";
      phandle = <0x16>;
    };
  };
};

soc {
  #address-cells = <0x02>;
  #size-cells = <0x02>;
  compatible = "simple-bus";
  ranges;

  interrupt-controller@70000000 {
    riscv,ndev = <0x65>;
    riscv,max-priority = <0x07>;
    reg-names = "control";
    reg = <0x00 0x70000000 0x00 0x4000000>;
    interrupts-extended = <0x16 0xffffffff 0x16 0x09>;
    interrupt-controller;
    compatible = "riscv,plic0";
    #interrupt-cells = <0x02>;
    #address-cells = <0x00>;
    phandle = <0x04>;
  };

  clint@74000000 {
    interrupts-extended = <0x16 0x03 0x16 0x07>;
    reg = <0x00 0x74000000 0x00 0x10000>;
    compatible = "riscv,clint0";
    clint,has-no-64bit-mmio;
  };
};
```

We see that PLIC is at 0x7000_0000, CLINT at 0x7400_0000. Let's implement this in NuttX...

# Fix the PLIC Interrupt Controller for SG2000

Read the article...

- ["Apache NuttX RTOS on Sophgo SG2000 RISC-V SoC (Milk-V Duo S SBC)"](https://lupyuen.github.io/articles/sg2000)

Based on the PLIC Address from above: We fix the PLIC Interrupt Controller for SG2000...

https://github.com/lupyuen2/wip-nuttx/commit/f5f1aeac36350b8149fc2a77c817217711f082f6

![Platform-Level Interrupt Controller](https://lupyuen.github.io/images/sg2000-plic.jpg)

Now we see a bit more NuttX...

https://gist.github.com/lupyuen/922e6379375fbc5d775d1e83cac4deb5

```text
Starting kernel ...

123ABCnx_start: Entry
uart_register: Registering /dev/console
uart_register: Registering /dev/ttyS0
work_start_lowpri: Starting low-priority kernel worker thread(s)
nxtask_activate: lpwork pid=1,TCB=0x80409130
nxtask_activate: AppBringUp pid=2,TCB=0x80409740
nx_start_application: Starting init task: /system/bin/init
elf_symname: Symbol has no name
elf_symvalue: SHN_UNDEF: Failed to get symbol name: -3
elf_relocateadd: Section 2 reloc 2: Undefined symbol[0] has no name: -3
nxtask_activate: /system/bin/init pid=3,TCB=0x8040b730
nxtask_exit: AppBringUp pid=2,TCB=0x80409740

Nuttnx_start: CPU0: Beginning Idle Loop
```

_Why did it stop?_

Duh we set the wrong UART0 IRQ! Here's the fix...

https://github.com/lupyuen2/wip-nuttx/commit/122c717447f81c310a4fb082101213ad338dfb0e

```bash
CONFIG_16550_UART0_IRQ=69
```

_How did we get IRQ 69 for UART?_

We saw this in the [SG2000 Reference Manual](https://github.com/sophgo/sophgo-doc/releases)...

> 3.1 Interrupt Subsystem

> Table 3.2: Interrupt number and Interrupt source mapping for Master RISCV C906 @ 1.0Ghz

> Int #44: UART0

Linx Device Tree also says UART0 IRQ is 44 (0x2C)...

```c
serial@04140000 {
  compatible = "snps,dw-apb-uart";
  reg = <0x00 0x4140000 0x00 0x1000>;
  clock-frequency = <0x17d7840>;
  reg-shift = <0x02>;
  reg-io-width = <0x04>;
  status = "okay";
  interrupts = <0x2c 0x04>;
  interrupt-parent = <0x04>;
};
```

Thus we compute [NuttX IRQ](https://lupyuen.github.io/articles/plic2#uart-interrupt) = 25 + RISC-V IRQ = 69

![NuttX Shell runs OK](https://lupyuen.github.io/images/sg2000-nsh.png)

# NuttX Shell runs OK on SG2000

Read the article...

- ["Apache NuttX RTOS on Sophgo SG2000 RISC-V SoC (Milk-V Duo S SBC)"](https://lupyuen.github.io/articles/sg2000)

Earlier we made these fixes...

1.  We dumped the __Linux Device Tree__ for SG2000...

    ```bash
    ## Convert the SG2000 Device Tree
    dtc \
      -o cv181x_milkv_duos_sd.dts \
      -O dts \
      -I dtb \
      cv181x_milkv_duos_sd.dtb
    ```

1.  Snooped the __PLIC Interrupt Controller__ in the Device Tree: [cv181x_milkv_duos_sd.dts](https://github.com/lupyuen/nuttx-sg2000/blob/main/cv181x_milkv_duos_sd.dts)

    ```c
    interrupt-controller@70000000 {
      riscv,ndev = <0x65>;
      riscv,max-priority = <0x07>;
      reg-names = "control";
      reg = <0x00 0x70000000 0x00 0x4000000>;
      interrupts-extended = <0x16 0xffffffff 0x16 0x09>;
      interrupt-controller;
      compatible = "riscv,plic0";
    ```

1.  And fixed the __NuttX Driver__ for PLIC Interrupts: [bl808_memorymap.h](https://github.com/lupyuen2/wip-nuttx/commit/f5f1aeac36350b8149fc2a77c817217711f082f6#diff-8fffa570a48f8f10004d9da8d4c671d34336f6c4b8dcfc2bd72275d8cda4ac04)

    ```c
    // Base Address of PLIC Interrupt Controller
    #define BL808_PLIC_BASE 0x70000000ul
    ```

After fixing the Interrupt Controller and UART Interrupt: NuttX Kernel now boots all the way to NuttX Shell yay!

https://gist.github.com/lupyuen/b778986ba87c18067cd993b92c673634

```bash
Starting kernel ...

123ABCnx_start: Entry
uart_register: Registering /dev/console
uart_register: Registering /dev/ttyS0
work_start_lowpri: Starting low-priority kernel worker thread(s)
nxtask_activate: lpwork pid=1,TCB=0x80409130
nxtask_activate: AppBringUp pid=2,TCB=0x80409740
nx_start_application: Starting init task: /system/bin/init
elf_symname: Symbol has no name
elf_symvalue: SHN_UNDEF: Failed to get symbol name: -3
elf_relocateadd: Section 2 reloc 2: Undefined symbol[0] has no name: -3
nxtask_activate: /system/bin/init pid=3,TCB=0x8040b730
nxtask_exit: AppBringUp pid=2,TCB=0x80409740

NuttShell (NSH) NuttX-12.4.0
nsh> nx_start: CPU0: Beginning Idle Loop
ls
posix_spawn: pid=0xc0202968 path=ls file_actions=0xc0202970 attr=0xc0202978 argv=0xc0202a18
exec_internal: ERROR: Failed to load program 'ls': -2
nxposix_spawn_exec: ERROR: exec failed: 2
/:
 dev/
 proc/
 system/
nsh> 
nsh> uname -a
posix_spawn: pid=0xc0202968 path=uname file_actions=0xc0202970 attr=0xc0202978 argv=0xc0202a18
exec_internal: ERROR: Failed to load program 'uname': -2
nxposix_spawn_exec: ERROR: exec failed: 2
NuttX 12.4.0 122c717 May  8 2024 18:13:30 risc-v ox64
nsh> 
nsh> free
posix_spawn: pid=0xc0202968 path=free file_actions=0xc0202970 attr=0xc0202978 argv=0xc0202a18
exec_internal: ERROR: Failed to load program 'free': -2
nxposix_spawn_exec: ERROR: exec failed: 2
                 total       used       free    maxused    maxfree  nused  nfree
      Kmem:    2065400      14296    2051104      76632    2049392     36      3
      Page:   20971520     647168   20324352   20324352
nsh> 
nsh> ls /dev
posix_spawn: pid=0xc0202968 path=ls file_actions=0xc0202970 attr=0xc0202978 argv=0xc0202a18
exec_internal: ERROR: Failed to load program 'ls': -2
nxposix_spawn_exec: ERROR: exec failed: 2
/dev:
 console
 null
 ram0
 ttyS0
 zero
nsh> 
nsh> 
```

_What about the rest of NuttX?_

__NuttX OSTest__ is the perfect way to test everything in NuttX...

```bash
nsh> ostest
user_main: mutex test
riscv_exception:
  EXCEPTION: Load access fault
  MCAUSE:    5
  EPC:       802189ce
  MTVAL:     0000000000000000
  Segmentation fault in PID 7: ostest
```

Sadly we're hitting a RISC-V Exception: __Load Access Fault__. Needs more troubleshooting sigh.

[(See the __Complete Log__)](https://gist.github.com/lupyuen/fff5242cf77a3f52d81f3effb9aa402f)

# U-Boot Commands for Milk-V Duo S

Read the article...

- ["Apache NuttX RTOS on Sophgo SG2000 RISC-V SoC (Milk-V Duo S SBC)"](https://lupyuen.github.io/articles/sg2000)

Here are the U-Boot Commands available for Milk-V Duo S...

https://gist.github.com/lupyuen/000b55a46336cddf217a589f469d60e2

```bash
cv181x_c906# help

?         - alias for 'help'
base      - print or set address offset
bdinfo    - print Board Info structure
blkcache  - block cache diagnostics and control
boot      - boot default, i.e., run 'bootcmd'
bootd     - boot default, i.e., run 'bootcmd'
bootefi   - Boots an EFI payload from memory
bootelf   - Boot from an ELF image in memory
booti     - boot Linux kernel 'Image' format from memory
bootm     - boot application image from memory
bootp     - boot image via network using BOOTP/TFTP protocol
bootvx    - Boot vxWorks from an ELF image
cmp       - memory compare
cp        - memory copy
cpu       - display information about CPUs
cvi_sd_boot- boot from SD card
cvi_update- cvi_update [eth, sd, usb]- check boot status and update if necessary

cvi_utask - bootloader control block command
dcache    - enable or disable data cache
dhcp      - boot image via network using DHCP/TFTP protocol
echo      - echo args to console
efuser    - Read efuse
efuser_dump- Read/Dump efuse
efusew    - Write efuse
efusew_word- Write word to efuse
env       - environment handling commands
erase     - erase FLASH memory
exit      - exit script
ext2load  - load binary file from a Ext2 filesystem
ext2ls    - list files in a directory (default /)
ext4load  - load binary file from a Ext4 filesystem
ext4ls    - list files in a directory (default /)
ext4size  - determine a file's size
false     - do nothing, unsuccessfully
fatinfo   - print information about filesystem
fatload   - load binary file from a dos filesystem
fatls     - list files in a directory (default /)
fatmkdir  - create a directory
fatrm     - delete a file
fatsize   - determine a file's size
fatwrite  - write file into a dos filesystem
fdt       - flattened device tree utility commands
flinfo    - print FLASH memory information
fstype    - Look up a filesystem type
fstypes   - List supported filesystem types
go        - start application at address 'addr'
help      - print command description/usage
icache    - enable or disable instruction cache
iminfo    - print header information for application image
ln        - Create a symbolic link
load      - load binary file from a filesystem
loadb     - load binary file over serial line (kermit mode)
loadx     - load binary file over serial line (xmodem mode)
loady     - load binary file over serial line (ymodem mode)
loop      - infinite loop on address range
ls        - list files in a directory (default /)
md        - memory display
mdio      - MDIO utility commands
mii       - MII utility commands
mm        - memory modify (auto-incrementing address)
mmc       - MMC sub system
mmcinfo   - display MMC info
mw        - memory write (fill)
net       - NET sub-system
nfs       - boot image via network using NFS protocol
nm        - memory modify (constant address)
panic     - Panic with optional message
part      - disk partition related commands
ping      - send ICMP ECHO_REQUEST to network host
printenv  - print environment variables
protect   - enable or disable FLASH write protection
pxe       - commands to get and boot from pxe files
random    - fill memory with random pattern
reset     - Perform RESET of the CPU
run       - run commands in an environment variable
save      - save file to a filesystem
saveenv   - save environment variables to persistent storage
setenv    - set environment variables
setexpr   - set environment variable as the result of eval expression
showvar   - print local hushshell variables
size      - determine a file's size
sleep     - delay execution for some time
source    - run script from memory
sysboot   - command to get and boot from syslinux files
test      - minimal test like /bin/sh
tftpboot  - boot image via network using TFTP protocol
true      - do nothing, successfully
version   - print monitor, compiler and linker version
```
