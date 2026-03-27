# Build Instructions

## Prerequisites (WSL2 / Ubuntu)

```bash
sudo apt install -y git python3-pip build-essential \
  gcc-avr avr-libc dfu-programmer dfu-util \
  gcc-arm-none-eabi binutils-arm-none-eabi libnewlib-arm-none-eabi

python3 -m pip install --user --break-system-packages qmk
```

## Clone & Setup

```bash
git clone git@github.com:webskin/qmk_firmware.git
cd qmk_firmware
git checkout webskin/firmware25
git submodule update --init --recursive
```

## Build

```bash
# Old board: Teensy + Shine (underglow RGB)
make zsa/ergodox_ez/m32u4/shine:webskin
# Output: zsa_ergodox_ez_m32u4_shine_webskin.hex

# New board: STM32 + Base (no RGB)
make zsa/ergodox_ez/stm32:webskin
# Output: zsa_ergodox_ez_stm32_base_webskin.bin
```

## Flash

Use [Keymapp](https://www.zsa.io/flash) on Windows to flash the firmware files. Keymapp auto-detects the board and prompts for the right format:

- `.hex` for the Teensy board
- `.bin` for the STM32 board

Access WSL files from Windows at `\\wsl$\Ubuntu\home\...\ws-ergodox-ez\`

## Updating from ZSA Upstream

```bash
git checkout firmware25
git pull zsa firmware25
git checkout webskin/firmware25
git rebase firmware25
```

## Output Directories

Built firmware can be copied to the workspace output directories:

```bash
cp zsa_ergodox_ez_m32u4_shine_webskin.hex ../teensy/
cp zsa_ergodox_ez_stm32_base_webskin.bin ../stm/
```
