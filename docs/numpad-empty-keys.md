# NUMPAD - Empty Key Suggestions

The NUMPAD layer is accessed by holding `LT(NUMPAD, KC_SPACE)`. It has F1-F12 on row 1, a numpad 0-9 on the home row, math operators top-right, and mod-taps for Ctrl/Alt on row 3. Many positions are empty, especially row 0, row 3, row 4, and all thumbs.

## Current NUMPAD Layout Map

Empty positions marked with `[___]`:

```
Row 0 (number row):
LEFT:  [___]  [___]  [___]  [___]  [___]  [___]  [___]
RIGHT: [___]  [___]  KP_+  KP_-  KP_/  KP_*  [___]

Row 1 (top):
LEFT:  [___]  F1  F2  SFT(F3)  F4  F5  [___]
RIGHT: [___]  F6  F7  SFT(F8)  F9  F10  F11

Row 2 (home):
LEFT:  [___]  KP_1  KP_2  KP_3  KP_4  KP_5
RIGHT: KP_6  KP_7  KP_8  KP_9  KP_0  F12

Row 3 (bottom):
LEFT:  [___]  CTL(-)  [___]  [___]  KP_.  ALT(-)  [___]
RIGHT: [___]  ALT(-)  [___]  [___]  [___]  RCTL(-)  [___]

Row 4 + Thumbs: all [___]
```

**Mapped:** 30 keys (F1-F12, numpad 0-9, 4 operators, dot, mod-taps)
**Empty:** ~46 positions

## Row 0 Suggestions

### Left Side - Missing Number Row Extras

| Position | Suggestion | Why |
|---|---|---|
| Row 0, pos 0 | `KC_NUM` | Num Lock toggle -- useful if numpad keys aren't sending expected values |
| Row 0, pos 1 | `KC_KP_EQUAL` | Numpad `=` |
| Row 0, pos 2 | `KC_PERC` | `%` -- common in calculations |

### Right Side - Complete Math Operators

| Position | Suggestion | Why |
|---|---|---|
| Row 0, right pos 1 | `KC_KP_ENTER` | Numpad Enter -- confirms calculation in many apps |
| Row 0, right corner | `KC_BSPC` | Quick delete while entering numbers |

## Row 1 Suggestions

### Big Keys (Inner Column)

| Position | Suggestion | Why |
|---|---|---|
| Row 1, left big key `[___]` | `KC_F13` | Extended function key (used by macros/shortcuts) |
| Row 1, right big key `[___]` | `KC_F14` | Extended function key |
| Row 1, left corner `[___]` | `KC_ESC` | Escape -- exit numpad mode quickly |

## Row 2 Suggestions

### Left Corner

| Position | Suggestion | Why |
|---|---|---|
| Row 2, pos 0 `[___]` | `KC_TAB` | Tab between fields while entering numbers (e.g., spreadsheets) |

## Row 3 Suggestions - Fill the Gaps

Row 3 has Ctrl/Alt mod-taps on the edges but empty middle positions.

| Position | Suggestion | Why |
|---|---|---|
| Row 3 left, pos 2 `[___]` | `KC_KP_COMMA` | Thousands separator in some locales |
| Row 3 left, pos 3 `[___]` | `KC_MINUS` | Regular minus (not numpad) -- for negative numbers |
| Row 3 right, pos 2 `[___]` | `KC_EQUAL` | Regular `=` |
| Row 3 right, pos 3 `[___]` | `KC_COMMA` | Regular comma (French decimal separator) |
| Row 3 right, pos 4 `[___]` | `KC_DOT` | Regular dot (alternative decimal separator) |

### French Consideration

In French locale, the decimal separator is `,` (comma) not `.` (dot). The numpad dot `KC_KP_DOT` sends `.` which may not be correct for French number input. Having both `KC_COMMA` and `KC_KP_DOT` available lets you pick the right one depending on the application.

## Row 4 & Thumb Suggestions

| Position | Suggestion | Why |
|---|---|---|
| Row 4, left pos 0 | `KC_ESC` | Quick exit |
| Row 4, left pos 1 | `KC_TAB` | Field navigation |
| Thumb left | `KC_KP_0` | Duplicate zero on thumb for quick `00` entry |
| Thumb right | `KC_KP_ENTER` | Numpad Enter on thumb -- natural confirm position |

## Extended Function Keys (F13-F24)

F13-F24 are available in QMK and usable as custom shortcuts in most applications. If you need more F-keys beyond F12:

| Position | Key | Common Use |
|---|---|---|
| Row 0, left | `KC_F13` - `KC_F18` | Custom app/IDE shortcuts |
| Row 3, gaps | `KC_F19` - `KC_F24` | Streaming (OBS), macros |

## Summary

| Priority | Suggestion | Positions |
|---|---|---|
| **High** | `KC_KP_ENTER` (numpad enter) | Row 0 right or thumb |
| **High** | `KC_TAB` (field navigation) | Row 2 left corner |
| **High** | French decimal `,` alongside `.` | Row 3 gaps |
| Medium | `KC_BSPC` (delete while typing numbers) | Row 0 right corner |
| Medium | `KC_ESC` (quick exit) | Row 1 left corner |
| Medium | `KC_NUM` (num lock toggle) | Row 0 left corner |
| Low | F13-F24 extended function keys | Row 0 left, row 3 gaps |
| Low | `KC_KP_0` on thumb for quick double-zero | Thumb cluster |

The biggest gaps are **numpad Enter** (no way to confirm input), **Tab** (can't navigate between fields), and the **French comma decimal separator**.
