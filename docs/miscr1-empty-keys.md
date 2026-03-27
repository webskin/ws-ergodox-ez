# MISCR1 / MISCR1AZ - Empty Key Suggestions

MISCR1 (Bepo) and MISCR1AZ (AZERTY) are the right-side navigation layers, accessed by holding `LT(MISCR1, BP_E)`. The right half has a well-designed navigation cluster (arrows, Home/End, PgUp/PgDn, word-jump, volume). The **entire left half is empty** except for Copy/Cut and Paste tap dances on the bottom row.

## Current MISCR1 Layout Map

Empty positions marked with `[___]`:

```
Row 0 (number row):
LEFT:  [___]  [___]  [___]  [___]  [___]  [___]  [___]
RIGHT: Insert  C(Del)  C(Home)  PgUp  C(End)  [___]  [___]

Row 1 (top):
LEFT:  [___]  [___]  [___]  [___]  [___]  [___]  [___]
RIGHT: VolUp  Delete  Home  Up  End  PrtSc  [___]

Row 2 (home):
LEFT:  [___]  [___]  [___]  [___]  [___]  [___]
RIGHT: Bksp  Left  Down  Right  Alt(PrtSc)  [___]

Row 3 (bottom):
LEFT:  [___]  [___]  [___]  [___]  [___]  TD(Paste/SIns)  [___]
RIGHT: VolDown  C(Bksp)  C(Left)  PgDn  C(Right)  [___]  [___]

Row 4 (thumb row):
LEFT:  [___]  [___]  [___]  [___]  TD(Copy/Cut)
RIGHT: [___]  [___]  [___]  [___]  [___]

Thumb cluster:
LEFT:  [___]  [___]  |  [___]  |  [___]  [___]  [___]
RIGHT: [___]  Mute  |  [___]  |  [___]  [___]  [___]
```

**Right half mapped:** 19 keys (navigation, editing, volume)
**Left half mapped:** 2 keys (Copy/Cut, Paste/ShiftInsert)
**Empty:** ~55 positions

## Left Half Suggestions

The left half is empty because this layer is activated by holding E (left hand stays on base layer with digraph protection). Same principle as MISCL1's empty right half. Suggestions below are for if you lock the layer or want quick-access keys near Copy/Cut/Paste.

### High Priority: Undo/Redo Near Copy/Cut/Paste

The editing cluster (Copy/Cut/Paste) is incomplete -- **Undo and Redo are missing** from this layer (they're on MISCR2 instead). Having them here too would be convenient.

| Position | MISCR1 (Bepo) | MISCR1AZ (AZERTY) | Why |
|---|---|---|---|
| Row 3, pos 4 (next to Paste) | `C(BP_Z)` | `C(FR_Z)` | Undo -- completes the editing cluster |
| Row 3, pos 3 | `C(S(BP_Z))` | `C(S(FR_Z))` | Redo |
| Row 3, pos 2 | `C(BP_A)` | `C(FR_A)` | Select All |

### Medium Priority: Find/Replace

| Position | Key | Why |
|---|---|---|
| Row 1, pos 4 | `C(BP_F)` or `C(FR_F)` | Find |
| Row 1, pos 5 | `C(BP_H)` or `C(FR_H)` | Replace |
| Row 1, pos 3 | `C(BP_G)` or `C(FR_G)` | Go to line |

### Medium Priority: Tab Navigation

| Position | Key | Why |
|---|---|---|
| Row 0, pos 1 | `C(KC_TAB)` | Next tab |
| Row 0, pos 2 | `C(S(KC_TAB))` | Previous tab |
| Row 0, pos 3 | `C(KC_W)` | Close tab |
| Row 0, pos 4 | `C(KC_T)` | New tab |

Works in browsers, IDEs, and terminals.

### Lower Priority: Window Management

| Position | Key | Why |
|---|---|---|
| Row 2, pos 0 | `G(KC_LEFT)` | Snap window left (Win) |
| Row 2, pos 1 | `G(KC_RIGHT)` | Snap window right (Win) |
| Row 2, pos 2 | `G(KC_UP)` | Maximize window (Win) |
| Row 2, pos 3 | `G(KC_DOWN)` | Minimize window (Win) |

## Right Half Suggestions

The right half is well-populated but has a few gaps.

### Row 0 Right Corner

| Position | Suggestion | Why |
|---|---|---|
| Row 0, pos 5 `[___]` | `C(KC_PGUP)` | Previous tab (alternative) |
| Row 0, pos 6 `[___]` | `C(KC_PGDN)` | Next tab (alternative) |

### Row 1 & Row 3 Right Corners

| Position | Suggestion | Why |
|---|---|---|
| Row 1, corner `[___]` | `KC_SCRL` | Scroll Lock |
| Row 3, pos 5 `[___]` | `C(KC_DELETE)` | Delete word forward |
| Row 3, corner `[___]` | `KC_PAUSE` | Pause/Break |

### Row 2 Right Corner

| Position | Suggestion | Why |
|---|---|---|
| Row 2, corner `[___]` | `KC_NUM` | Num Lock toggle |

### Row 4 & Thumbs

| Position | Suggestion | Why |
|---|---|---|
| Row 4 right `[___]` x4 | Keep transparent | Thumb row stays on base layer |

## Summary

| Priority | Suggestion | Positions |
|---|---|---|
| **High** | Undo `C(Z)` / Redo `C(S(Z))` / Select All `C(A)` near Copy/Paste | Left row 3 |
| **High** | Find `C(F)` / Replace `C(H)` | Left row 1 |
| Medium | Tab navigation (Ctrl+Tab, Ctrl+W, Ctrl+T) | Left row 0 |
| Medium | Window snapping (Win+arrows) | Left home row |
| Low | Missing right corner keys (Ctrl+PgUp/PgDn for tabs) | Right row 0 corners |

The biggest gap is **Undo/Redo right next to Copy/Cut/Paste** -- they belong together as a complete editing cluster.
