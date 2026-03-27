# CLAUDE.md

## Communication

- Before executing a prompt, reformulate the user's request in clear English so they can confirm the intent. The user's prompts may contain grammar or phrasing issues — always restate the task clearly before proceeding.
- Don't use plan mode for trivial operations (git push, simple edits, etc.).

## Project Overview

Two ErgoDox EZ keyboards sharing one QMK keymap:

| | Old Board | New Board |
|---|---|---|
| MCU | Teensy / ATmega32U4 | STM32 / F303 |
| Variant | Shine (underglow RGB) | Base (no RGB) |
| Firmware | `.hex` | `.bin` |

## Repositories

### ws-ergodox-ez (this repo)

- GitHub: https://github.com/webskin/ws-ergodox-ez
- MkDocs documentation site (Material theme), deploy with `mkdocs gh-deploy`
- `docs/` contains markdown pages, `mkdocs.yml` at root
- `teensy/` and `stm/` are output directories for built firmware (gitignored)

### qmk_firmware (subdir)

- GitHub: https://github.com/webskin/qmk_firmware (SSH: `git@github.com:webskin/qmk_firmware.git`)
- Fork of ZSA's QMK firmware
- Upstream remote `zsa` points to `https://github.com/zsa/qmk_firmware.git`

**Branches:**

| Branch | Purpose |
|---|---|
| `firmware25` | Clean tracking of ZSA upstream (never commit keymap changes here) |
| `webskin/firmware25` | Working branch with keymap customizations |
| `develop` | Original 7-year-old keymap (archived, read-only) |

**Keymap location:** `keyboards/zsa/ergodox_ez/keymaps/webskin/`

Files: `keymap.c`, `config.h`, `rules.mk`, `keymap.json`

## Build Commands

```bash
cd qmk_firmware

# Old board (Teensy + Shine)
make zsa/ergodox_ez/m32u4/shine:webskin
cp zsa_ergodox_ez_m32u4_shine_webskin.hex ../teensy/

# New board (STM32 + Base)
make zsa/ergodox_ez/stm32:webskin
cp zsa_ergodox_ez_stm32_base_webskin.bin ../stm/
```

Flash via Keymapp on Windows.

## Updating from ZSA Upstream

```bash
cd qmk_firmware
git checkout firmware25
git pull zsa firmware25
git checkout webskin/firmware25
git rebase firmware25
```

## Keymap Details

- 14 layers: BEPO, AZERT, MISCL1/1AZ, MISCL2/2AZ, MISCR1/1AZ, MISCR2/2AZ, NUMPAD, MOUSE, FXXNPOH, GAME1
- 4 custom keycodes: `THIN_ARROW` (`->`), `FAT_ARROW` (`=>`), `TILD_ARROW` (`~>`), `PIPE_ARROW` (`|>`)
- 12 tap dance actions (Bepo + AZERTY variants)
- Smart digraph protection on home row when accessing symbol layers
- RGB code wrapped in `#ifdef RGBLIGHT_ENABLE` for Base (no-RGB) compatibility
- Uses `zsa/defaults` module (provides `TOGGLE_LAYER_COLOR`, `LED_LEVEL`, `ZSA_SAFE_RANGE`)
- `keyboard_config.disable_layer_led` controls RGB layer indicators
