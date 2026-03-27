# MOUSE - Empty Key Suggestions

The MOUSE layer is accessed via `MO(MOUSE)` on the left thumb cluster. It has a minimal right-hand mouse cluster (movement, 3 buttons, scroll up/down). The **entire left half is empty**, and much of the right half too.

## Current MOUSE Layout Map

Empty positions marked with `[___]`:

```
Row 0 (number row):
LEFT:  [___]  [___]  [___]  [___]  [___]  [___]  [___]
RIGHT: [___]  [___]  [___]  BTN3  [___]  [___]  [___]

Row 1 (top):
LEFT:  [___]  [___]  [___]  [___]  [___]  [___]  [___]
RIGHT: [___]  [___]  BTN1  MS_UP  BTN2  [___]  [___]

Row 2 (home):
LEFT:  [___]  [___]  [___]  [___]  [___]  [___]
RIGHT: WH_UP  MS_LEFT  MS_DOWN  MS_RIGHT  [___]  [___]

Row 3 (bottom):
LEFT:  [___]  [___]  [___]  [___]  [___]  [___]  [___]
RIGHT: [___]  WH_DOWN  [___]  [___]  [___]  [___]  [___]

Row 4 + Thumbs: all [___]
```

**Mapped:** 10 keys (4 movement, 3 buttons, 2 scroll, 1 middle click)
**Empty:** ~66 positions

## Right Half Suggestions

### High Priority: Missing Mouse Features

#### Mouse Buttons 4 & 5 (Back/Forward)

Essential for browser navigation and many apps.

| Position | Key | Why |
|---|---|---|
| Row 1, right pos 1 `[___]` (left of BTN1) | `KC_MS_BTN4` | Back (browser, file explorer) |
| Row 1, right corner `[___]` (right of BTN2) | `KC_MS_BTN5` | Forward (browser, file explorer) |

#### Horizontal Scroll

Missing from the current layout. Useful in spreadsheets, timelines, wide documents.

| Position | Key | Why |
|---|---|---|
| Row 3, right pos 2 `[___]` | `KC_MS_WH_LEFT` | Scroll left |
| Row 3, right pos 3 `[___]` | `KC_MS_WH_RIGHT` | Scroll right |

#### Mouse Acceleration Toggle

| Position | Key | Why |
|---|---|---|
| Row 2, right pos 4 `[___]` | `KC_MS_ACCEL0` | Slow mouse speed (precision) |
| Row 2, right pos 5 `[___]` | `KC_MS_ACCEL2` | Fast mouse speed (quick movement) |

Or use a single toggle:

| Position | Key | Why |
|---|---|---|
| Row 2, right corner | `KC_MS_ACCEL1` | Medium speed (default) |

### Medium Priority: Click Modifiers

Shift-click, Ctrl-click, etc. are common but require two hands normally. Dedicated keys let you do modified clicks with one hand.

| Position | Key | Why |
|---|---|---|
| Row 0, right pos 2 `[___]` | `S(KC_MS_BTN1)` | Shift+Click (extend selection) |
| Row 0, right pos 4 `[___]` | `C(KC_MS_BTN1)` | Ctrl+Click (multi-select, open in new tab) |

### Row 3 Right Side - Complete the Layout

| Position | Key | Why |
|---|---|---|
| Row 3, right pos 4 `[___]` | `KC_MS_BTN1` | Duplicate left-click -- accessible from more positions |
| Row 3, right pos 5 `[___]` | `KC_MS_BTN2` | Duplicate right-click |

## Left Half Suggestions

The left half can serve as a **keyboard companion** while mousing -- keys you'd normally need but can't reach while your right hand is on the mouse.

### High Priority: Common Shortcuts for Mousing

| Position | Key | Why |
|---|---|---|
| Row 2, pos 0 | `KC_ESC` | Cancel / close menu |
| Row 2, pos 1 | `C(KC_Z)` | Undo -- essential while editing with mouse |
| Row 2, pos 2 | `C(KC_C)` | Copy |
| Row 2, pos 3 | `C(KC_V)` | Paste |
| Row 2, pos 4 | `C(KC_X)` | Cut |
| Row 2, pos 5 | `C(KC_A)` | Select All |

### Medium Priority: Modifiers for Click Combinations

Hold these with left hand while clicking with right:

| Position | Key | Why |
|---|---|---|
| Row 3, pos 0 | `KC_LSFT` | Hold Shift for Shift+Click |
| Row 3, pos 1 | `KC_LCTL` | Hold Ctrl for Ctrl+Click |
| Row 3, pos 2 | `KC_LALT` | Hold Alt for Alt+Click |
| Row 3, pos 3 | `KC_LGUI` | Hold GUI for GUI+Click |

These are simpler than the pre-combined Shift+Click keys suggested above, and more flexible.

### Medium Priority: Window/Tab Management

| Position | Key | Why |
|---|---|---|
| Row 1, pos 1 | `C(KC_W)` | Close tab |
| Row 1, pos 2 | `C(KC_T)` | New tab |
| Row 1, pos 3 | `C(KC_TAB)` | Next tab |
| Row 1, pos 4 | `C(S(KC_TAB))` | Previous tab |
| Row 1, pos 5 | `A(KC_F4)` | Close window |

### Lower Priority: Drag Support

| Position | Key | Why |
|---|---|---|
| Row 0, pos 0 | `KC_MS_BTN1` (hold) | Left click hold for drag -- useful if physical click is awkward |

## Thumb Suggestions

| Position | Key | Why |
|---|---|---|
| Left thumb | `KC_MS_BTN1` | Left click on thumb -- can move and click with right hand only |
| Right thumb | `KC_MS_BTN2` | Right click on thumb |

## Mouse Keys Configuration Note

QMK now supports multiple mouse acceleration modes. Consider adding to `config.h`:

```c
// Kinetic mode -- quadratic acceleration curve
#define MK_KINETIC_SPEED
#define MOUSEKEY_DELAY 5
#define MOUSEKEY_INTERVAL 10
#define MOUSEKEY_MOVE_DELTA 16
#define MOUSEKEY_MAX_SPEED 32
#define MOUSEKEY_TIME_TO_MAX 35
```

This gives precise movement at first (for small targets), then fast jumps for crossing the screen.

## Summary

| Priority | Suggestion | Positions |
|---|---|---|
| **High** | BTN4/BTN5 (Back/Forward) | Right row 1, flanking BTN1/BTN2 |
| **High** | Horizontal scroll (WH_LEFT/WH_RIGHT) | Right row 3 |
| **High** | Undo/Copy/Paste on left home row | Left row 2 |
| Medium | Mouse acceleration keys (ACCEL0/1/2) | Right row 2 corners |
| Medium | Modifier keys on left (Shift/Ctrl/Alt) for click combos | Left row 3 |
| Medium | Tab management on left (Ctrl+W/T/Tab) | Left row 1 |
| Low | Kinetic mouse speed config in config.h | Configuration change |
| Low | Duplicate BTN1/BTN2 on thumbs | Thumb cluster |

The biggest gaps are **Back/Forward buttons** (BTN4/BTN5), **horizontal scroll**, and having **Undo/Copy/Paste accessible** while mousing with the right hand.
