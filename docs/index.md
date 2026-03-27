# ErgoDox EZ - Webskin Keymap

Custom firmware for two ErgoDox EZ keyboards, migrated to ZSA firmware25.

## Boards

| | Old Board | New Board |
|---|---|---|
| **MCU** | Teensy / ATmega32U4 | STM32 / F303 |
| **Variant** | Shine (underglow RGB) | Base (no RGB) |
| **Bootloader** | HalfKay | DFU |
| **Firmware** | `.hex` | `.hex` |

Both boards share the same keymap source. RGB code is guarded with `#ifdef RGBLIGHT_ENABLE` so it compiles for the Base variant.

## Repository & Branches

Fork: [github.com/webskin/qmk_firmware](https://github.com/webskin/qmk_firmware)

| Branch | Purpose |
|---|---|
| `firmware25` | Clean tracking branch for [ZSA upstream](https://github.com/zsa/qmk_firmware/tree/firmware25) |
| `webskin/firmware25` | Working branch with keymap customizations |
| `develop` | Original 7-year-old keymap (archived) |

Keymap source: `keyboards/zsa/ergodox_ez/keymaps/webskin/`

## File Structure

```
ws-ergodox-ez/
  docs/                     # MkDocs documentation
  teensy/                   # Built .hex firmware
  stm/                      # Built .bin firmware
  qmk_firmware/             # ZSA QMK fork
    keyboards/zsa/ergodox_ez/keymaps/webskin/
      keymap.c              # 14-layer keymap (~830 lines)
      config.h              # Tapping term, permissive hold
      rules.mk              # Tap dance enabled
      keymap.json            # ZSA defaults module
```

## Build Results

| Target | Size | Free |
|---|---|---|
| Teensy / Shine | 26,526 / 32,256 bytes (82%) | 5,730 bytes |
| STM32 / Base | 38,912 / 262,144 bytes (15%) | 223,232 bytes |
