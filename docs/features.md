# Features

## Custom Keycodes (4)

| Keycode | Output | Use |
|---|---|---|
| `THIN_ARROW` | `->` | Lambda / dereference |
| `FAT_ARROW` | `=>` | Hash rocket / fat arrow |
| `TILD_ARROW` | `~>` | Pessimistic version constraint |
| `PIPE_ARROW` | `|>` | Pipe operator (Elixir, F#, etc.) |

All arrows preserve active modifier state (clear before send, restore after).

## Tap Dance (12 actions)

### Bepo

| Action | Tap | Double tap |
|---|---|---|
| Copy/Cut | Copy | Cut |
| Paste/ShiftInsert | Paste | Shift+Insert |
| `< / <<` | `<` | `<<` |
| `> / >>` | `>` | `>>` |
| V/W | V | W |
| Q/Z | Q | Z |
| E grave/Esc | e grave | Escape |

### AZERTY

Matching actions with AZERTY keycodes: Copy/Cut, Paste/ShiftInsert, V/W, Q/Z, E grave/Esc.

## Smart Digraph Protection

When holding a layer key (e.g., `LT(MISCL1, BP_T)`) and pressing a home-row key, the firmware sends the digraph combination instead of the layer function.

For example, holding T to access MISCL1 then pressing C sends `tc` rather than activating the layer action on C. This prevents unintended characters when briefly accessing modifier layers.

Works for both Bepo and AZERTY base layers with their respective layer variants.

## Per-Key Tapping Term

Custom 200ms tapping term with per-key overrides enabled. Mod-tap keys on the home row (Ctrl, Shift, Alt) use the same 200ms term for consistent behavior.

```c
uint16_t get_tapping_term(uint16_t keycode, keyrecord_t *record) {
  switch (keycode) {
    case CTL_T(BP_AGRV):
    case SFT_T(BP_P):
    // ...
      return 200;
    default:
      return TAPPING_TERM;
  }
}
```

## Platform-Aware Shortcuts

Separate definitions for Mac (GUI-based) and PC (Ctrl-based) operations:

```c
#define KC_MAC_UNDO LGUI(KC_Z)
#define KC_PC_UNDO  C(KC_Z)
#define KC_BP_CUT   C(BP_X)
#define KC_FR_CUT   C(FR_X)
```
