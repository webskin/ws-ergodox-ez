# Migration from Old QMK to firmware25

The original keymap was written ~7 years ago for the pre-ZSA QMK fork. Here are all the changes applied to make it compile on ZSA's `firmware25` branch (March 2026).

## Keycode Renames (17)

| Old | New | Reason |
|---|---|---|
| `EZ_SAFE_RANGE` | `ZSA_SAFE_RANGE` | ZSA namespace change |
| `KC_BSPACE` | `KC_BSPC` | Deprecated alias removed |
| `KC_PSCREEN` | `KC_PSCR` | Deprecated alias removed |
| `BP_EN_DASH` | `BP_NDSH` | Renamed |
| `BP_EM_DASH` | `BP_MDSH` | Renamed |
| `BP_ECUT` | `BP_EACU` | Renamed |
| `BP_DCRC` | `BP_DCIR` | Renamed |
| `BP_APOS` | `BP_QUOT` | Renamed |
| `BP_LESS` | `BP_LABK` | Renamed |
| `BP_GRTR` | `BP_RABK` | Renamed |
| `BP_LGIL` | `BP_LDAQ` | Renamed |
| `BP_RGIL` | `BP_RDAQ` | Renamed |
| `BP_DQOT` | `BP_DQUO` | Renamed |
| `BP_COLON` | `BP_COLN` | Renamed |
| `BP_DEGR` | `BP_DEG` | Renamed |
| `FR_APOS` | `FR_QUOT` | Renamed |
| `FR_LESS` | `FR_LABK` | Renamed |
| `FR_GRTR` | `FR_RABK` | Renamed |

## API & Signature Changes

| Change | Details |
|---|---|
| Function rename | `biton32()` -> `get_highest_layer()` |
| Type change | `uint32_t` -> `layer_state_t` for layer state functions |
| Signature change | `get_tapping_term(keycode)` -> `get_tapping_term(keycode, record)` |
| API change | `rgblight_config.raw = eeconfig_read_rgblight()` -> `eeconfig_read_rgblight(&rgblight_config)` |
| Type rename | `qk_tap_dance_action_t` -> `tap_dance_action_t` |
| Variable rename | `disable_layer_color` -> `keyboard_config.disable_layer_led` |

## Removed / Replaced Config

### config.h

| Removed | Reason |
|---|---|
| `#define COMBO_COUNT 1` | Auto-detected in modern QMK |
| `#define IGNORE_MOD_TAP_INTERRUPT` | Removed in QMK 0.20; now default behavior |

### rules.mk

| Removed | Reason |
|---|---|
| `COMBO_ENABLE = yes` | No combos were defined |
| `LINK_TIME_OPTIMIZATION_ENABLE = yes` | Renamed to `LTO_ENABLE`; set by keyboard info.json |
| `WEBUSB_ENABLE = no` | Feature removed from QMK |

### keymap.c

| Removed | Reason |
|---|---|
| `TOGGLE_LAYER_COLOR` case in `process_record_user` | Now handled by ZSA `zsa/defaults` module at keyboard level |
| `bool disable_layer_color` variable | Replaced by `keyboard_config.disable_layer_led` |
| `bool suspended` variable | Unused |

## New: ZSA Module

Added `keymap.json` to include the `zsa/defaults` module:

```json
{
    "modules": [
        "zsa/defaults"
    ]
}
```

This provides `TOGGLE_LAYER_COLOR`, `LED_LEVEL`, and `ZSA_SAFE_RANGE` at the keyboard level.

## RGB Guards

All `rgblight_*` calls wrapped in `#ifdef RGBLIGHT_ENABLE` so the same keymap compiles for both:

- **Shine** (m32u4) -- has `RGBLIGHT_ENABLE`, RGB code is compiled
- **Base** (STM32) -- no `RGBLIGHT_ENABLE`, RGB code is skipped

```c
#ifdef RGBLIGHT_ENABLE
  rgblight_enable_noeeprom();
  rgblight_mode_noeeprom(1);
  rgblight_sethsv_noeeprom(85, 255, 127);
#endif
```
