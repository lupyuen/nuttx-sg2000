# Apache NuttX RTOS on 64-bit RISC-V Sophgo SG2000 (T-Head C906 / Milk-V Duo S)

64-bit RISC-V Sophgo SG2000 SoC ... Will it boot Apache NuttX RTOS? 🤔 (T-Head C906 / Milk-V Duo S)

Source: https://www.cnx-software.com/2024/02/07/sophgo-sg2000-sg2002-ai-soc-features-risc-v-arm-8051-cores-android-linux-freertos/

Let's find out! Connect our USB UART Dongle like so...

https://milkv.io/docs/duo/getting-started/duos

USB UART Dongle must be CP2102, it doesn't like CH340G 😬

Flip the switch so it's set to "RV" (RISC-V) instead of "Arm"

Power up via the USB-C Port. We should see in RISC-V Mode...

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

If we use CH340G: UART Output will be garbled...

https://gist.github.com/lupyuen/1d5ba1b2a47c110ee7ff265102b1aae5

Milk-V Duo S doesn't ship with U-Boot Bootloader preinstalled. Too bad we can't boot NuttX over TFTP, our NuttX Porting will be a bit slower. Bummer :-(

TODO: Boot with U-Boot or Linux on MicroSD

TODO: Get the eMMC Version with U-Boot preinstalled
