# Apache NuttX RTOS on 64-bit RISC-V Sophgo SG2000 (T-Head C906 / Milk-V Duo S)

64-bit RISC-V Sophgo SG2000 SoC ... Will it boot Apache NuttX RTOS? 🤔 (T-Head C906 / Milk-V Duo S)

Source: https://www.cnx-software.com/2024/02/07/sophgo-sg2000-sg2002-ai-soc-features-risc-v-arm-8051-cores-android-linux-freertos/

Let's find out! Connect our USB UART Dongle like so...

https://milkv.io/docs/duo/getting-started/duos

USB UART Dongle must be CP2102, it doesn't like CH340G 😬

Flip the switch so it's set to "RV" (RISC-V) instead of "Arm"

Milk-V Duo S doesn't ship with U-Boot Bootloader preinstalled. Too bad we can't boot NuttX over TFTP, that will make NuttX Porting a lot easier. Bummer :-(

TODO
